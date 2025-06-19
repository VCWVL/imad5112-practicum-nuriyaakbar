# Music Playlist Manager App

A simple Android application (package: `com.example.musicplaylstmanager`) for managing a personal music playlist.

## Core Features:

*   **Add Songs:** Input song title, artist, rating (1-5), and comments via a dialog.
    *   *Note: Currently limits playlist to 4 songs for this demo version.*
*   **View Playlist Details:** (Functionality handled by `DetailActivity` - not shown in this snippet).
*   **Exit Application:** Closes the app.

## Main Components:

*   **`MainActivity.kt`**:
    *   Main screen with "Add Song", "Next" (to `DetailActivity`), and "Exit" buttons.
    *   Uses `findViewById` with IDs: `R.id.btnAdd`, `R.id.btnNext`, `R.id.btnExit`.
    *   Displays an `AlertDialog` for adding songs using `R.layout.layout` (for the dialog's view).
    *   In the dialog, expects EditTexts with IDs: `R.id.etTitle`, `R.id.etArtist`, `R.id.etRating`, `R.id.etComments`.
*   **`Song.kt`**:
    *   A `data class` to store song information (`title`, `artist`, `rating`, `comments`).
*   **Global Playlist:** A `MutableList<Song>` named `playlist` is stored in `MainActivity.companion object` to hold song data.

## How to Run:

1.  Open the project in Android Studio.
2.  Ensure you have the corresponding layout files:
    *   `res/layout/activity_main.xml` (with `Button` IDs: `btnAdd`, `btnNext`, `btnExit`).
    *   `res/layout/layout.xml` (with `EditText` IDs: `etTitle`, `etArtist`, `etRating`, `etComments`).
    *   A layout for `DetailActivity`.
3.  Ensure `DetailActivity` is created and declared in `AndroidManifest.xml`.
4.  Build and run on an Android emulator or device.

This app demonstrates basic Android UI interaction, dialogs, data classes, and Activity navigation in Kotlin.

READ ME FOR SCREEN 2:

# Music Playlist Manager App - DetailActivity

This `README` section focuses on the `DetailActivity.kt` (package: `com.example.musicplaylstmanager`), which is responsible for displaying the details of the music playlist.

## Core Features of `DetailActivity`:

*   **Display Playlist:** Shows a list of all songs currently in the `MainActivity.playlist`. Each song's title, artist, rating, and comments are displayed.
*   **Calculate Average Rating:** Computes and displays the average rating of all songs in the playlist.
*   **Return to Main Screen:** Allows the user to navigate back to `MainActivity`.

## Components:

*   **`DetailActivity.kt`**:
    *   Sets its content view from `R.layout.activity_screen2`.
    *   Interacts with UI elements from `activity_screen2.xml` using `findViewById` with the following IDs:
        *   `Button`: `R.id.btnShow` (to display the song list)
        *   `Button`: `R.id.btnAverage` (to calculate and show the average rating)
        *   `Button`: `R.id.btnReturn` (to go back to `MainActivity`)
        *   `TextView`: `R.id.tvDetails` (to display song details or the average rating)
    *   Retrieves song data from the static `MainActivity.playlist`.

## Functionality:

1.  **Show Songs (`btnShow`):**
    *   Iterates through the `MainActivity.playlist`.
    *   Formats the details of each song into a string.
    *   Sets the formatted string to the `tvDetails` TextView.

2.  **Calculate Average (`btnAverage`):**
    *   Calculates the sum of ratings from all songs in `MainActivity.playlist`.
    *   Computes the average (handles empty list case to prevent division by zero).
    *   Displays the average rating in the `tvDetails` TextView, formatted to two decimal places.

3.  **Return (`btnReturn`):**
    *   Calls `finish()` on the `DetailActivity`, closing it and returning the user to the previous screen (presumably `MainActivity`).

## Requirements for `DetailActivity` to Function:

*   **`MainActivity.playlist`:** This activity relies on `MainActivity` having a publicly accessible static list named `playlist` (i.e., `MainActivity.Companion.playlist`) that holds `Song` objects.
*   **`Song` Data Class:** A `Song` data class with properties like `title`, `artist`, `rating`, and `comments` must be defined and accessible.
*   **`R.layout.activity_screen2`:** A layout file named `activity_screen2.xml` must exist in `res/layout/` and contain the UI elements with the IDs mentioned above (`btnShow`, `btnAverage`, `btnReturn`, `tvDetails`).
*   **Manifest Declaration:** `DetailActivity` must be declared in the `AndroidManifest.xml`.

This activity serves as the detailed view component of the Music Playlist Manager application.



