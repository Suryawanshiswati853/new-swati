 my  projects
lib/
│
├── main.dart
│   └── Application entry point. Initializes required services and starts the Flutter application.
│
├── app/
│   │
│   ├── export.dart
│   │   └── Central export file for commonly used application files and configurations.
│   │
│   ├── bindings/
│   │   └── initial_binding.dart
│   │       └── Registers global GetX controllers and dependencies when the application starts.
│   │
│   ├── routes/
│   │   ├── app_pages.dart
│   │   │   └── Defines GetX routes and maps routes to their respective screens and bindings.
│   │   │
│   │   └── app_routes.dart
│   │       └── Contains centralized route name constants used throughout the application.
│   │
│   └── theme/
│       ├── app_colors.dart
│       │   └── Contains centralized application color definitions.
│       │
│       ├── app_theme.dart
│       │   └── Defines the global ThemeData and application-wide UI styling.
│       │
│       └── app_text_styles.dart
│           └── Contains reusable text styles for consistent typography.
│
├── core/
│   │
│   ├── constants/
│   │   ├── app_constants.dart
│   │   │   └── Stores application-wide constants such as login credentials and storage keys.
│   │   │
│   │   └── api_constants.dart
│   │       └── Contains API base URLs and endpoint definitions.
│   │
│   └── services/
│       ├── api_service.dart
│       │   └── Handles HTTP requests and communication with the Fake Store API.
│       │
│       └── storage_service.dart
│           └── Manages local data persistence using SharedPreferences for login and cart data.
│
├── data/
│   │
│   └── models/
│       ├── product_model.dart
│       │   └── Represents product data received from the Fake Store API.
│       │
│       └── cart_item_model.dart
│           └── Represents products and quantities stored in the local shopping cart.
│
├── controllers/
│   │
│   ├── splash_controller.dart
│   │   └── Checks the login status and controls navigation from the Splash Screen.
│   │
│   ├── login_controller.dart
│   │   └── Handles login validation, authentication logic, loading state, and login persistence.
│   │
│   ├── product_controller.dart
│   │   └── Manages product fetching, loading, refreshing, errors, retry functionality, and product state using GetX.
│   │
│   └── cart_controller.dart
│       └── Manages cart operations including adding, updating, removing products, quantity changes, totals, and persistence.
│
├── views/
│   │
│   ├── splash/
│   │   └── splash_screen.dart
│   │       └── Displays the application logo and splash screen while checking the user's login status.
│   │
│   ├── auth/
│   │   └── login_screen.dart
│   │       └── Provides username and password fields with validation and login functionality.
│   │
│   ├── products/
│   │   │
│   │   ├── product_list_screen.dart
│   │   │   └── Displays products in a responsive grid with loading, error, empty, retry, and pull-to-refresh states.
│   │   │
│   │   ├── product_details_screen.dart
│   │   │   └── Displays complete product details with quantity selection and Add to Cart functionality.
│   │   │
│   │   └── widgets/
│   │       ├── product_card.dart
│   │       │   └── Reusable card displaying product image, title, category, rating, price, and cart action.
│   │       │
│   │       ├── product_image.dart
│   │       │   └── Reusable widget responsible for displaying product images.
│   │       │
│   │       └── product_info.dart
│   │           └── Displays reusable product information such as title, category, rating, and price.
│   │
│   └── cart/
│       │
│       ├── cart_screen.dart
│       │   └── Displays all cart products and the complete cart summary.
│       │
│       └── widgets/
│           ├── cart_badge.dart
│           │   └── Displays the reactive cart item count on the application header.
│           │
│           ├── cart_items.dart
│           │   └── Displays cart products with quantity controls and remove functionality.
│           │
│           └── cart_summary.dart
│               └── Displays the total number of items and total cart amount.
│
└── widgets/
    │
    ├── common_app_bar.dart
    │   └── Reusable application AppBar component used across screens.
    │
    ├── common_button.dart
    │   └── Reusable button component with consistent styling.
    │
    ├── empty_state_widget.dart
    │   └── Reusable UI component for displaying empty data states.
    │
    ├── shimmer_widgets.dart
    │   └── Contains skeleton loading widgets displayed while data is loading.
    │
    └── app_snackbar.dart
        └── Provides reusable success, error, and informational GetX Snackbar messages.
#### ---------------------Architecture---------------------------------------------------

The project follows a feature-based MVC architecture with GetX.

Model
data/models/

Responsible for defining application data structures such as products and cart items.

View
views/

Responsible for displaying the user interface and interacting with controllers.

Controller
controllers/

Responsible for business logic, GetX reactive state management, API operations, authentication, and cart management.

## Application Data Flow
View
  ↓
GetX Controller
  ↓
ApiService / StorageService
  ↓
HTTP API / SharedPreferences
  ↓
Model
  ↓
Reactive UI Update
## Cart Data Flow
Product Screen
      ↓
CartController
      ↓
Add / Update / Remove Product
      ↓
SharedPreferences
      ↓
Cart Data Persists After App Restart
## Authentication Flow
Splash Screen
      ↓
StorageService
      ↓
Check Login Status
      │
      ├── Logged In
      │      ↓
      │   Product List
      │
      └── Not Logged In
             ↓
           Login
## Main Technologies
Flutter – Cross-platform application development.
GetX – State management, navigation, and dependency injection.
HTTP – API integration with the Fake Store API.
SharedPreferences – Persistent storage for login status and cart data.
Shimmer – Skeleton loading placeholders.
Google Fonts – Consistent application typography.
Cached Network Image – Efficient network image loading and caching.
## Responsive Design

The application is designed to support different screen sizes, including:

Mobile

## Code Quality

# The project follows these principles:

Feature-based organization
MVC architecture
Separation of UI and business logic
Reusable widgets
Centralized constants
Centralized theme management
Centralized API communication
Centralized local storage
Reactive GetX state management
Clean and maintainable code


 










