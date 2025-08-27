# Turbo Setup Tauri + React + TypeScript + Tailwind

A modern and efficient Tauri starter template with React, TypeScript, Tailwind CSS, and various development tools pre-configured.

## 🚀 Features

- ⚡️ [React 19](https://react.dev/) with [TypeScript](https://www.typescriptlang.org/)
- 🎨 [Tailwind CSS](https://tailwindcss.com/) for styling
- 📦 [Vite](https://vitejs.dev/) for fast development and building
- 🔍 [ESLint](https://eslint.org/) for code linting
- 💅 [Prettier](https://prettier.io/) for code formatting
- 🐶 [Husky](https://typicode.github.io/husky/) for Git hooks
- 📋 [Commitlint](https://commitlint.js.org/) for conventional commits
- 🏪 [Zustand](https://zustand-demo.pmnd.rs/) for state management
- 🌐 [React Router](https://reactrouter.com/) for routing
- 📅 [Day.js](https://day.js.org/) for date manipulation
- 🔄 [Axios](https://axios-http.com/) for HTTP requests
- 🔄 [SWR](https://swr.vercel.app/) for data fetching and caching
- 🔗 [nuqs](https://nuqs.47ng.com/) for URL query state management
- 🎭 [rc-dialog](https://dialog-react-component.vercel.app/) for modal and dialog components
- 💅 [styled-components](https://styled-components.com/) for CSS-in-JS styling
- 🎨 [tailwind-merge](https://github.com/dcastil/tailwind-merge) for merging Tailwind CSS classes
- 🖥️ [Tauri](https://tauri.app/) for cross-platform desktop applications

## 🛠️ Prerequisites

- Node.js (v18 or higher)
- Bun (latest version)
- Rust (latest stable version) - for Tauri desktop functionality

## 📦 Installation

# Clone the repository

```
git clone https://github.com/khoivudevz/turbo-setup-tauri-react
```

# Install dependencies

```
bun install
```

## 🚀 Development

### Web Development

```bash
bun dev # Development mode
bun dev:stg # Staging mode
bun dev:prod # Production mode
```

### Desktop Application (Tauri)

```bash
bun run tauri:dev # Start Tauri desktop app in development mode
bun run tauri:build # Build Tauri desktop app for production
```

### Building for Production

```bash
bun build # Production build (web)
bun build:stg # Staging build (web)
bun build:dev # Development build (web)
bun run tauri:build # Production build (desktop app)
```

## 📁 Development

```
src/
├── assets/           # Static assets (images, fonts, icons)
├── components/       # Reusable UI components
├── configs/          # Configuration files (env, http, app urls)
├── constants/        # Application constants and shared values
├── hooks/            # Custom React hooks (useNews, useAuth, useFetch, useMutation, useKeyPress)
├── layouts/          # Layout components and templates
├── pages/            # Page components
├── providers/        # React context providers
├── router/           # Routing configuration
├── services/         # Browser services (cookies, localStorage, data persistence)
├── store/            # State management with Zustand
├── styles/           # Global styles and Tailwind imports
├── types/            # TypeScript type definitions
├── utils/            # Utility functions
└── views/            # View components
```

## 🖥️ Desktop Application (Tauri)

This project can be run as a cross-platform desktop application using Tauri. The desktop app provides:

- **Cross-platform support**: Windows, macOS, and Linux
- **Native performance**: Rust backend with web frontend
- **Small bundle size**: Efficient resource usage
- **Native system integration**: File system access, notifications, system tray

### Tauri Configuration

The Tauri configuration is located in `src-tauri/tauri.conf.json`. Key settings include:

- **App name**: "Turbo setup Tauri x React 19, TypeScript & Tailwind and more..."
- **Window title**: "Turbo setup Tauri x React 19, TypeScript & Tailwind and more..."
- **Window size**: 800x600 (resizable)
- **Web assets**: Built from React app in `build/` directory
- **Dev server**: http://localhost:8000

### Building for Different Platforms

```bash
# Build for current platform
bun run tauri:build

# The built application will be in src-tauri/target/release/bundle/
```

## 🔧 Configuration

### Environment Variables

Create `.env` files for different environments:

```
VITE_ENV=development
VITE_API_URL=your_api_url
```

### TypeScript

The project includes two TypeScript configurations:

- `tsconfig.app.json` - Application configuration
- `tsconfig.node.json` - Node.js configuration

### ESLint & Prettier

- ESLint is configured with TypeScript and React rules
- Prettier is set up with custom formatting rules
- Pre-commit hooks ensure code quality

## 🗄️ Browser Services

The project includes browser services for data persistence and session management:

### Cookie Service

Handles authentication token storage and retrieval:

```typescript
import {saveAuth, removeAuth, getAuth} from '@/services/cookie.service'

// Save authentication token
saveAuth('your-jwt-token')

// Retrieve authentication token
const token = getAuth()

// Remove authentication token
removeAuth()
```

### Local Storage Service

Provides utilities for localStorage operations:

```typescript
import {
	localStorageServices,
	localStorageKey,
} from '@/services/localStorage.service'

// Save user data
const userData = {id: '1', name: 'John Doe'}
localStorageServices.setLocalStorage(userData, localStorageKey.USER_INFOR)

// Retrieve user data
const user = localStorageServices.getLocalStorage(localStorageKey.USER_INFOR)

// Remove user data
localStorageServices.removeLocalStorage(localStorageKey.USER_INFOR)
```

### Available Storage Keys

The service includes predefined keys for consistent data storage:

- `USER_INFOR`: User profile information
- And other application-specific keys as needed

## 🌍 Internationalization (i18n)

This project uses [i18next](https://www.i18next.com/) with [react-i18next](https://react.i18next.com/) for internationalization support. The translations are stored in JSON files located in the `src/i18n/translations` directory.

### Adding a New Language

1. Create a new JSON file in the `src/i18n/translations` directory with the language code as the filename (e.g., `fr.json` for French).

2. Add your translations in the new JSON file. For example:

   ```json
   {
   	"translation": {
   		"welcome": "Bienvenue à React, tailwindcss et plus"
   	}
   }
   ```

### Switching Languages

The `SwitchLanguage` component allows users to switch between available languages. It uses the `useTranslation` hook from `react-i18next` to change the language dynamically.

Example usage in a component:

```typescript:src/views/HomeView/HomeView.tsx
import {useTranslation} from 'react-i18next'
import SwitchLanguage from '@/components/SwitchLanguage/SwitchLanguage'

const HomeView = () => {
  const {t} = useTranslation()
  return (
    <div>
      <p>{t('welcome')}</p>
      <SwitchLanguage />
    </div>
  )
}
```

## 📡 Data Fetching

This project uses [SWR](https://swr.vercel.app/) for data fetching, which provides features like:

- Automatic caching and revalidation
- Real-time experience
- Request deduplication
- TypeScript ready
- Suspense mode support

### Custom Hooks

The project includes custom hooks for data fetching:

#### useNews Hook

A custom hook for fetching news data:

```typescript
import useNews from '@/hooks/useNews'

const MyComponent = () => {
  const { news, isLoading, error } = useNews()

  if (isLoading) return <div>Loading...</div>
  if (error) return <div>Error loading news</div>

  return (
    <div>
      {news?.map(item => (
        <div key={item.ticker}>{item.name}</div>
      ))}
    </div>
  )
}
```

The `useNews` hook provides:

- Automatic data fetching and caching
- Loading state management
- Error handling
- Type-safe data access

## 🔐 Authentication System

This project includes a complete authentication system built with Zustand for state management and provides both cookie and localStorage persistence.

### Authentication Hook

The `useAuth` hook provides a simple interface for authentication:

```typescript
import useAuth from '@/hooks/useAuth'

const MyComponent = () => {
  const {
    user,
    isAuthenticated,
    login,
    logout,
    userName,
    userEmail,
    userId
  } = useAuth()

  const handleLogin = async () => {
    // After successful API authentication
    const userData = {
      id: '1',
      email: 'user@example.com',
      name: 'John Doe',
      avatar: 'https://example.com/avatar.jpg',
      role: 'user'
    }
    const token = 'your-jwt-token'

    login(userData, token)
  }

  const handleLogout = () => {
    logout()
  }

  return (
    <div>
      {isAuthenticated ? (
        <div>
          <p>Welcome, {userName}!</p>
          <button onClick={handleLogout}>Logout</button>
        </div>
      ) : (
        <button onClick={handleLogin}>Login</button>
      )}
    </div>
  )
}
```

### Authentication Features

- **Persistent Sessions**: Automatic session persistence using cookies and localStorage
- **Type Safety**: Full TypeScript support with defined user and auth types
- **State Management**: Zustand store for global authentication state
- **Helper Functions**: Convenient access to user properties and authentication status
- **Auto-initialization**: Automatic session restoration on app load

### Authentication Types

The authentication system includes comprehensive TypeScript types:

```typescript
interface User {
	id: string
	email: string
	name: string
	avatar?: string
	role?: string
}

interface LoginCredentials {
	email: string
	password: string
}
```

## 🎭 Modal System

The project includes a robust modal management system using rc-dialog and Zustand.

### Modal Provider

All modals are managed through the `ModalsProvider` component:

```typescript
import ModalsProvider from '@/providers/ModalsProvider'

// Wrap your app with the provider
<ModalsProvider>
  <App />
</ModalsProvider>
```

### Using Modals

Modals are managed through the modal store:

```typescript
import useModalStore from '@/store/useModal.store'
import { MODAL_KEYS } from '@/constants/modals.constant'

const MyComponent = () => {
  const { openModal, closeModal } = useModalStore()

  const handleOpenModal = () => {
    openModal(MODAL_KEYS.DEMO_MODAL, {
      title: 'Demo Modal',
      data: 'some data'
    })
  }

  const handleCloseModal = () => {
    closeModal(MODAL_KEYS.DEMO_MODAL)
  }

  return (
    <button onClick={handleOpenModal}>
      Open Modal
    </button>
  )
}
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes using conventional commits
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License.
