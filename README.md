# 🐛 TaskGlitch - Bug Fixes Assignment

> **SDE Assignment**: Fixed 5 critical bugs in a Task Management Web App for sales teams

## 📋 Project Overview

TaskGlitch is a Task Management Web App designed for sales teams to track, manage, and prioritize tasks based on ROI (Return on Investment). This project was part of a bug-fixing challenge where I identified and resolved 5 critical bugs affecting UI, logic, and performance.

## 🎯 Features

- ✅ Add, edit, and delete tasks
- ✅ View detailed task information and notes
- ✅ Search & filter by status and priority
- ✅ Automatic ROI calculation (Revenue ÷ Time Taken)
- ✅ Smart sorting by ROI and priority
- ✅ Real-time metrics dashboard:
  - Total revenue
  - Time efficiency
  - Average ROI
  - Performance grade
- ✅ Import & export tasks via CSV
- ✅ Undo delete functionality
- ✅ LocalStorage-based persistence

## 🔧 Tech Stack

- **Frontend**: React 18 + TypeScript
- **UI Library**: Material-UI (MUI)
- **Build Tool**: Vite
- **State Management**: React Context API
- **Styling**: Emotion (CSS-in-JS)

## 🐛 Bugs Fixed

### 1️⃣ Double Fetch Issue
**Problem**: API was called twice on page load due to React.StrictMode and duplicate useEffect.

**Solution**: 
- Removed `<React.StrictMode>` wrapper
- Deleted duplicate fetch logic in `useTasks.ts`

**Commit**: `fix double fetch on load`

---

### 2️⃣ Undo Snackbar Bug
**Problem**: Deleted task state wasn't cleared when snackbar closed, causing incorrect undo behavior.

**Solution**: 
- Added `clearLastDeleted()` method to context
- Implemented proper cleanup in `handleCloseUndo`

**Commit**: `fix undo snackbar state clearing`

---

### 3️⃣ Unstable Sorting
**Problem**: Tasks with same ROI/priority flickered and reordered randomly on each render.

**Solution**: 
- Replaced `Math.random()` tie-breaker with stable alphabetical sorting by title and ID

**Commit**: `fix unstable sorting with stable tie-breaker`

---

### 4️⃣ Double Dialog Opening
**Problem**: Clicking Edit/Delete buttons triggered both the action dialog AND the view dialog.

**Solution**: 
- Added `event.stopPropagation()` to Edit and Delete button handlers

**Commit**: `prevent double dialog opening`

---

### 5️⃣ ROI Calculation Errors
**Problem**: Division by zero caused `Infinity` and `NaN` values in ROI calculations.

**Solution**: 
- Added comprehensive input validation
- Return `null` for invalid calculations
- Ensure all ROI values are finite numbers

**Commit**: `fix ROI calculation errors`

## 🚀 Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/Rajadi16/Rajput_Aditya_Singh-task-glitch.git

# Navigate to project directory
cd Rajput_Aditya_Singh-task-glitch

# Install dependencies
npm install

# Start development server
npm run dev
```

The app will be available at `http://localhost:5173/`

### Build for Production

```bash
npm run build
```

The production-ready files will be in the `dist/` directory.

### Preview Production Build

```bash
npm run preview
```

## 📁 Project Structure

```
src/
├── components/          # React components
│   ├── TaskTable.tsx   # Main task table with CRUD operations
│   ├── TaskForm.tsx    # Add/Edit task dialog
│   ├── UndoSnackbar.tsx # Undo delete notification
│   ├── MetricsBar.tsx  # Performance metrics display
│   └── ...
├── context/            # React Context providers
│   ├── TasksContext.tsx # Task state management
│   └── UserContext.tsx  # User information
├── hooks/              # Custom React hooks
│   └── useTasks.ts     # Task operations logic
├── utils/              # Utility functions
│   ├── logic.ts        # ROI calculations & sorting
│   ├── csv.ts          # CSV import/export
│   └── seed.ts         # Sample data generation
├── types.ts            # TypeScript type definitions
├── theme.ts            # MUI theme configuration
└── App.tsx             # Main application component
```

## 🧪 Testing

All bugs were manually tested and verified:

- ✅ Single fetch on page load (no duplicates)
- ✅ Undo snackbar clears state properly
- ✅ Consistent task sorting (no flickering)
- ✅ Single dialog opens per action
- ✅ Valid ROI calculations (no Infinity/NaN)

## 📝 Git Commit History

All fixes were committed individually with clean, descriptive messages:

```
1. fix double fetch on load
2. fix undo snackbar state clearing
3. fix unstable sorting with stable tie-breaker
4. prevent double dialog opening
5. fix ROI calculation errors
```

## 🌐 Live Demo

**Deployed URL**: [Coming Soon - Deploy to Vercel/Netlify]

## 👨‍💻 Author

**Aditya Singh Rajput**

- GitHub: [@Rajadi16](https://github.com/Rajadi16)
- Repository: [Rajput_Aditya_Singh-task-glitch](https://github.com/Rajadi16/Rajput_Aditya_Singh-task-glitch)

## 📄 License

This project was created as part of an SDE assignment.

## 🙏 Acknowledgments

- Original repository: [sanjeev-cmyk/task-glitch](https://github.com/sanjeev-cmyk/task-glitch)
- Assignment provided by the hiring team

---

**Note**: This project demonstrates bug-fixing skills, code analysis, debugging techniques, and clean git practices.
