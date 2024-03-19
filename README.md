
## fullstack with postgresql apps and Data Modeling

# Pet Adoption Agency Database Design

## Tables:

1. **Animals**
   - animal_id: SERIAL, PRIMARY KEY
   - name: VARCHAR
   - species_id: INTEGER (FOREIGN KEY referencing Species.species_id)
   - age: INTEGER
   - gender: VARCHAR
   - color: VARCHAR
   - adopted: BOOLEAN

2. **Species**
   - species_id: SERIAL, PRIMARY KEY
   - name: VARCHAR
   - description: TEXT

3. **Adopters**
   - adopter_id: SERIAL, PRIMARY KEY
   - name: VARCHAR
   - email: VARCHAR
   - phone: VARCHAR
   - address: VARCHAR

4. **Adoptions**
   - adoption_id: SERIAL, PRIMARY KEY
   - animal_id: INTEGER (FOREIGN KEY referencing Animals.animal_id)
   - adopter_id: INTEGER (FOREIGN KEY referencing Adopters.adopter_id)
   - adoption_date: DATE
   - fee: DECIMAL

## Relationships:
- One-to-Many relationship between Species and Animals (One species can have many animals)
- Many-to-Many relationship between Animals and Adopters (An animal can be adopted by multiple adopters and an adopter can adopt multiple animals)
- One-to-Many relationship between Adopters and Adoptions (One adopter can have multiple adoptions)

# Instructions for Sequelize Integration

## Step 1: Dotenv
1. Install dotenv using `npm install dotenv`.
2. Create a new local database in pgAdmin named `unit5`.
3. Create a `.env` file in the root of the `travel-journal` directory with the following variables:
   - `SERVER_PORT=4004`
   - `CONNECTION_STRING=postgres:///unit5`

## Step 2: Sequelize
1. Install Sequelize and its dependencies using `npm install sequelize pg pg-hstore`.
2. Initialize a new Sequelize instance in `controller.js` using your connection string.

## Step 3: Seeding the Database
1. Replace `*****YOUR CODE HERE*****` in the seed function in `controller.js` with a SQL query to create a `cities` table with the specified columns.
2. Start your backend with `nodemon`.
3. Use Postman to make a POST request to `http://localhost:4004/seed` to seed the database.

## Step 4: Getting Countries
1. Write a new function `getCountries` in `controller.js` to query all columns from the `countries` table using `sequelize.query`.
2. Comment in `app.get('/countries', getCountries)` in `index.js`.
3. Open `index.html` in your browser to view the list of countries.

## Step 5: Adding Entries
1. Write a new function `createCity` in `controller.js` to insert data into the `cities` table using `sequelize.query`.
2. Comment in `app.post('/cities', createCity)` in `index.js`.

## Step 6: Getting Cities
1. Write a new function `getCities` in `controller.js` to query columns from both `cities` and `countries` tables using `sequelize.query`.
2. Comment in `app.get('/cities', getCities)` in `index.js`.

## Step 7: Deleting Cities
1. Write a new function `deleteCity` in `controller.js` to delete a city from the `cities` table using `sequelize.query`.
2. Comment in `app.delete('/cities/:id', deleteCity)` in `index.js`.

## Extra Credit: Travel Journal
1. Update the `getCities` function to retrieve cities ordered by rating (highest to lowest).
2. Update the seed function to initially insert at least 3 entries into the `cities` table.
