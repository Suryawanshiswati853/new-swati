# new-swati

lib/
├── core/ # Shared infrastructure
│ ├── constants/ # App-wide constants
│ │ ├── app_assets.dart
│ │ ├── app_colors.dart
│ │ ├── app_style.dart
│ │ └── export.dart # Re‑exports core constants & widgets
│ ├── theme/ # Theming
│ │ ├── app_theme.dart
│ │ └── theme_cubit.dart # ( system theme only)
│ ├── utils/ # Helpers
│ │ ├── filter_utils.dart
│ │ ├── reponsive.dart # Custom responsive helper (percentage‑based)
│ │ └── validators.dart
│ └── widgets/ # Reusable UI components
│ ├── animated_section_card.dart
│ ├── app_snack_bar.dart
│ ├── custom_button.dart
│ ├── custom_chip.dart
│ ├── custom_drawer.dart
│ ├── custom_textfield.dart
│ ├── empty_widget.dart
│ ├── error_widget.dart
│ ├── loading_widget.dart
│ ├── roi_projection_chart.dart
│ ├── search_filter_bar.dart
│ └── theme_aware_image.dart
├── data/ # Data layer
│ ├── local/ # Local storage
│ │ └── shared_preferences_helper.dart
│ ├── mock/ # Mock API responses
│ │ └── mock_deals.dart
│ ├── models/ # Data models (Deal, User)
│ │ ├── deal_model.dart
│ │ └── user_model.dart
│ └── repositories/ # Repository pattern
│ ├── auth_repository.dart
│ ├── deal_repository.dart
│ └── interest_repository.dart
├── logic/ # BLoC state management
│ ├── auth/ # Authentication
│ │ ├── auth_bloc.dart
│ │ ├── auth_event.dart
│ │ └── auth_state.dart
│ ├── deals/ # Deals filtering & loading
│ │ ├── deals_bloc.dart
│ │ ├── deals_event.dart
│ │ └── deals_state.dart
│ └── interests/ # User interests
│ ├── interest_bloc.dart
│ ├── interest_event.dart
│ └── interest_state.dart
├── presentation/ # UI screens
│ ├── auth/
│ │ └── login_screen.dart
│ ├── deal_details/
│ │ └── deal_details_screen.dart
│ ├── deal_list/
│ │ └── deal_list_screen.dart
│ ├── home/
│ │ └── home_screen.dart
│ ├── interests/
│ │ └── my_interests_screen.dart
│ └── widgets/ # Screen-specific widgets
│ ├── animated_search_bar.dart
│ ├── animated_text.dart
│ ├── deal_card.dart
│ └── deal_chip.dart
├── app.dart # App entry point (MultiBlocProvider)
└── main.dart # App initialization + route setup

##  Architecture Explanation
The project follows **Clean Architecture** with three main layers:

### 1. **Core Layer** (`lib/core`)
- **Constants** – centralised colours, text styles, and asset paths.
- **Theme** – light/dark theme definitions (`AppTheme`). The app respects the system theme (`ThemeMode.system`) – no manual toggle.
- **Utils** – reusable helpers:
  - `Responsive` – percentage‑based sizing (width, height, font) to avoid web overflow.
  - `FilterUtils` – client‑side filtering logic.
  - `Validators` – email/password validation.
- **Widgets** – pure, reusable UI components (buttons, chips, text fields, empty states, etc.). No business logic.

### 2. **Data Layer** (`lib/data`)
- **Local** – `SharedPreferences` helper for session and interests persistence.
- **Mock** – `mock_deals.dart` provides dummy deals. Real API can replace this later.
- **Models** – `Deal` and `User` data classes (plain Dart objects).
- **Repositories** – abstract the data source. Repositories are injected into BLoCs, making them testable and decoupled.

### 3. **Logic Layer** (`lib/logic`)
- **BLoC** – manages state for authentication, deals, and interests.
  - `AuthBloc` – handles login/logout and session checking.
  - `DealsBloc` – loads deals, applies filters, updates filtered list.
  - `InterestBloc` – stores/removes interested deal IDs in `SharedPreferences`.
- **Events** – user actions (e.g., `LoginRequested`, `UpdateFilters`, `AddInterest`).
- **States** – loading, loaded, error, and specific data states.

### 4. **Presentation Layer** (`lib/presentation`)
- **Screens** – each screen is a `StatelessWidget` or `StatefulWidget` that observes a BLoC.
- **Screen‑specific widgets** – `deal_card.dart`, `animated_text.dart`, etc. – organised under each screen or in a shared `presentation/widgets` folder.
| Decision | Rationale |
|----------|-----------|
| **BLoC for state management** | Separates UI from logic, predictable state transitions, easy testing, and strong community support. |
| **Custom `Responsive` class** | Avoids `sizer` web overflow; uses screen percentage (`MediaQuery`). All dimensions are percentage‑based, ensuring consistency on mobile, tablet, and web. |
| **No manual theme toggle** | App follows system dark/light mode. Simpler UX and less state to manage. |
| **Client‑side filtering** | Mock data size is small; no need for backend API calls. Filtering is fast and reactive. |
| **`IndexedStack` for tab switching** | Keeps both `DealListScreen` and `MyInterestsScreen` in memory, avoiding unnecessary rebuilds. |
| **Repository pattern** | Abstracts data sources (local/mock/remote). Easy to swap implementation later. |
| **Centralised SnackBar service** | `AppSnackBar` ensures consistent, theme‑aware messages across the app. |
| **Export files** | `core/constants/export.dart` and `logic/auth/auth.dart` reduce import boilerplate. |
| **Animations** | `AnimationController` + `addPostFrameCallback` guarantees entrance animations (fade, slide) work on first appearance. Pie chart uses `fl_chart` with custom grow animation. |
##  Features

-  **Mock Authentication** – email/password login . Session stored in `SharedPreferences`.
- **Deal Listing** – cards display company name, industry, investment (₹L), ROI (%), risk level (Low/Medium/High), and status (Open/Closed).
-  **Search & Filter** – global search (company, ROI, industry, risk, status, investment). Range filters for ROI and investment, plus exact filters for risk and industry.
-  **Deal Details** – overview, financial highlights, and an animated pie chart (ROI projection over 5 years).
-  **Express Interest** – store interested deals; remove from interests.
-  **Dark / Light Mode** – follows system theme automatically.
-  **Animations** – cards fade/slide in.






