# TradeWise

**Personalized Investment Portfolio Management Platform**

**TradeWise** is a personalized investment portfolio management platform built with **Python (Django)** and **JavaScript (React)**, offering real-time stock tracking, historical data visualization, news insights, and AI-powered financial consultation and trend forecasting through API integration, simplifying complex financial decisions for investors.

![](/static/main.png)
![](/static/quote.png)
[Click Here to Watch Video Demo](https://youtu.be/Gcb93llG8d0)


---
## Distinctiveness and Complexity

TradeWise is a comprehensive stock portfolio management platform that provides users with real-time stock data, financial insights, and advanced investment tools. It is a highly distinct and complex project that builds on CS50W concepts while introducing innovative features. Here's why TradeWise stands out and meets the complexity requirements:

### Distinctiveness

1. **Comprehensive Financial Tool**:
   - TradeWise integrates functionalities like real-time stock quotes, transaction tracking, and historical data visualization, making it a one-stop solution for investment management.
   - Unlike previous projects in CS50W, which focused on social or e-commerce workflows, TradeWise is uniquely designed for the financial domain.

2. **Dynamic Visualization and Insights**:
   - Users can visualize stock trends using multiple chart types (e.g., candlestick, Heikin Ashi) powered by ApexCharts. This level of interactivity and insight goes far beyond static data representation.

3. **Automated News Integration**:
   - News scraping from NewsAPI ensures that users stay informed about the latest financial developments. This real-time integration is distinct from static content seen in other projects.

4. **AI and Machine Learning Capabilities**:
   - TradeWise leverages AI for **Personalized Investment Consulting** via its chatbot, which provides tailored advice to users based on their account data.
   - The project includes plans for deep learning-based stock predictions using LSTM models, demonstrating its ambition to incorporate cutting-edge technologies.

5. **User-Centric Features**:
   - Users can manage their accounts effectively with features like transaction tracking, cash management, and profile updates, emphasizing convenience and usability.

6. **Full-Stack Development**:
   - The integration of a React-powered front-end and Django back-end showcases the potential of full-stack development. It ensures seamless communication between the client and server for dynamic data updates.

### Complexity

1. **Advanced API Integration**:
   - TradeWise integrates multiple APIs, including Twelve Data, Financial Modeling Prep, and NewsAPI, for real-time stock data, financial summaries, and news. Handling rate limits, errors, and data formatting adds significant complexity.

2. **Stock Visualization**:
   - Implementing multiple stock chart types (e.g., candlestick, line, Heikin Ashi) required understanding complex data structures and visualization libraries like ApexCharts.

3. **AI-Powered Chatbot**:
   - The chatbot, powered by the Llama3 API, offers personalized investment advice based on user account data. This feature enhances the platform’s interactivity and complexity.

4. **Transactional Workflows**:
   - The project includes buy/sell validation to ensure accurate transactions based on live stock data and user balances. This feature integrates real-time checks and secure workflows.

5. **Responsive and Interactive Design**:
   - The use of Bootstrap for responsiveness ensures that TradeWise is accessible across devices, meeting the mobile-responsiveness requirement.
   - Features like "load more" buttons, dynamic table updates, and form validation improve usability and enhance the user experience.

6. **Scalable Deployment**:
   - TradeWise is containerized using Docker and Docker Compose, making it easy to deploy and scale. This ensures the project can handle real-world use cases effectively.

### Comparison to CS50W Projects

TradeWise avoids overlap with previous CS50W projects:
- **Not an E-Commerce Platform (Project 2)**:
   - TradeWise focuses on stock portfolio management, with features like transaction validation, AI consultation, and stock visualization, unrelated to "add to cart" or "checkout" workflows.
- **Not a Social Network (Project 4)**:
   - The application lacks social features like posts or likes. Instead, it emphasizes data-driven financial tools and personalized insights.

### Conclusion

TradeWise demonstrates both distinctiveness and complexity by addressing real-world financial challenges with advanced technologies. Its integration of APIs, dynamic visualization, and AI consulting makes it a standout project that showcases the true potential of full-stack development. By combining foundational CS50W concepts with innovative features, TradeWise exceeds the course’s expectations for final projects.

---
## How to Run

### Installation and Environment Setup
1. **(Optional)** Install **Docker Desktop** on your system.
2. **Clone the repository:**
   ```bash
   git clone https://github.com/hiepnguyendudc2005/TradeWise.git
   cd TradeWise
    ```
3. **Configure environment variables:**
- Add the following variables to a .env file:
    - If using Docker Compose: place the .env file in the root directory.
    - Otherwise: place the .env file in the server folder.
    ```bash
    TWELVE_DATA_API_URL=https://api.twelvedata.com
    TWELVE_DATA_API_KEYS=key1,key2,key3

    FMP_API_URL=https://financialmodelingprep.com/api/v3/
    FMP_API_KEY=key1,key2,key3

    NEWS_API_URL=https://newsapi.org/v2/
    NEWS_API_KEY=key1,key2,key3

    LLAMA_API_URL=https://openrouter.ai/api/v1/
    LLAMA_API_KEY=key
    ```
- Obtain API keys from:
    - [Twelve Data API](https://twelvedata.com/)
    - [Financial Modeling Prep API](https://site.financialmodelingprep.com/)
    - [NewsAPI](https://newsapi.org/)
    - [OpenRouter API, Llama3](https://openrouter.ai/models/meta-llama/llama-3.1-8b-instruct:free/api)
- **Note**: Using multiple keys in the first three variables is required help avoid exceeding free usage limits.

### Running the Application
#### With Docker Compose
- **Start the application:**
    ```bash
    docker compose up
    ```
- **Rebuild and start with local changes:**
    - Modify docker-compose.yml as needed (e.g., uncomment context and comment out pre-built image lines).
    - Build and start:
        ```bash
        docker compose up --build
        ```
- **Stop the application:**
    - Press Ctrl + C to terminate, then run:
    ```bash
    docker compose down
    ```

#### Using Docker (Build Local Images and Containers)
1. **Build and run the server:**
    ```bash
    cd server
    docker build -t tradewise-server .
    docker run -p 8000:8000 --env-file .env --name test-server tradewise-server
    ```
2. **Build and run the client:**
    ```bash
    cd client
    docker build -t tradewise-client .
    docker run -p 80:80 -e SERVER_URL=http://host.docker.internal:8000/ --name test-client tradewise-client
    ```

### Development Mode (Without Docker)
1. **Set up a Python virtual environment:**
    ```bash
    python3 -m venv myenv
    source myenv/bin/activate  # On Linux/macOS
    myenv\Scripts\activate     # On Windows
    ```
2. **Install server dependencies:**
    ```bash
    cd server
    pip install -r requirements.txt
    python manage.py makemigrations
    python manage.py migrate
    ```
3. **Run the Django server:**
    ```bash
    python manage.py test
    python manage.py runserver
    ```
4. **Install client dependencies:**
    ```bash
    cd client
    npm install
    ```
5. **Start the React client:**
    ```bash
    npm run dev
    ```


---
## File Structures

```md
├── /client
│   ├── /public: Static assests like favicons
│   ├── /src: Source files for React application
│   │   ├── /components: Reusable UI components
│   │   │   ├── /Graphs: Components for rendering stock graphs for specific styles
│   │   │   │   ├── Area.jsx
│   │   │   │   ├── Candlestick.jsx
│   │   │   │   ├── HeinkinAshi.jsx
│   │   │   │   └── Line.jsx
│   │   │   ├── About.jsx: Component for Company profile
│   │   │   ├── AntiProtectedRoute.jsx: Component for routes inaccessible to authenticated users
│   │   │   ├── Chatbot.jsx: Chatbot interface
│   │   │   ├── Demo.jsx: Demo video interface
│   │   │   ├── Finance.jsx: Component for Company financial summary
│   │   │   ├── Navbar.jsx: Navigation bar
│   │   │   ├── NewsData.jsx: Component for feteched news articles
│   │   │   ├── ProtectedRoute.jsx: Component for routes accessible to authenticated users
│   │   │   └── StockGraph.jsx: Component to handle stock graph display
│   │   ├── /css: Stylesheets for components
│   │   │   ├── Chatbot.css
│   │   │   ├── main.css
│   │   │   ├── Navbar.css
│   │   │   ├── NewsData.css
│   │   │   └── Profile.css
│   │   ├── /pages: Pages corresponding to app routes
│   │   │   ├── AddCash.jsx
│   │   │   ├── Buy.jsx
│   │   │   ├── ChangePassword.jsx
│   │   │   ├── History.jsx
│   │   │   ├── Index.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── NotFound.jsx
│   │   │   ├── Profile.jsx
│   │   │   ├── Quote.jsx
│   │   │   ├── Sell.jsx
│   │   │   └── Signup.jsx
│   │   ├── /services: API-related logic and service calls
│   │   │   ├── AuthAPI.jsx
│   │   │   ├── ChatbotAPI.jsx
│   │   │   ├── Profiles.jsx
│   │   │   ├── TransactionsAPI.jsx
│   │   │   └── UsersAPI.jsx
│   │   ├── /utilities: Helper functions for reusability across components
│   │   │   ├── APICall.jsx: Handles API calls and error handling
│   │   │   ├── CalculateClose.jsx: Calculates the closing price for stock data
│   │   │   ├── CalculateHeikinAshi.jsx: Implements the Heikin-Ashi algorithm for candlestick charts
│   │   │   ├── CalculateVolume.jsx: Processes and calculates stock trading volumes
│   │   │   ├── Formatter.jsx: Formats chart categories
│   │   │   └── NumberFormat.jsx: Provides number formatting utilities for UI consistency
│   │   ├── App.css: Body CSS styles
│   │   ├── App.jsx: Main application entry point
│   │   ├── index.css (default): Global CSS styles
│   │   └── main.jsx (default): App's root render logic
│   ├── .dockerignore: Lists files and folders to exclude from Docker builds
│   ├── .gitignore: Lists files and folders to exclude from version control
│   ├── Dockerfile: Instructions to containerize the client application
│   ├── eslint.config.js (default): Configuration for linting JavaScript/React code
│   ├── index.html: Entry point for the React app
│   ├── nginx.conf: Configuration file for serving the app using NGINX
│   ├── package-lock.json: Dependencies and scripts for the React application (details)
│   ├── package.json: Dependencies and scripts for the React application
│   └── vite.config.js: Configuration file for Vite build tool
├── /server
│   ├── /server: Django project directory
│   │   ├── __init__.py (default): Marks the folder as a Python package
│   │   ├── asgi.py (default): ASGI configuration for async support
│   │   ├── settings.py: Django settings, including installed apps and middleware
│   │   ├── urls.py: Main URL routing configuration
│   │   └── wsgi.py (default): WSGI configuration for production servers
│   ├── /tradewise: Django app directory
│   │   ├── __init__.py (default): Marks the folder as a Python package
│   │   ├── admin.py: Admin interface configurations
│   │   ├── apps.py (default): Configuration for the tradewise app
│   │   ├── helpers.py: Utility functions for the server
│   │   ├── models.py: Database models for the app (MODELS)
│   │   ├── prompt.py: Text Prompt to improve conversation with Chatbot
│   │   ├── signals.py: Signal handling (e.g., post-save actions for models) 
│   │   ├── templates.py: Template view for reusuable Json Response formats (VIEWS)
│   │   ├── tests.py: Unit tests for the server-side code
│   │   ├── urls.py: URL routing for the app
│   │   └── views.py: View functions handling HTTP requests (CONTROLLERS)
│   ├── .dockerignore: Exclude unnecessary files from Docker builds
│   ├── .gitignore: Exclude unnecessary files from version control
│   ├── Dockerfile: Instructions to containerize the server application
│   ├── manage.py: Command-line utility for managing the Django project
│   └── requirements.txt: Lists Python dependencies for the server
├── /static: Screenshots of the app and main feature
├── .gitignore: Global file exclusions for version control
├── docker-compose.yml: Defines multi-container setup for the client and server
└── README.md: Documentation for the project
```


---
## License
    Copyright [2024] [Hiep Nguyen]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

---
## Contribution
Contributions are welcome! Please fork the repository and create a pull request with your changes.

---
## Contact
For any queries or suggestions, feel free to reach out via the project repository.
Let me know if you'd like further customization!