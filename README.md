# StudentCard

A personal profile card app built with **React Native** and **Expo**. It is the Week 1 lab project for **Mobile Application Development** at the Department of Computer Science, Faculty of Science and Technology, American International University-Bangladesh (AIUB), Fall 26-27.

**Faculty:** Md. Sazid Uddin

StudentCard shows a student's name, ID, department, bio, and skills. A Follow/Unfollow button toggles using React state. You build it step by step, and each part adds one new React Native concept.

## Features

- Avatar with initials generated from the student's name
- Student ID badge, department, and bio
- Skills shown as wrapping badges, using `map()`. The skills section is optional.
- Follow/Unfollow toggle with conditional styling
- One reusable `ProfileCard` component, rendered several times with different props
- Each card keeps its own follow state

## Concepts Covered

| Part | Concept                         | What it adds                           |
| ---- | ------------------------------- | -------------------------------------- |
| 1    | JSX, `StyleSheet`, Flexbox      | A static profile card                  |
| 2    | Props                           | A reusable `ProfileCard` component     |
| 3    | `useState`                      | The Follow/Unfollow button             |
| 4    | Lists and conditional rendering | The skills section, built with `map()` |
| 5    | Git and GitHub                  | Committing and pushing the project     |

## Tech Stack

- [React Native](https://reactnative.dev/)
- [Expo](https://expo.dev/), **SDK 54**
- TypeScript
- Expo Router (file-based routing, `app/(tabs)`)

## Prerequisites

- [Node.js](https://nodejs.org) (LTS). Check with `node --version` and `npm --version`.
- [VS Code](https://code.visualstudio.com/) with the ESLint and Prettier extensions
- [Git](https://git-scm.com/). Check with `git --version`.
- _(Optional)_ **Expo Go** on your Android or iOS phone, with your phone and laptop on the same Wi-Fi network

> **Note:** This course requires **Expo SDK 54**, so your Expo Go app must support SDK 54. For Android, you can install the compatible
> [Expo Go 54.0.8 APK](https://github.com/expo/expo-go-releases/releases/download/Expo-Go-54.0.8/Expo-Go-54.0.8.apk).

You do not need Android Studio or Xcode.

## Getting Started

### Run this repository

```bash
git clone https://github.com/sazid-uddin/MAD-Fall-26-StudentCard.git
cd MAD-Fall-26-StudentCard
npm install
npx expo start
```

### Open the app

- **On your phone:** Scan the QR code shown in the terminal. On Android, use the Expo Go app. On iOS, use the built-in Camera app.
- **In the browser:** Press `w` in the terminal running Expo.

Saving a file reloads the app automatically. If the app shows an old version, press `r` in the Expo terminal to force a reload.

### Create the project from scratch (as in the lab)

```bash
npx create-expo-app@latest StudentCard --template default@sdk54
cd StudentCard
npx expo start
```

Then add JSX support to `tsconfig.json` under `compilerOptions`:

```json
{
    "extends": "expo/tsconfig.base",
    "compilerOptions": {
        "jsx": "react-native",
        "strict": true,
        "paths": {
            "@/*": ["./*"]
        }
    }
}
```

## Project Structure

```
StudentCard/
├── app/
│   └── (tabs)/
│       └── index.tsx        # Home screen: renders the ProfileCard list
├── components/
│   └── profile-card.tsx     # Reusable ProfileCard (props, state, skills list)
├── assets/                  # App icon, splash screen, static images
├── app.json                 # Expo app configuration
├── package.json             # Dependencies and npm scripts
└── tsconfig.json            # TypeScript configuration
```

## Usage

`ProfileCard` takes these props:

| Prop         | Type       | Required | Description                                                |
| ------------ | ---------- | -------- | ---------------------------------------------------------- |
| `name`       | `string`   | Yes      | Full name. Initials for the avatar are generated from it.  |
| `studentId`  | `string`   | Yes      | Student ID, shown as a badge                               |
| `department` | `string`   | Yes      | Department or role line                                    |
| `bio`        | `string`   | Yes      | Short bio                                                  |
| `skills`     | `string[]` | No       | Skills shown as badges. If omitted, the section is hidden. |

```tsx
<ProfileCard name="Asadul Haque" studentId="22-12345-1" department="Computer Science — AIUB" bio="Passionate about mobile development and building tools that make everyday life easier." skills={["React Native", "JavaScript", "Node.js", "PostgreSQL"]} />
```

## Practice Exercises

These are ungraded but recommended:

1. **Stats row:** Add Followers and Following counts. The Followers count goes up when the card is followed and down when unfollowed.
2. **Colour theme prop:** Add a `themeColor` prop that sets the avatar and Follow button colours.
3. **Output tracing:** Predict the final value of `count` after pressing `double → double → reset → double`, starting from `useState(5)`.

## Troubleshooting

| Problem                                                   | Fix                                                                                                               |
| --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `Text strings must be rendered within a <Text> component` | Wrap all visible text in `<Text>`. Never put a raw string directly inside `<View>`.                               |
| `Cannot read properties of undefined (reading 'map')`     | The `skills` prop was not passed. Guard it with `skills && skills.length > 0`, or set a default of `skills = []`. |
| `Unable to resolve module`                                | Check the file path and capitalisation. File names are case-sensitive.                                            |
| `StyleSheet.create is not a function`                     | Import `StyleSheet` from `react-native`.                                                                          |
| `useState is not defined`                                 | Add `import { useState } from 'react';`.                                                                          |
| `create-expo-app` fails on a lab PC                       | Create an `npm` folder in `C:/Users/Student/AppData/Roaming/` and rerun the command.                              |
| Phone shows an old version                                | Press `r` in the Expo terminal, or shake the phone and tap **Reload**.                                            |

## Useful Commands

| Command                    | Description                                                                                  |
| -------------------------- | -------------------------------------------------------------------------------------------- |
| `npx expo start`           | Start the development server and show the QR code                                            |
| `npx expo start --tunnel`  | Start the server using a tunnel (useful when the phone and laptop are on different networks) |
| `r` (in the Expo terminal) | Force reload on connected devices                                                            |
| `Ctrl+C`                   | Stop the development server                                                                  |
| `git add .`                | Stage all changes                                                                            |
| `git commit -m "message"`  | Commit staged changes                                                                        |
| `git push`                 | Push commits to GitHub                                                                       |

## Author

**Md. Sazid Uddin**
Department of Computer Science, Faculty of Science and Technology, AIUB
