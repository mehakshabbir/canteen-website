# 🍔 Campus Canteen — Food Ordering Web App

A modern, fast, and mobile-friendly campus food ordering web application built with **React**, **Vite**, **Tailwind CSS**, and **React Router DOM**. Designed specifically for university students to browse daily canteen menus, search and filter items, customize orders with special notes, save favourites, and generate simulated pickup tokens.

---

## 🚀 Quick Start Guide (Run in VS Code)

Follow these simple steps to run this project on your computer using **Visual Studio Code**:

### 1. Prerequisites
Ensure you have **Node.js** (version 18 or newer) installed on your system.
You can download it for free from [https://nodejs.org](https://nodejs.org).

### 2. Open the Project in VS Code
1. Open **Visual Studio Code**.
2. Click **File** > **Open Folder...** and select this project directory.
3. Open the integrated terminal in VS Code: `Ctrl + ~` (Windows/Linux) or `Cmd + ~` (macOS).

### 3. Install Dependencies
Run the following command in the terminal to install all required packages:
```bash
npm install
```

### 4. Start the Local Development Server
Launch the live server by running:
```bash
npm run dev
```

You will see an output like:
```
  VITE v...  ready in 200 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: use --host to expose
```
Hold `Ctrl` (or `Cmd` on Mac) and click the `http://localhost:3000/` link in your terminal to open the app in your browser!

### 5. Build for Production
To create an optimized production build:
```bash
npm run build
```

---

## 📁 Project Folder Structure

```
campus-canteen/
├── public/
│   ├── images/              # Local food images & photography
│   │   ├── zinger-burger.jpg
│   │   ├── chicken-biryani.jpg
│   │   ├── club-sandwich.jpg
│   │   └── hero-canteen.jpg
│   └── menu.json            # 16 complete dishes with PKR prices & details
├── src/
│   ├── components/
│   │   ├── Header.jsx       # Navigation bar with live cart & favourites badge
│   │   ├── SearchBar.jsx    # Instant search with suggestion tags & clear button
│   │   ├── CategoryFilter.jsx # Segmented category buttons with item counts
│   │   ├── ItemCard.jsx     # Food card with image fallback, PKR price, stepper
│   │   ├── MenuList.jsx     # Responsive grid, loading skeleton & error retry
│   │   ├── Cart.jsx         # Cart items, student checkout, and price calculations
│   │   └── Footer.jsx       # Campus hours, counter locations, and info
│   ├── pages/
│   │   ├── Menu.jsx         # Homepage with hero banner and menu browser
│   │   ├── ItemDetails.jsx  # Detailed food view (/item/:id) with notes & related items
│   │   ├── CartPage.jsx     # Full order page with digital token generator
│   │   └── NotFound.jsx     # 404 page for invalid routes
│   ├── context/
│   │   └── CartContext.jsx  # Global React Context for Cart, Favourites, & Discounts
│   ├── App.jsx              # Main routes, ScrollToTop, and global toast alerts
│   ├── main.jsx             # React DOM root entry point
│   └── index.css            # Tailwind CSS imports and custom typography
├── index.html               # Main HTML entry with Google Fonts
├── package.json             # Project dependencies and npm scripts
└── README.md                # Complete documentation and instructions
```

---

## 🌟 Key Features

1. **Today's Canteen Menu (`/`)**:
   - Fetched asynchronously from `/menu.json` using `fetch()` and `async/await`.
   - Beautiful Hero section highlighting today's fresh campus kitchen.
   - Clean loading skeleton states and friendly error handling with a **"Retry Loading"** button.

2. **Case-Insensitive Search & Quick Filters**:
   - Search by dish name, category, or ingredients.
   - Quick one-click search chips (e.g. *Zinger*, *Biryani*, *Pizza*, *Chai*, *Fries*).
   - Clear (`X`) button to reset search immediately.

3. **Category & Favourites Filtering**:
   - Filter by *All Items*, *Fast Food*, *Snacks*, *Desi Specials*, *Drinks*, and *Desserts*.
   - Filter by **Saved Favourites** to view your personal shortlist.
   - Dynamic counter showing how many items exist in each category.

4. **Interactive Food Cards (`ItemCard.jsx`)**:
   - High-resolution food photography with 4:3 aspect ratio.
   - **Zero-Broken-Image Policy**: If an image fails or is unavailable, an automatic styled SVG fallback is rendered.
   - Heart button to save/remove dishes from favourites (saved to `localStorage`).
   - Dynamic Cart Stepper: If an item is already in your cart, adjust the quantity directly on the card!

5. **Detailed Dish Page (`/item/:id`)**:
   - High-definition image, preparation time, rating, and spice level indicators.
   - Special instructions field for the counter chef (e.g., *"Extra spicy"*, *"No mayo"*).
   - Quantity selector with instant subtotal preview.
   - Related dishes recommendations from the same category.

6. **Cart & Token Generation (`/cart`)**:
   - Live badge counter in the header updating on every screen.
   - Itemized order list with individual subtotal calculations.
   - Student ID & Roll number input for counter collection.
   - Counter selection (*Counter 1: Fast Food*, *Counter 2: Desi*, *Counter 3: Drinks*).
   - **Student Promo Codes**:
     - `STUDENT10` (10% discount)
     - `CAMPUS15` (15% discount)
     - `FREESERVICE` (Rs. 20 handling fee waiver)
   - Order Confirmation Modal with a simulated **Digital Pickup Token** (e.g. `TOKEN #C-384`) and printable receipt.

---

## 🍲 How to Add New Dishes to `menu.json`

Open `public/menu.json` and add a new object to the array:

```json
{
  "id": 17,
  "name": "Crispy Fish & Chips",
  "category": "Fast Food",
  "price": 550,
  "description": "Golden battered fish fillet served with crinkle-cut fries and homemade tartar sauce.",
  "image": "https://images.unsplash.com/photo-1579208575657-c595a05383b7?auto=format&fit=crop&w=800&q=80",
  "available": true,
  "rating": 4.8,
  "prepTime": "12-14 mins",
  "isSpicy": false,
  "tag": "New"
}
```

---

## 🎨 Design & Theme Details

- **Palette**: Warm Cream (`#FAF8F5`), Deep Slate (`#1E293B`), Warm Orange (`#EA580C`), Rose (`#E11D48`), and Emerald (`#059669`).
- **Typography**: *Plus Jakarta Sans* for modern, legible user interface hierarchy.
- **Prices**: Realistic Pakistani Rupee (PKR) pricing using tabular numbers (`font-variant-numeric: tabular-nums`).
- **No Paid APIs Required**: Runs 100% locally with client-side JSON data.
