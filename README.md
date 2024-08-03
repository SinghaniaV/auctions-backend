# Auction Site

## Project Overview

This project is a web-based auction site implemented using Django. It allows users to create and bid on auction listings, comment on them, and manage their own watchlists. The project fulfills the following requirements:

## Models

The application contains the following models in addition to the default `User` model:

1. **Category**
   - `name`: The name of the category.

2. **AuctionListing**
   - `title`: The title of the listing.
   - `description`: A text-based description of the listing.
   - `starting_bid`: The starting bid for the auction.
   - `image_url`: An optional URL for an image of the listing.
   - `category`: The category of the listing (foreign key to `Category`).
   - `created_at`: The date and time when the listing was created.
   - `active`: A boolean indicating if the listing is still active.
   - `owner`: The user who created the listing (foreign key to `User`).

3. **Bid**
   - `amount`: The amount of the bid.
   - `listing`: The auction listing the bid is for (foreign key to `AuctionListing`).
   - `user`: The user who placed the bid (foreign key to `User`).
   - `created_at`: The date and time when the bid was placed.

4. **Comment**
   - `content`: The content of the comment.
   - `listing`: The auction listing the comment is for (foreign key to `AuctionListing`).
   - `user`: The user who posted the comment (foreign key to `User`).
   - `created_at`: The date and time when the comment was posted.

## Functionality

### Create Listing

Users can create new auction listings by providing a title, description, starting bid, and optionally an image URL and category.

### Active Listings Page

The default route displays all currently active auction listings with their title, description, current price, and photo (if provided).

### Listing Page

Clicking on a listing redirects users to a page with all details about the listing, including the current price. Signed-in users can:
- Add the item to their watchlist.
- Remove the item from their watchlist.
- Bid on the item (if the bid is valid).
- Close the auction (if they created the listing).

Users who have won an auction will see a message indicating they have won when viewing the closed listing.

### Watchlist

Signed-in users can view all listings in their watchlist and navigate to individual listing pages from there.

### Categories

Users can view a list of all categories and see active listings in each category.

### Comments

Signed-in users can comment on listings. All comments are displayed on the listing page.

## How to Run

1. **Clone the repository**:
    ```bash
    git clone https://github.com/SinghaniaV/auctions-backend
    cd auctions-backend
    ```

2. **Create a virtual environment and activate it**:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3. **Install dependencies**:
    ```bash
    pip install django
    ```

4. **Apply migrations**:
    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```

5. **Run the development server**:
    ```bash
    python manage.py runserver
    ```
