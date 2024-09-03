# BrainerHub Assignment

This project consists of a Flask application to upload an Excel file and load employee and company data into an SQLite database.

## Project Structure

- `app.py`: The main Flask application file.

## Requirements

- Python 3.x
- Flask
- Flask-SQLAlchemy
- openpyxl

## Setup

1. **Clone the repository:**

    ```bash
    git clone <repository-url>
    cd <repository-folder>
    ```

2. **Create a virtual environment:**

    ```bash
    python -m venv venv
    source venv/bin/activate   # On Windows use `venv\Scripts\activate`
    ```

3. **Install the dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

## Running the Application

1. **Initialize the database:**

    This will create the `employees.db` SQLite database file.

    ```bash
    python app.py
    ```

2. **Run the Flask application:**

    ```bash
    python app.py
    ```

    The application will be available at `http://127.0.0.1:5000`.

## API Endpoints

### Load Data

- **URL:** `/load_data`
- **Method:** `POST`
- **Description:** Loads data from an Excel file to the database.

#### Request

- **Headers:**

    ```json
    {
        "Content-Type": "multipart/form-data"
    }
    ```

- **Body:**

    A file field containing the Excel file.

#### Response

- **Success Response:**

    ```json
    {
        "message": "Data loaded successfully"
    }
    ```

- **Error Responses:**

    ```json
    {
        "error": "No file part"
    }
    ```

    ```json
    {
        "error": "No selected file"
    }
    ```

    ```json
    {
        "error": "Error adding company: <error-message>"
    }
    ```

    ```json
    {
        "error": "Error adding employees: <error-message>"
    }
    ```

    ```json
    {
        "error": "An error occurred: <error-message>"
    }
    ```

## Excel File Format

The Excel file should have the following columns:

- `employee_id`
- `first_name`
- `last_name`
- `phone_number`
- `company_name`
- `salary`
- `manager_id`
- `department_id`

Ensure the data starts from the second row; the first row should contain column headers.

## Testing

You can use tools like Postman or `curl` to test the `/load_data` endpoint by uploading an Excel file.

## License

This project is licensed under the MIT License.
