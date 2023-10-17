# MLD

```MLD

user ( id INTEGER, firstname TEXT, lastname TEXT, email TEXT, password TEXT )
quiz ( id INTEGER, title TEXT, description TEXT, #user(id) )
level ( id INTEGER, nom TEXT )
question ( id INTEGER, description TEXT, anecdote TEXT, wiki TEXT, #quizz(id), #answer(id), #level(id) )
answer ( id INTEGER, description TEXT, #question(id) )
tag ( id INTEGER, nom TEXT)
quizz_has_tag ( #quizz(id), #tag(id) )

```
