# UniMentorAI Architecture

## System Overview

UniMentorAI follows a modern, scalable architecture designed for reliability, performance, and security. The system is built on cloud-native principles with AI integration at its core.

## High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    User Interface Layer                      │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │  Web App │  │ Mobile   │  │ PWA      │  │ Desktop  │  │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘  │
└─────────────────────────────────────────────────────────────┘
                            │
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                  Application Programming Interface           │
│  ┌────────────────────────────────────────────────────────┐ │
│  │  RESTful API Gateway                                    │ │
│  │  • Authentication & Authorization                        │ │
│  │  • Request Routing                                      │ │
│  │  • Rate Limiting                                        │ │
│  │  • Load Balancing                                       │ │
│  └────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
                            │
          ┌─────────────────┴─────────────────┐
          ↓                                   ↓
┌─────────────────────┐           ┌─────────────────────┐
│   Business Logic    │           │    AI Layer         │
│     Services        │           │                     │
│  ┌───────────────┐ │           │  ┌───────────────┐  │
│  │ Profile Mgmt  │ │           │  │ OpenAI API   │  │
│  │ University DB │ │           │  │ GPT-3.5-turbo │  │
│  │ Matching Algo│ │           │  │ Integration  │  │
│  │ Scoring Eng.  │ │           │  └───────────────┘  │
│  │ Timeline Gen. │ │           │  ┌───────────────┐  │
│  └───────────────┘ │           │  │ Custom Models │  │
│  ┌───────────────┐ │           │  │ • Matching    │  │
│  │ Essay Analysis│ │           │  │ • Prediction  │  │
│  │ Scholarship DB│ │          │  │ • Scoring     │  │
│  └───────────────┘ │           │  └───────────────┘  │
└─────────────────────┘           └─────────────────────┘
          │                                   │
          └──────────────┬────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────────┐
│                     Data Layer                               │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐       │
│  │   MySQL DB   │  │   Redis Cache│  │  S3 Storage  │       │
│  │ • User Data  │  │ • Sessions   │  │ • Files     │       │
│  │ • Univ. Info │  │ • Temp Data  │  │ • Uploads   │       │
│  │ • Profiles   │  │ • Rate Limits│  │             │       │
│  └──────────────┘  └──────────────┘  └──────────────┘       │
└─────────────────────────────────────────────────────────────┘
```

## Component Details

### 1. User Interface (UI) Layer

**Technology**: HTML5, CSS3, JavaScript (Vanilla + Modern ES6+)

**Components**:
- **Responsive Web Application**: Desktop and tablet optimized
- **Progressive Web App (PWA)**: Offline support, installable
- **Mobile-Responsive Design**: Touch-optimized interfaces

**Key Features**:
- Asynchronous data loading
- Real-time AI feedback
- Smooth transitions and animations
- Accessibility (WCAG 2.1 AA compliant)

### 2. Application Programming Interface (API) Layer

**Technology**: RESTful API with Node.js/Express

**Endpoints**:
```
POST /api/v1/match          - Generate university matches
POST /api/v1/predict        - Calculate admission probability
POST /api/v1/essay/analyze  - Analyze essay
POST /api/v1/scholarship    - Find scholarships
GET  /api/v1/universities   - List universities
GET  /api/v1/rankings       - Get rankings
```

**Responsibilities**:
- Request validation
- Authentication & authorization
- Rate limiting
- Error handling
- Response formatting

### 3. AI Layer

**Primary AI Provider**: OpenAI GPT-3.5-turbo

**Integration Points**:
- University recommendation generation
- Essay analysis and feedback
- Profile scoring algorithms
- Natural language processing for user queries

**Custom Algorithms**:
- **Matching Engine**: Multi-factor scoring system
- **Prediction Model**: Regression-based probability estimation
- **Profile Scorer**: Weighted factor analysis

**AI Workflow**:
1. User input received
2. Context assembled (profile, preferences, history)
3. OpenAI API called with tailored prompt
4. Response parsed and validated
5. Fallback logic if API fails
6. Results formatted for UI

### 4. Business Logic Services

**Profile Management**:
- Store and update user academic profiles
- Track application progress
- Maintain user preferences

**University Database**:
- 1,500+ university profiles
- Requirements, rankings, programs
- Real-time updates (quarterly refresh)

**Matching Algorithm**:
```
Score = (Academic × 0.35) + 
        (Test Scores × 0.25) + 
        (Activities × 0.20) + 
        (Preferences × 0.20)

Match = Score weighted by university competitiveness
```

**Timeline Generator**:
- Calculate optimal task sequencing
- Account for multiple deadlines
- Buffer time for revisions
- Test retake recommendations

### 5. Data Layer

**Database**: MySQL (Structured Data)
- User accounts and profiles
- University information
- Application tracking
- Usage analytics

**Cache**: Redis (Performance)
- Session management
- Frequently accessed data
- Rate limiting counters
- Temporary AI results

**Storage**: S3-Compatible (Files)
- User-uploaded documents
- Essay drafts
- Generated reports

## Data Flow

### Example: University Matching Request

```
1. User → UI: Submits profile information
   ↓
2. UI → API: POST /api/v1/match with JSON payload
   ↓
3. API Validates: Profile completeness, format
   ↓
4. API → Business Logic: Generate match request
   ↓
5. Business Logic → Database: Fetch university data
   ↓
6. Business Logic → AI Layer: Send profile + universities to GPT
   ↓
7. AI Layer → OpenAI: API call with customized prompt
   ↓
8. OpenAI → AI Layer: Recommendation response
   ↓
9. AI Layer → Business Logic: Formatted recommendations
   ↓
10. Business Logic → API: Final recommendations
   ↓
11. API → UI: JSON response
   ↓
12. UI → User: Display recommendations with reasoning
```

## Security Architecture

**Authentication**:
- JWT tokens for sessions
- Secure password hashing (bcrypt)
- Multi-factor authentication (planned)

**Data Protection**:
- HTTPS/TLS for all communications
- Encryption at rest for sensitive data
- GDPR compliant data handling
- Regular security audits

**Privacy**:
- Minimal data collection
- User control over data
- Right to deletion
- No unauthorized sharing

## Scalability Design

**Horizontal Scaling**:
- Stateless API design
- Load balanced servers
- CDN for static assets

**Performance Optimization**:
- Redis caching layer
- Database query optimization
- Lazy loading in UI
- Async processing for AI calls

**Reliability**:
- Error handling at every layer
- Automatic failover
- Graceful degradation
- Monitoring and alerting

## Integration Principles

**Separation of Concerns**:
- UI handles presentation
- API handles coordination
- Business logic handles rules
- AI layer handles intelligence
- Data layer handles persistence

**Abstraction Layers**:
- UI doesn't know about AI implementation
- API doesn't know about database structure
- Services are independently testable

**Flexibility**:
- Easy to swap AI providers
- Database-agnostic design
- Pluggable business logic
- Configurable routing

## Future Architecture Enhancements

**Planned Improvements**:
- Microservices migration for better scaling
- GraphQL API for flexible queries
- Real-time features with WebSocket
- Mobile native apps (React Native)
- Advanced analytics dashboard

**AI Enhancements**:
- Fine-tuned models on proprietary data
- Multi-model ensemble predictions
- Real-time learning from outcomes
- Personalized AI behavior per user

## Monitoring & Observability

**Metrics Tracked**:
- API response times
- AI API latency
- Error rates
- User engagement
- Prediction accuracy (longitudinal)

**Tools**:
- Application performance monitoring
- Error tracking and alerting
- User analytics (GDPR compliant)
- Cost tracking for AI API usage

## Technology Stack Summary

**Frontend**: HTML5, CSS3, JavaScript, PWA APIs  
**Backend**: Node.js, Express.js  
**Database**: MySQL  
**Cache**: Redis  
**Storage**: S3-compatible  
**AI**: OpenAI GPT-3.5-turbo  
**Hosting**: Cloud-based (multi-region)  
**Security**: HTTPS, JWT, encryption  
**Monitoring**: Application and error tracking

---

**Design Philosophy**: Simplicity, reliability, and AI-first functionality guide every architectural decision in UniMentorAI.

