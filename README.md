Flask Code Challenge - Superheroes
Welcome to the Phase 4 Flask Code Challenge.
This project involves expanding a Flask application for tracking heroes and their superpowers. The goal is to fulfill specific deliverables outlined below.

Table of Contents.
-Setup.
-Models.
-Validations.
-Routes.

Setup.
To get started, follow these steps to set up the project:
Dependencies
Download the dependencies for the frontend and backend:

pipenv install.
npm install --prefix client.
Run Flask API.
Launch the Flask API on localhost:5555:

python app.py
Run React App
Run the React app on localhost:4000:

npm start --prefix client.
Feel free to use the provided React frontend for testing the API's behavior.

Models.
Create the following relationships in the database:

A Hero has many Powers through HeroPower
A Power has many Heros through HeroPower
A HeroPower belongs to a Hero and belongs to a Power
Start by creating models and migrations for the specified database tables. Refer to the domain diagram provided.

Run migrations and seed data:

flask db upgrade head.
python app/seed.py
If the provided seed file doesn't work, generate your own seed data for testing.

Validations.
Add validations to the HeroPower model:

strength must be one of the following values: 'Strong', 'Weak', 'Average'
Add validations to the Power model:

description must be present and at least 20 characters long
Routes
Set up the following routes, ensuring JSON data is returned in the specified format:

GET /heroes
Return JSON data:

json
Copy code
[
  { "id": 1, "name": "Kamala Khan", "super_name": "Ms. Marvel" },
  { "id": 2, "name": "Doreen Green", "super_name": "Squirrel Girl" },
  { "id": 3, "name": "Gwen Stacy", "super_name": "Spider-Gwen" }
]
GET /heroes/:id
Return JSON data if the Hero exists:

json
Copy code
{
  "id": 1,
  "name": "Kamala Khan",
  "super_name": "Ms. Marvel",
  "powers": [
    { "id": 1, "name": "super strength", "description": "gives the wielder super-human strengths" },
    { "id": 2, "name": "flight", "description": "gives the wielder the ability to fly through the skies at supersonic speed" }
  ]
}
Return an error if the Hero does not exist.

GET /powers
Return JSON data:

json
Copy code
[
  { "id": 1, "name": "super strength", "description": "gives the wielder super-human strengths" },
  { "id": 2, "name": "flight", "description": "gives the wielder the ability to fly through the skies at supersonic speed" }
]
GET /powers/:id
Return JSON data if the Power exists:

json
Copy code
{ "id": 1, "name": "super strength", "description": "gives the wielder super-human strengths" }
Return an error if the Power does not exist.

PATCH /powers/:id
Update an existing Power. Accept an object with the following properties:

json
Copy code
{ "description": "Updated description" }
Return updated data if successful, or an error if the Power does not exist or doesn't pass validations.

POST /hero_powers
Create a new HeroPower associated with an existing Power and Hero. Accept an object with the following properties:

json
Copy code
{ "strength": "Average", "power_id": 1, "hero_id": 3 }
Return related Hero data if successful, or validation errors if not.

Feel free to check your progress by running tests or interacting with the API via the provided methods. Good luck!

Author.

This Project was contributed by: Christine Muriungi.

License.

This project is licensed under the MIT License - see the LICENSE file for details.
