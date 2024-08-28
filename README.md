# Career Karma Voice Call SDK

Voice Calls for Career Karma API in your web application

## Installation

To install the Career Karma Voice Call SDK via npm, run the following command:

```shell
npm install @career-karma/voice-call
```

## Usage

Import the Career Karma Web SDK into your project:

```typescript
import VoiceCall from "@career-karma/voice-call";
```

Create a new instance of the Career Karma Voice Call SDK using your public key or token:

```typescript
const voiceCall = new VoiceCall({
  publicKey: "YOUR PUBLIC KEY",
  // OR
  token: "TOKEN GENERATED BY API",
});
```

### Voice call start

Initiate the call with a companion:

```typescript
voiceCall.startCall({
  companionId: string;            // Required
  userId: string;                 // Optional
  variables: Record<string, any>; // Optional
});
```

After initiating the call, microphone permissions will be requested. Once granted, the client will be able to interact with their companion.

### Voice call stop

To stop the call with a companion, use the following method:

```typescript
voiceCall.stop();
```

### Microphone mute

To mute\unmute the microphone use the following method:

```typescript
// Mute microphone
voiceCall.mute();
// Unmute microphone
voiceCall.unmute();
// Check if the microphone is currently muted
voiceCall.isMuted();
```

## Events

The Career Karma Voice Call SDK provides a set of events that you can listen to:

```typescript
voiceCall.on('speech-start', () => {
  console.log('Speech has started');
});

voiceCall.on('speech-end', () => {
  console.log('Speech has ended');
});

voiceCall.on('call-start', () => {
  console.log('Call has started');
});

voiceCall.on('call-end', () => {
  console.log('Call has stopped');
});

voiceCall.on('volume-level', (volume) => {
  console.log(`Companion volume level: ${volume}`);
});

voiceCall.on('transcript', (message) => {
  console.log(`${message.role === "user" ? "User" : "Companion"} transcript:`);
  console.log(message.transcript);
});

voiceCall.on('function-call', (function) => {
  console.log(`Function ${function.name} was called with arguments ${function.arguments}`);
});

voiceCall.on('error', (e) => {
  console.error(e);
});
```

Listening to these events will help you track the call progress and user interaction with the companion.
