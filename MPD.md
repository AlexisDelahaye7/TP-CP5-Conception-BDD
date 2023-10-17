# MPD

```postgresql
CREATE DOMAIN email AS TEXT CHECK (VALUE ~* '^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$');


CREATE TABLE "user" (
    "id" INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    "firstname" TEXT NOT NULL,
    "lastname" TEXT NOT NULL,
    "email" email NOT NULL,
    "password" TEXT NOT NULL,
    "created_at" TIMESTAMPTZ NOT NULL DEFAULT now(),
    "updated_at" TIMESTAMPTZ 
);

CREATE TABLE "quiz" (
    "id" INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    "title" TEXT NOT NULL,
    "description" TEXT,
    "user_id" INT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES "user" (id),
    "created_at" TIMESTAMPTZ NOT NULL DEFAULT now(),
    "updated_at" TIMESTAMPTZ 
);

CREATE TABLE "level" (
    "id" INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    "nom" TEXT NOT NULL,
    "created_at" TIMESTAMPTZ NOT NULL DEFAULT now(),
    "updated_at" TIMESTAMPTZ 
);

CREATE TABLE "answer" (
    "id" INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    "description" TEXT NOT NULL,
    "created_at" TIMESTAMPTZ NOT NULL DEFAULT now(),
    "updated_at" TIMESTAMPTZ 
);

CREATE TABLE "question" (
    "id" INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    "description" TEXT NOT NULL,
    "anecdote" TEXT,
    "wiki" TEXT,
    "quiz_id" INT NOT NULL,
    "answer_id" INT NOT NULL,
    "level_id" INT NOT NULL,
    FOREIGN KEY (quiz_id) REFERENCES quiz (id),
    FOREIGN KEY (answer_id) REFERENCES answer (id),
    FOREIGN KEY (level_id) REFERENCES level (id),
    "created_at" TIMESTAMPTZ NOT NULL DEFAULT now(),
    "updated_at" TIMESTAMPTZ 
);

CREATE TABLE "tag" (
    "id" INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    "nom" TEXT NOT NULL,
    "created_at" TIMESTAMPTZ NOT NULL DEFAULT now(),
    "updated_at" TIMESTAMPTZ 
);

CREATE TABLE "quiz_has_tag" (
    "quiz_id" INT,
    "tag_id" INT,
    FOREIGN KEY (quiz_id) REFERENCES quiz (id),
    FOREIGN KEY (tag_id) REFERENCES tag (id)
);
```
