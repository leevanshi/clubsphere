# ClubSphere 🎓📱
**College Club & Event Management Android Application**

Built with **Java**, **XML Layouts**, **SQLite Database**, and **Jetpack Material Design**.

---

## 🌟 Key Features

### 🔐 1. Role-Based Authentication & Security
- **Dual Login Roles**: Toggle between **"Login as Student"** and **"Login as Admin"**.
- **Role Verification**: Admin login verifies the account role in SQLite (`role = 'admin'`). Access is denied if a non-admin attempts admin login.
- **Direct Route Guarding**: Direct navigation to `AdminActivity` is blocked for non-admins and redirects to the login screen.
- **Persistent Sessions**: User session state is preserved across app launches using `SessionManager` (`SharedPreferences`).
- **Logout Support**: Dedicated logout action available on both Admin and Student dashboards.

---

### 👑 2. Admin / Coordinator Panel (`AdminActivity`)
- **Live Club-Filtered Membership Requests**: Displays pending student join requests for the currently selected club in real time.
- **Applicant Information**: Shows applicant Name, Email, and Department for each request with one-click **Approve** and **Reject** buttons.
- **Club Management**: Add, update, or delete college clubs, including logo/image links and coordinator names.
- **Event Management**: Schedule club events with date picker, venue, description, and poster images.
- **Announcements**: Post club-wide announcements with automatic timestamping.

---

### 🎓 3. Student Experience (`HomeActivity`, `ClubListActivity`, `ClubDetailsActivity`)
- **Student Dashboard**: Welcome banner, quick action navigation, and latest announcements feed.
- **Club Discovery**: Search clubs by name or filter by category (Technical, Cultural, Sports, Entrepreneurship, etc.).
- **Interactive Club Details**:
  - View club description, coordinator details, approved member counts, and banner images.
  - Live Membership Status: **Not joined**, **Pending Approval**, **Approved Member**, **Rejected**.
  - **Join Request**: Submit a join request (prevents duplicate requests).
  - **Leave Club**: Leave a club with an interactive confirmation dialog.
  - View upcoming events and club-specific announcements.
- **My Clubs**: View all joined and pending clubs with **CSV Export** feature.
- **Events Feed**: View all upcoming campus events across all clubs.

---

### 🖼️ 4. Image System & Branding
- **Branding Logo**: Integrated `clubsphere_logo.png` across Splash/Landing, Login, and Homepage headers.
- **Custom Local Drawables**: Embedded club logos (`coding_club.png`, `cricket_club.png`, `dance_society.png`, `enterpreneuship_club.png`) in `res/drawable`.
- **Hybrid Image Loader (Glide)**: Dynamically resolves both local `res/drawable` resource names and remote HTTP/HTTPS image URLs, with fallback placeholder vectors (`ic_club_placeholder.xml`).

---

## 🗄️ Database Architecture (`SQLiteOpenHelper`)

### Tables in `clubsphere.db`:
1. `users` (`id`, `name`, `email`, `password`, `department`, `role`)
2. `clubs` (`id`, `name`, `category`, `description`, `coordinator`, `image_url`)
3. `memberships` (`id`, `user_id`, `club_id`, `status` [Pending / Approved / Rejected])
4. `events` (`id`, `club_id`, `title`, `description`, `date`, `venue`, `image_url`)
5. `announcements` (`id`, `club_id`, `title`, `message`, `created_at`)

---

## 🔑 Default Credentials

- **Admin Account**:
  - **Email**: `admin@clubsphere.com`
  - **Password**: `admin123`
  - **Role**: `admin`
- **Student Account**:
  - Register a new account via the **"New here? Register"** link on the login screen.

---

## 🚀 How to Run

1. Open Android Studio (Koala / Ladybug or newer).
2. Select **File > Open** and choose the `ClubSphere` project directory.
3. Allow Gradle to sync.
4. Select an Android Emulator or connected device (API 24 / Android 7.0 or higher) and click **Run 'app'**.
