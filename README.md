# new-swati

  new project for Trading application - 021 Trade.
as per video recording provided i try to create same design of screens
my folder structure is
```
lib/
│
├── core/
│   │
│   ├── constants/
│   │   ├── app_colors.dart
│   │   └── app_style.dart
│   │
│   ├── features/
│   │   └── watchlist/
│   │       │
│   │       ├── bloc/
│   │       │   ├── watchlist_bloc.dart
│   │       │   ├── watchlist_event.dart
│   │       │   └── watchlist_state.dart
│   │       │
│   │       ├── data/
│   │       │   └── watchlist_data.dart
│   │       │
│   │       ├── model/
│   │       │   └── stock_model.dart
│   │       │
│   │       └── ui/
│   │           │
│   │           ├── widgets/
│   │           │   ├── bottom_button.dart
│   │           │   ├── custom_searchbar.dart
│   │           │   ├── header_box.dart
│   │           │   ├── reorder_stock_list.dart
│   │           │   ├── sort_button.dart
│   │           │   ├── stock_tile.dart
│   │           │   ├── top_index.dart
│   │           │   └── watchlist_tab.dart
│   │           │
│   │           ├── edit_watchlist.dart
│   │           └── watchlist_screen.dart
│   │
│   └── utils/
│       └── responsive_helper.dart
│
└── main.dart
```

---

### ******* Explanation of Structure*****

####  `lib/`

This is the main directory where all Flutter application code resides.

-------------------------------------------------------------------

#### 1) `core/`

Contains shared logic, reusable components, and main feature modules.

----------------------------------------------------------------------

##### i) `constants/`

Holds app-wide constant values:

* `app_colors.dart` → defines colors 
* `app_style.dart` → defines text styles, themes, UI styling

-----------------------------------------------------------------

##### ii) `features/watchlist/`

Feature-based architecture for the **Watchlist module**.
-------------------------------------------------------------

######  ` bloc/`

Implements state management using BLoC pattern:

* `watchlist_bloc.dart` → main business logic
* `watchlist_event.dart` → user/actions events
* `watchlist_state.dart` → UI states

-----------------------------------------------

######  `data/`

Handles data sources:

* `watchlist_data.dart` → static/mock/API data handling

--------------------------------------------------------

######  `model/`

Defines data structures:

* `stock_model.dart` → stock entity/model

-------------------------------------------------------

######  `ui/`

Contains all UI-related code:

**Widgets (Reusable UI components):**

* `bottom_button.dart` → bottom action button
* `custom_searchbar.dart` → search input UI
* `header_box.dart` → header display
* `reorder_stock_list.dart` → draggable list UI
* `sort_button.dart` → sort button
* `stock_tile.dart` →  stock item UI
* `top_index.dart` →  top index display
* `watchlist_tab.dart` → tab navigation
-----------------------------------------------------------------------------
**Screens:**

* `watchlist_screen.dart` → main screen
* `edit_watchlist.dart` → edit/reorder screen

-------------------------------------------------------------------------------

#####  `utils/`

Utility/helper functions:

* `responsive_helper.dart` → handles responsiveness for different screen sizes

------------------------------------------------------------------------------

####  `main.dart`

Entry point of the Flutter application.

-------------------------------------------------------------------------------

******************* Architecture Highlights**************************

* Follows **feature-based structure**
* Uses **BLoC pattern** for state management
* Separates:

  * UI
  * Business logic
  * Data layer
* Promotes scalability and maintainability

-------------------------------------------------------------------------------------



