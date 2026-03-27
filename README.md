# TripTracker Notes (随行Notes)

A bilingual (English/Chinese) travel trip planner and checklist app built with React Native and Expo. 

Users can create trips, manage category-based checklists, track transport and accommodations, log expenses, and generate AI-powered itineraries using Google Gemini.

## Key Features

- **Smart Checklists**: Manage packing, documents, and shopping with drag-to-reorder categories.
- **Transport & Accommodation**: Track flights, trains, hotels, and check-in times in one place.
- **AI Itinerary Planner**: Generate day-by-day travel plans based on your destination and checklists.
- **Voice Input**: Add checklist items hands-free using AI audio transcription.
- **Bilingual**: Full support for English and Simplified Chinese.
- **Privacy First**: No accounts, no cloud storage. All data stays locally on your device.
- **Export**: Share your trip details and AI itineraries as PDFs.

## Tech Stack

- **Framework**: React Native 0.81, Expo SDK 54, React 19
- **Language**: TypeScript (strict mode)
- **Routing**: Expo Router 6
- **Storage**: `@react-native-async-storage/async-storage`
- **AI Integration**: Google Gemini 2.5 Flash (via Cloudflare Worker proxy)
- **UI/UX**: `rn-emoji-keyboard`, `reanimated-color-picker`, `react-native-draggable-flatlist`, `expo-haptics`

## Local Development

1. Install dependencies:
   ```bash
   npm install
   ```

2. Set up environment variables:
   Create a `.env` file in the root directory. You can either use a direct Gemini API key for local testing, or point to your Cloudflare proxy:
   ```env
   # Local testing (direct to Google)
   EXPO_PUBLIC_GEMINI_API_KEY="your-gemini-api-key"
   
   # Or use the production proxy
   EXPO_PUBLIC_GEMINI_PROXY_URL="https://your-worker.your-subdomain.workers.dev"
   ```

3. Start the Expo development server:
   ```bash
   npx expo start --clear
   ```

## Production Build & Deployment

This project uses EAS (Expo Application Services) for cloud builds and App Store submission.

1. Build the iOS app:
   ```bash
   eas build --platform ios
   ```

2. Submit to TestFlight / App Store Connect:
   ```bash
   eas submit --platform ios --latest
   ```

*Note: The production build requires `EXPO_PUBLIC_GEMINI_PROXY_URL` to be set as a plaintext environment variable in your EAS project settings, as `.env` is gitignored and not uploaded to EAS.*

## AI Proxy Setup

To protect the Gemini API key in production, the app routes AI requests through a Cloudflare Worker. See `server/PROXY-SETUP.md` for deployment instructions.