# E-Commerce Product Recommendation System

A simple machine learning project that recommends similar products based on product names, categories, and descriptions.

The system uses TF-IDF and cosine similarity to find products that are similar to a selected product. Product information is stored in SQLite, and FastAPI is used to provide a simple API for accessing recommendations.

## Features

- Product data stored in SQLite
- Data preprocessing using Pandas
- TF-IDF based text representation
- Cosine similarity for product recommendations
- FastAPI REST API
- Product recommendation endpoint
- Basic recommendation feedback storage

## Technologies Used

- Python
- Pandas
- Scikit-learn
- SQLite
- FastAPI
- Uvicorn


## How It Works

The recommendation pipeline is:

Product Dataset
        ↓
Data Cleaning
        ↓
Combine Product Information
        ↓
TF-IDF Vectorization
        ↓
Cosine Similarity
        ↓
Find Similar Products
        ↓
Return Recommendations

The product name, category, and description are combined into a single text field.

TF-IDF converts this text into numerical vectors. Cosine similarity is then used to calculate how similar two products are.

Products with the highest similarity scores are returned as recommendations.

## Dataset

The project works with an e-commerce dataset containing product information such as:

- Product ID
- Product name
- Category
- Description
- Price

A public e-commerce dataset can be used as the input data.

## Installation

Clone the repository:

    git clone <your-repository-url>
    cd ecommerce-recommender

Create a virtual environment:

    python -m venv .venv

Activate the virtual environment.

Windows:

    .venv\Scripts\activate

Linux / macOS:

    source .venv/bin/activate

Install dependencies:

    pip install -r requirements.txt

## Running the Project

First, populate the SQLite database using the product dataset.

Then start the FastAPI server:

    uvicorn api.main:app --reload

The API will be available at:

    http://127.0.0.1:8000

Interactive API documentation is available at:

    http://127.0.0.1:8000/docs

## API Endpoints

### Get Products

    GET /products

Returns the products stored in the database.

### Get Recommendations

    GET /recommend/{product_id}

Returns similar products for a selected product.

Example:

    GET /recommend/101

Example response:

    {
        "product_id": 101,
        "recommendations": [
            {
                "product_id": 245,
                "name": "Adidas Running Shoes",
                "similarity": 0.82
            },
            {
                "product_id": 318,
                "name": "Puma Running Shoes",
                "similarity": 0.76
            }
        ]
    }

### Submit Feedback

    POST /feedback

Stores basic feedback about recommendations.

## Example

If a user selects:

    Nike Running Shoes

The system compares it with other products and may return:

    1. Adidas Running Shoes
    2. Puma Running Shoes
    3. ASICS Running Shoes

Products from unrelated categories are expected to receive lower similarity scores.

## Future Improvements

- Add product ratings
- Add price-based filtering
- Implement collaborative filtering
- Add user-based recommendations
- Build a simple frontend
- Experiment with different recommendation algorithms
- Add recommendation evaluation metrics

## Learning Outcomes

This project helped me understand:

- Data preprocessing
- TF-IDF vectorization
- Cosine similarity
- Content-based recommendation systems
- SQLite databases
- REST APIs
- FastAPI
- Basic machine learning workflows

## License

This project is for educational purposes.
