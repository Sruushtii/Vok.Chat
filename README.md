# VokChat - Secure Peer-to-Peer Video Calling

<div align="center">

![VokChat Logo](https://img.shields.io/badge/VokChat-Secure%20Video%20Calling-000000?style=for-the-badge&logo=video&logoColor=white)

**Connect. Share. Heal.**  
*Your Thoughts, Fully Protected. End-to-End Encrypted.*

[![React](https://img.shields.io/badge/React-19.1.0-61DAFB?style=flat-square&logo=react)](https://reactjs.org/)
[![Socket.IO](https://img.shields.io/badge/Socket.IO-4.8.1-010101?style=flat-square&logo=socket.io)](https://socket.io/)
[![WebRTC](https://img.shields.io/badge/WebRTC-Peer--to--Peer-0088CC?style=flat-square&logo=webrtc)](https://webrtc.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-4.1.11-38B2AC?style=flat-square&logo=tailwind-css)](https://tailwindcss.com/)
[![Vite](https://img.shields.io/badge/Vite-7.0.4-646CFF?style=flat-square&logo=vite)](https://vitejs.dev/)

</div>

---

## About VokChat

VokChat is a modern, secure video calling platform designed for confidential conversations. Built with privacy-first principles, it enables direct peer-to-peer connections with end-to-end encryption, ensuring your conversations remain private and secure.

###  Mission
To provide a safe, supportive, and empowering space for meaningful conversations through cutting-edge technology and thoughtful design.

### Core Values
- **Confidential** - Your conversations stay private
- **Supportive** - Designed for meaningful connections  
- **Empowering** - Technology that serves human connection

---

## Technical Architecture

### System Overview

```mermaid
graph TB
    subgraph "Frontend (React + Vite)"
        A[React App] --> B[WebRTC Client]
        B --> C[Socket.IO Client]
        A --> D[UI Components]
        A --> E[React Router]
    end
    
    subgraph "Backend (Node.js + Express)"
        F[Express Server] --> G[Socket.IO Server]
        G --> H[Room Management]
        H --> I[Signaling Service]
    end
    
    subgraph "Peer-to-Peer Connection"
        J[User A] -->|WebRTC| K[User B]
        J -->|STUN/TURN| L[ICE Servers]
        K -->|STUN/TURN| L
    end
    
    C --> G
    G --> C
    B --> J
    B --> K
    E --> A
```

### Technology Stack

#### Frontend
- **React 19.1.0** - Modern UI framework with hooks
- **React Router 6.8.0** - Client-side routing for URL-based navigation
- **Vite 7.0.4** - Lightning-fast build tool
- **Tailwind CSS 4.1.11** - Utility-first CSS framework
- **Socket.IO Client 4.8.1** - Real-time communication
- **React Icons 5.5.0** - Beautiful icon library

#### Backend
- **Node.js** - Server runtime
- **Express 5.1.0** - Web framework
- **Socket.IO 4.8.1** - Real-time bidirectional communication
- **CORS** - Cross-origin resource sharing

#### Core Technologies
- **WebRTC** - Peer-to-peer video/audio streaming
- **STUN/TURN Servers** - NAT traversal and relay
- **ICE Protocol** - Connection establishment

---

## Features

### Core Functionality
- **One-to-One Video Calls** - High-quality peer-to-peer video
- **Audio Support** - Crystal clear voice communication
- **Smart URL Sharing** - Shareable links like `vok-chat.app/ABC123`
- **Real-time Controls** - Mute, pause video, end call
- **Responsive Design** - Works on desktop and mobile
- **Auto Quality Adaptation** - Automatic video quality adjustment based on connection

### Smart URL Sharing
- **Direct Links** - `vok-chat.app/ABC123` for instant joining
- **Copy Link** - One-click copy of shareable URL
- **Native Sharing** - Share via WhatsApp, Email, SMS, etc.
- **Mobile Optimized** - Perfect for mobile sharing

### Mobile Features
- **Camera Rotation** - Switch between front/back cameras
- **User Leave Notifications** - Real-time notifications when peers leave
- **Touch-Optimized** - Designed for mobile interaction
- **Responsive Layout** - Side-by-side video on desktop, stacked on mobile

### Technical Features
- **WebRTC** - Standard web technology
- **STUN Servers** - NAT traversal support
- **Encrypted Media** - SRTP/SRTCP protection
- **Low Latency** - Direct peer connections
- **Auto Quality Switching** - Maintains high audio quality even when video quality adapts

---

## Security & Privacy Features

### End-to-End Encryption
- **Direct P2P Connection** - No server involvement in media streams
- **WebRTC Encryption** - Built-in SRTP/SRTCP encryption
- **Session Isolation** - Unique room codes for each session

### Privacy Protection
- **No Account Required** - Anonymous usage
- **No Data Storage** - Conversations aren't stored
- **Session-Based** - Temporary connections only

### Security Measures
```mermaid
sequenceDiagram
    participant UserA as User A
    participant Server as Signaling Server
    participant UserB as User B
    
    UserA->>Server: Join Room (Session Code)
    Server->>UserA: Room Created/Joined
    UserB->>Server: Join Same Room
    Server->>UserA: User Joined Notification
    Server->>UserB: User Joined Notification
    
    UserA->>Server: WebRTC Offer
    Server->>UserB: Forward Offer
    UserB->>Server: WebRTC Answer
    Server->>UserA: Forward Answer
    
    Note over UserA,UserB: Direct P2P Connection Established
    Note over UserA,UserB: All media encrypted end-to-end
```

---

## Installation & Setup

### Prerequisites
- Node.js 18+ 
- npm or yarn

### Quick Start

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/Vok.Chat.git
cd Vok.Chat
```

2. **Install frontend dependencies**
```bash
npm install
```

3. **Install backend dependencies**
```bash
cd backend
npm install
cd ..
```

4. **Set up environment variables**
```bash
# Create .env file in backend directory
echo "PORT=5001" > backend/.env
```

5. **Start the development servers**

**Terminal 1 - Backend:**
```bash
cd backend
npm start
```

**Terminal 2 - Frontend:**
```bash
npm run dev
```

6. **Open your browser**
Navigate to `http://localhost:5173`

---

## Usage Guide

### Starting a Call
1. Click **"Start a Call"** button
2. System generates a unique URL (e.g., `vok-chat.app/ABC123`)
3. Use **"Copy Link"** or **"Share"** buttons to share with others
4. Wait for them to join via the link

### Joining a Call
1. **Option A**: Click the shared link directly
2. **Option B**: Enter the session code manually
3. Grant camera/microphone permissions
4. Automatically joins the room

### During the Call
- **Mute/Unmute** - Click microphone icon
- **Pause/Resume Video** - Click video icon  
- **Rotate Camera** - Click rotate icon (mobile devices)
- **End Call** - Click red phone icon
- **Copy Link** - Click copy icon to share room URL
- **Share** - Click share icon for native sharing

### Smart URL Sharing
- **Copy Link**: Copies full URL to clipboard
- **Share Button**: Opens native share dialog (WhatsApp, Email, etc.)
- **Direct Access**: Anyone with the link can join instantly
- **No Typing Required**: Just click the link to join

---

## Project Structure

```
VokChat/
├── src/                    # Frontend source code
│   ├── App.jsx               # Main application with routing
│   ├── LandingPage.jsx       # Landing page component
│   ├── VideoCall.jsx         # Video call component
│   ├── main.jsx              # React entry point
│   ├── turnConfig.js         # WebRTC configuration
│   └── index.css             # Global styles & fonts
├── backend/               # Backend server
│   ├── index.js              # Express + Socket.IO server
│   └── package.json          # Backend dependencies
├── public/                # Static assets
│   └── fonts/            # Custom typography
├── package.json              # Frontend dependencies
├── tailwind.config.js        # Tailwind configuration
└── vite.config.js           # Vite build configuration
```

---

## Development

### Available Scripts

**Frontend:**
```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run preview  # Preview production build
npm run lint     # Run ESLint
```

**Backend:**
```bash
cd backend
npm start        # Start production server
```

### Key Components

#### Frontend Architecture
```mermaid
graph LR
    A[App.jsx] --> B[React Router]
    A --> C[WebRTC Manager]
    A --> D[Socket.IO Client]
    A --> E[UI Components]
    
    B --> F[LandingPage]
    B --> G[VideoCall]
    
    C --> H[Peer Connection]
    C --> I[Media Streams]
    C --> J[ICE Handling]
    
    D --> K[Signaling]
    D --> L[Room Management]
    
    E --> M[Video Display]
    E --> N[Controls]
    E --> O[Share UI]
```

#### Backend Architecture
```mermaid
graph LR
    A[Express Server] --> B[Socket.IO Server]
    B --> C[Room Manager]
    B --> D[Signaling Handler]
    
    C --> E[Session Storage]
    C --> F[User Tracking]
    
    D --> G[Offer/Answer Relay]
    D --> H[ICE Candidate Relay]
```

---

## Deployment

### Frontend (Vercel/Netlify)
```bash
npm run build
# Deploy dist/ folder
```

### Backend (Render)
```bash
# Set environment variables
PORT=5001
NODE_ENV=production

# Deploy backend/ folder
```

### Environment Variables
```env
# Backend (.env)
PORT=5001
NODE_ENV=production
```



## Acknowledgments

- **WebRTC** - For peer-to-peer communication
- **Socket.IO** - For real-time signaling
- **React Team** - For the amazing framework
- **Tailwind CSS** - For the utility-first CSS
- **Vite** - For the lightning-fast build tool

