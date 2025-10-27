# Node.js Course - S21 Adding Pagination

Practice code for Section 21 - Adding Pagination, part of the course "NodeJS - The Complete Guide (MVC, REST APIs, GraphQL, Deno)" by Academind, Maximilian Schwarzmüller.

This project covers:
- Implementing server-side pagination without external packages
- Reading the page value from query parameter
- Using MongoDB `.skip()` and `.limit()` to fetch the current page slice
- Rendering pagination links in views

# Project type
- Independently implemented while following a Node.js course, writing all functionalities from scratch and extending the project with personal improvements.

## Tech Stack
- Node.js
- Express.js
- JavaScript (ES6+)
- MongoDB
- Mongoose
- express-session
- connect-mongodb-session
- multer
- pdfkit-table
- Nodemailer with SendGrid transport
- Docker
- dotenv
- chalk
- Nodemon
  
# How to Run

## 1) Clone the repo
```bash
git clone https://github.com/S21-Adding-Pagination
cd ./S21-Adding-Pagination
```

---

## 2) Environment variables

#### 2.1) Copy the example file
```bash
cp .env.example .env
```
> Note: Recommended and essential environment variable settings are described in `.env.example`

---

## 3) Run the app via Docker (already installed)

#### 1. Make sure your Docker app is running

#### 2. Install dependencies
   ```bash
   npm install
   ```

#### 3. Start MongoDB with Docker Compose
   ```bash
   npm run db:start
   ```
   - Creates database **`shop`**
> Runs `docker compose up -d`

#### 4. Run the app
```bash
node .\server.js
```

#### 5. Stop the container
   ```bash
   npm run db:down
   ```
> Runs `docker compose down -v`

#### 6. Reset database (remove data + re-run init scripts)
   ```bash
   npm run db:reset
   ```
> Runs `docker compose down -v && docker compose up -d`

---

## 4) Log in using example credentials

#### 1. Main user
```code
email: test@example.com
password: 123
```

#### 2. Second user
```code
email: foo@bar.com
password: 456
```

---

## Testing DB Connection
A helper script is included to quickly test DB connectivity

```bash
npm run db:test
```
> Runs `node scripts/test-db.js`

<br>Expected output:
```

===== DB connection OK =====

--- Product data: --- [
  {
    _id: new ObjectId('68c5a0d9f45e62ed9233c5d3'),
    title: 'Physical picture of a kitty',
    price: 0.99,
    description: 'kitty',
    imageUrl: 'images/kitty-image.jpg',
    userId: new ObjectId('68c59cebf2b7f6e17ff9ea08')
  },
  {
    _id: new ObjectId('68c32686af5c529e81421f78'),
    title: 'A book!',
    price: 12.99,
    description: 'Funny-colored',
    imageUrl: 'images/book-image.jpg',
    userId: new ObjectId('68c59cebf2b7f6e17ff9ea08')
  },
  {
    _id: new ObjectId('68c32686af5c529e814266e1'),
    title: 'Red apple',
    price: 2.99,
    description: 'Do not combine with a pen',
    imageUrl: 'images/apple-image.png',
    userId: new ObjectId('68c59cebf2b7f6e17ff9ea08')
  },
  {
    _id: new ObjectId('68c495a27829b9cab975da81'),
    title: 'Pen',
    price: 249.99,
    description: 'Pure prestige',
    imageUrl: 'images/pen-image.png',
    userId: new ObjectId('68c49525baa988da36319592')
  }
]

--- User data: --- [
  {
    cart: { items: [] },
    _id: new ObjectId('68c59cebf2b7f6e17ff9ea08'),
    email: 'test@example.com',
    password: '$2b$12$3K2ChFNft.k8lF4TShiRee6vOBnaSqC3gi81SNUDvMf.dhsf84zv.'
  },
  {
    cart: { items: [] },
    _id: new ObjectId('68c49525baa988da36319592'),
    email: 'foo@bar.com',
    password: '$2b$12$9FaAU/JXiYbJ6k3RuPM9pudnJkOPoQaF9BlF0exENihInyhR/6stK'
  }
]

```

---

## NPM Scripts

- **`npm start` / `node .\server.js`** → start the Node app
- **`npm run db:test`** → run DB connectivity test (`scripts/test-db.js`)
- **`npm run db:up`** → start MongoDB container
- **`npm run db:down`** → stop MongoDB container
- **`npm run db:reset`** → reset database (drop volume + re-init)

---

## Notes
- `.env` is ignored by Git; only `.env.example` is committed
- If port 3000 is already in use, change the `SERVER_PORT` value in `.env`
- Recommended and essential environment variable settings are described in `.env.example`
- Email functionality will not work out of the box. To enable email sending, you need to create your own SendGrid account and provide an API key + Sender Email in your `.env`

---

## IMPORTANT - About `csurf`

<details>
  <summary>My note about csurf deprecation</summary>
  
<br>
<b>I know that <code>csurf</code> has been marked as deprecated.</b>
<br><br>
This Node.js course was created a few years ago using <code>csurf</code>, before the development team deprecated this package. Maximillian explained the general principle of CSRF attacks and used <code>csurf</code> for demonstration purposes.
<br><br>
Since the attacks are only simulated locally in our code and this is a course repository after all <i>(though I put my heart into every single one of them)</i>, I will continue using <code>csurf</code> until I decide otherwise.

</details>
