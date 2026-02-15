# Startup Saathi - Requirements Document

**Project Name:** Startup Saathi (स्टार्टअप साथी)  
**Version:** 1.0  
**Date:** February 2026  
**Hackathon:** AI for Bharat AWS Hackathon  

## 1. Executive Summary

### 1.1 Vision
Democratize entrepreneurship in India by making world-class startup guidance accessible to everyone - from tech founders in Bangalore to vegetable sellers in rural Bihar - in their own language, through voice or text.

### 1.2 Product Overview
Startup Saathi is an AI-powered business guidance platform that helps ANY Indian entrepreneur start and grow their business by providing personalized recommendations for:
- Product/service ideas based on skills and market analysis
- Government scheme matching (exact schemes they qualify for)
- Legal compliance roadmap (step-by-step guidance)
- Marketing strategies tailored to budget and location
- Funding opportunities (VCs, banks, government grants)
- Export/import business guidance
- Voice-first interface in 12+ Indian languages

### 1.3 Target Users

**Primary Persona: First-Time Entrepreneur**
- **Demographics:** 25-45 years, Tier 2/3 cities, limited English proficiency
- **Characteristics:** 
  - Monthly income: ₹15K-₹50K
  - Education: 10th-12th pass or graduate
  - Digital literacy: Basic smartphone usage
  - Language preference: Regional language (68% of target market)
- **Pain Points:**
  - Information overload (don't know where to start)
  - Language barriers (95% resources in English)
  - Lack of affordable guidance (consultants cost ₹50K-5L)
  - Fear of legal non-compliance
- **Goals:**
  - Start a business with ₹50K-₹5L budget
  - Access government funding
  - Understand legal requirements
  - Get customers quickly

**Secondary Personas:**
- Students (E-cell members, aspiring entrepreneurs)
- Professionals (side hustle, career transition)
- MSME owners (scaling existing business)
- Returning NRIs (India market entry)

**Scale:** MVP target of 5,000-10,000 users

### 1.4 Success Metrics & KPIs

**North Star Metric:** Number of entrepreneurs who successfully launch their business (tracked via scheme applications + revenue generation)

**Primary KPIs (MVP - Month 3):**

| Metric | Target | Baseline | Measurement Method |
|--------|--------|----------|-------------------|
| Onboarding completion rate | 70% | 0% | (Users completing profile / Total signups) × 100 |
| Scheme applications submitted | 50+ | 0 | Count from database |
| User satisfaction (NPS) | 50+ | N/A | Post-analysis survey |
| Platform uptime | 99.5% | N/A | CloudWatch metrics |
| Voice transcription accuracy | 85%+ | N/A | Manual review of 100 samples |
| API response time (p95) | <500ms | N/A | CloudWatch metrics |
| Critical bugs | <5 | N/A | Bug tracking system |

**Secondary KPIs (Public Launch - Month 6):**

| Metric | Target | Baseline | Measurement Method |
|--------|--------|----------|-------------------|
| Total active users | 5,000-10,000 | 100 | Monthly active users (MAU) |
| Successful scheme applications | 500+ | 50 | User-reported + verified |
| Funding accessed via platform | ₹20 Cr+ | ₹0 | User surveys + scheme data |
| Referral rate | 30%+ | 0% | (Referred users / Total users) × 100 |
| User retention (30-day) | 50%+ | N/A | Users returning within 30 days |
| Average session duration | 8+ min | N/A | Analytics tracking |
| Incubator partnerships | 2-3 | 0 | Signed MOUs |
| Media mentions | 2+ articles | 0 | PR tracking |

**Engagement Metrics:**

| Metric | Target | Measurement |
|--------|--------|-------------|
| Voice usage rate | 40%+ | % of users using voice feature |
| AI chat interactions | 3+ per user | Average messages per user |
| Scheme detail views | 5+ per user | Page views per user |
| PDF downloads | 60%+ | % of users downloading checklists |
| Notification open rate | 25%+ | Opened / Sent |

**Business Impact Metrics:**

| Metric | Target | Timeline |
|--------|--------|----------|
| Cost per acquisition (CPA) | <₹100 | Month 6 |
| Customer lifetime value (LTV) | ₹500+ | Month 12 |
| LTV:CAC ratio | 5:1 | Month 12 |
| Revenue (premium tier) | ₹5L+ | Month 12 |

**Quality Metrics:**

| Metric | Target | Measurement |
|--------|--------|-------------|
| AI recommendation accuracy | 80%+ | User feedback (thumbs up/down) |
| Scheme matching relevance | 85%+ | User ratings (1-5 stars) |
| Legal checklist completeness | 95%+ | Expert review |
| Voice transcription error rate | <15% | Manual review |

### 1.5 Business Constraints

**Budget Constraints:**
- MVP development: ₹0 (self-funded)
- AWS infrastructure: $292.68/month (covered by AWS Activate credits)
- Third-party APIs: $104/month (data collection)
- Total monthly burn: ~$400/month for first 6 months

**Timeline Constraints:**
- MVP launch: 3 months from kickoff
- Public launch: 6 months from kickoff
- Break-even: 18 months from kickoff

**Resource Constraints:**
- Team size: 1-2 developers (MVP)
- No dedicated QA (automated testing only)
- No dedicated designer (use Tailwind UI components)

**Regulatory Constraints:**
- DPDPA compliance mandatory (data protection)
- No financial advice (educational content only)
- No direct VC introductions without proper licensing

## 2. User Stories & Acceptance Criteria

### 2.1 User Story 1: Multilingual Voice Onboarding
**As a** non-English speaking entrepreneur  
**I want to** describe my business idea by speaking in my native language  
**So that** I can get personalized guidance without language barriers

#### Acceptance Criteria:

1.1. System shall support voice input in 12 Indian languages (Hindi, Tamil, Telugu, Bengali, Marathi, Gujarati, Kannada, Malayalam, Punjabi, Odia, Assamese, English)
1.2. Voice recognition accuracy shall be ≥85% for Indian accents
1.3. System shall detect language automatically with ≥95% confidence
1.4. User shall be able to switch between voice and text input at any time
1.5. System shall provide audio responses in the same language as user input
1.6. Voice processing latency shall be <3 seconds for transcription
1.7. System shall handle code-mixing (Hinglish) with ≥80% accuracy
1.8. User shall receive confirmation of transcribed text before proceeding
1.9. System shall work on 2G/3G networks with graceful degradation
1.10. Audio files shall be auto-deleted after 7 days for privacy

### 2.2 User Story 2: AI-Powered Product Recommendations
**As an** aspiring entrepreneur with skills but no clear business idea  
**I want to** receive personalized product/service recommendations based on my profile  
**So that** I can choose a viable business with high success probability

#### Acceptance Criteria:
2.1. System shall collect user profile: skills, location, budget, time availability, education
2.2. System shall analyze market demand for ≥5 potential products/services
2.3. System shall provide top 3 ranked recommendations with match scores (0-100)
2.4. Each recommendation shall include:
     - Market demand rating (1-5 stars)
     - Competition assessment (Low/Medium/High)
     - Profit margin estimate (%)
     - Startup cost breakdown
     - Year 1 revenue potential
     - Success probability (%)
     - Key success factors
     - Common failure reasons
2.5. System shall complete analysis within 2-3 minutes
2.6. Recommendations shall be based on ≥50 factors including location-specific data
2.7. System shall provide growth path projections (Month 1-12)
2.8. User shall be able to request alternative recommendations
2.9. System shall explain reasoning for each recommendation
2.10. Recommendations shall align with available government schemes

### 2.3 User Story 3: Government Scheme Matching
**As an** entrepreneur eligible for government funding  
**I want to** discover exact schemes I qualify for with application guidance  
**So that** I don't miss funding opportunities due to lack of awareness

#### Acceptance Criteria:

3.1. System shall maintain database of ≥500 government schemes (central + state)
3.2. System shall filter schemes based on: industry, stage, location, turnover, entity type, gender, category (SC/ST/OBC)
3.3. System shall provide top 5 schemes ranked by relevance score (0-100)
3.4. Each scheme shall include:
     - Benefits (grant amount, training, subsidies)
     - Complete eligibility criteria
     - Required documents checklist
     - Step-by-step application process
     - Timeline and deadlines
     - Success probability estimate
     - Insider tips to increase approval chances
     - Common mistakes to avoid
3.5. System shall provide direct links to application portals
3.6. System shall offer AI-generated DPR (Detailed Project Report) templates
3.7. System shall send deadline reminders via SMS/email/WhatsApp
3.8. Scheme data shall be updated weekly via automated scraping
3.9. System shall track user's scheme applications and status
3.10. System shall provide video tutorials in user's preferred language

### 2.4 User Story 4: Legal Compliance Roadmap
**As a** first-time entrepreneur unfamiliar with legal requirements  
**I want to** receive a personalized, prioritized legal checklist  
**So that** I can ensure compliance without expensive consultants

#### Acceptance Criteria:
4.1. System shall generate dynamic checklist based on: business type, location, entity type, revenue stage
4.2. Checklist shall be prioritized: Critical (do now), High (before launch), Medium (when earning), Low (future)
4.3. Each item shall include:
     - What it is (simple explanation)
     - Why it's needed
     - Cost estimate
     - Time required
     - Step-by-step application process
     - Penalty for non-compliance
     - Direct links to portals
4.4. System shall provide timeline view (Week 1-2, Week 3-4, Month 2-3, Future)
4.5. System shall calculate total immediate cost
4.6. System shall offer downloadable PDF checklist
4.7. System shall set reminders for annual compliance (GST, Income Tax)
4.8. System shall provide CA/lawyer referral options
4.9. Checklist shall update dynamically as business grows (e.g., GST when turnover >₹20L)
4.10. System shall support ≥20 business types and ≥10 entity types

### 2.5 User Story 5: Marketing Strategy Generator
**As an** entrepreneur with limited marketing budget  
**I want to** receive a customized, actionable marketing plan  
**So that** I can acquire customers cost-effectively

#### Acceptance Criteria:

5.1. System shall accept inputs: business type, budget (₹5K-₹5L), timeline (3/6/12 months), target customers, location
5.2. System shall provide month-by-month marketing plan with specific tactics
5.3. Each tactic shall include:
     - Detailed execution steps
     - Cost breakdown
     - Expected results (reach, conversions)
     - ROI estimate
5.4. Plan shall include mix of: hyperlocal, digital, partnerships, content, referral strategies
5.5. System shall provide budget allocation across channels
5.6. System shall include free/low-cost tactics (WhatsApp groups, Google My Business, sampling)
5.7. System shall provide templates (flyers, social media posts, email scripts)
5.8. System shall calculate expected customer acquisition metrics
5.9. System shall provide tracking metrics dashboard
5.10. Plan shall be downloadable as PDF with content calendar

### 2.6 User Story 6: Export/Import Business Guidance
**As an** entrepreneur wanting to export products  
**I want to** step-by-step guidance in my language  
**So that** I can access global markets without expensive consultants

#### Acceptance Criteria:

6.1. System shall provide 6-step export roadmap: License, Find Buyers, Pricing, Documentation, Customs, Payment
6.2. System shall recommend target countries based on product type
6.3. System shall provide country-specific guides for ≥20 countries
6.4. System shall offer downloadable document templates (Invoice, Packing List, Certificate of Origin)
6.5. System shall auto-detect HS Code from product photo/description
6.6. System shall calculate duties and taxes for target countries
6.7. System shall provide shipping partner comparisons (FedEx, DHL, India Post)
6.8. System shall estimate total cost and timeline for first export
6.9. System shall provide video tutorials in regional languages
6.10. Premium tier: Step-by-step documentation assistance

### 2.7 User Story 7: Image Upload & Analysis
**As an** entrepreneur with a product prototype  
**I want to** upload photos for AI analysis and feedback  
**So that** I can improve my product presentation

#### Acceptance Criteria:
7.1. System shall accept image uploads (JPEG, PNG, max 10MB)
7.2. System shall analyze product photos for: quality, packaging, branding, lighting
7.3. System shall provide actionable improvement suggestions
7.4. System shall compare with competitor products
7.5. System shall suggest pricing based on visual analysis
7.6. System shall extract text from scanned documents (OCR)
7.7. System shall convert handwritten notes to digital text
7.8. System shall support document uploads (legal docs, certificates)
7.9. System shall check documents for errors/completeness
7.10. Images shall be stored securely and deleted after 30 days

### 2.8 User Story 8: Smart Notifications
**As a** busy entrepreneur  
**I want to** receive timely, relevant notifications  
**So that** I never miss critical deadlines or opportunities

#### Acceptance Criteria:
8.1. System shall send notifications via: SMS, WhatsApp, Email, In-app, Voice call (optional)
8.2. Notification categories: Deadline Alerts (critical), New Opportunities (timely), Action Items (helpful), Learning Content (optional), Market Alerts (premium)
8.3. System shall filter notifications based on user profile (no irrelevant content)
8.4. Deadline alerts shall be sent: 7 days before, 3 days before, 1 day before
8.5. User shall control: categories, frequency, preferred time, language
8.6. System shall limit non-critical notifications to max 2 per week
8.7. One-click unsubscribe for any category
8.8. System shall use AI to determine notification relevance score (>80% to send)
8.9. Critical notifications (scheme deadlines) shall be sent via multiple channels
8.10. System shall track notification open rates and optimize delivery

### 2.9 User Story 9: Conversational AI Dashboard
**As an** entrepreneur needing ongoing guidance  
**I want to** ask follow-up questions to AI anytime  
**So that** I can get clarifications and support 24/7

#### Acceptance Criteria:

9.1. System shall provide persistent chat interface on dashboard
9.2. AI shall maintain conversation context across sessions
9.3. AI shall answer questions about: schemes, legal, marketing, funding, competitors
9.4. Free tier: 5 questions/month; Premium tier: Unlimited
9.5. Response time shall be <5 seconds for text, <10 seconds for voice
9.6. AI shall provide sources/links for factual claims
9.7. AI shall escalate complex queries to human experts (premium tier)
9.8. System shall support multi-turn conversations (follow-ups)
9.9. Chat history shall be searchable and exportable
9.10. AI shall proactively suggest next steps based on user's progress

## 3. Non-Functional Requirements

### 3.1 Performance
- Page load time: <2 seconds on 3G
- API response time: <500ms (p95)
- Voice transcription: <3 seconds
- AI analysis completion: <3 minutes
- System uptime: 99.5%
- Concurrent users: Support 1,000 simultaneous users (MVP)

### 3.2 Scalability
- Horizontal scaling for web servers
- Database read replicas for high traffic
- CDN for static assets
- Auto-scaling based on load
- Support growth from 5K to 100K users

### 3.3 Security
- HTTPS for all communications
- JWT-based authentication
- Password hashing (bcrypt)
- Rate limiting (100 requests/min per user)
- SQL injection prevention
- XSS protection
- GDPR/DPDPA compliance
- PII data encryption at rest
- Audio files auto-deletion (7 days)
- Regular security audits

### 3.4 Accessibility
- WCAG 2.1 Level AA compliance
- Screen reader support
- High contrast mode
- Large text option (for elderly)
- Voice-only mode (no typing required)
- Works on ₹5,000 smartphones
- Offline mode for cached data
- Low data consumption (2-5 MB per session)

### 3.5 Localization
- 12 Indian languages supported
- Cultural adaptation (not just translation)
- Right-to-left text support (if needed)
- Local currency (₹)
- Date/time formats (DD/MM/YYYY)
- Regional examples and case studies

### 3.6 Reliability
- Automated backups (daily)
- Disaster recovery plan (RPO: 24 hours, RTO: 4 hours)
- Error logging and monitoring
- Graceful degradation (if AI service down, show cached results)
- Retry logic for failed API calls

### 3.7 Maintainability
- Modular architecture
- Comprehensive API documentation
- Code comments and README
- Automated testing (unit, integration)
- CI/CD pipeline
- Version control (Git)

## 4. Technical Constraints

### 4.1 Technology Stack

**Frontend:**
- Framework: Next.js 14.x (App Router)
- Language: TypeScript 5.x
- Styling: Tailwind CSS 3.x
- State Management: React Context + Zustand 4.x
- Forms: React Hook Form 7.x + Zod 3.x validation
- HTTP Client: Axios 1.x with retry logic
- PWA: next-pwa 5.x
- Testing: Jest 29.x, React Testing Library 14.x

**Backend:**
- Runtime: Node.js 20.x LTS (Lambda), Python 3.12 (Lambda)
- API: Next.js API Routes + AWS API Gateway
- Database: PostgreSQL 15.4 (Amazon RDS)
- Cache: Redis 7.x (Amazon ElastiCache)
- Vector DB: OpenSearch 2.x (Amazon OpenSearch Service)
- ORM: Prisma 5.x (Node.js), SQLAlchemy 2.x (Python)

**Cloud Infrastructure:**
- Provider: AWS (us-east-1 primary region)
- Compute: AWS Lambda + Amazon ECS Fargate / EC2 t3.small
- Storage: Amazon S3 (Standard + Intelligent-Tiering)
- CDN: Amazon CloudFront
- DNS: Amazon Route 53

**AI/ML Services:**
- Primary: Amazon Bedrock (Claude 3.5 Sonnet - anthropic.claude-3-5-sonnet-20241022-v2:0)
- Backup: OpenAI GPT-4 Turbo, Anthropic Claude 3.5 API
- Voice-to-Text: Amazon Transcribe (Standard, 12 Indian languages)
- Text-to-Speech: Amazon Polly (Neural voices)
- Image Analysis: Amazon Rekognition
- Embeddings: Amazon Titan Embeddings G1 - Text

**Authentication & Security:**
- Auth: AWS Cognito (50K MAU free tier)
- Secrets: AWS Secrets Manager
- WAF: AWS WAF (SQL injection, XSS protection)
- Encryption: AES-256 (at rest), TLS 1.3 (in transit)

**Monitoring & Observability:**
- Logs: AWS CloudWatch Logs
- Metrics: AWS CloudWatch Metrics
- Tracing: AWS X-Ray
- Error Tracking: Sentry (free tier)
- Uptime Monitoring: UptimeRobot (free tier)

**CI/CD:**
- Version Control: Git (GitHub)
- CI/CD: GitHub Actions / AWS CodePipeline
- Container Registry: Amazon ECR
- IaC: Terraform 1.5+

### 4.2 Third-Party Integrations

**Required Integrations:**

| Service | Purpose | Cost | SLA | Fallback |
|---------|---------|------|-----|----------|
| Razorpay | Payment processing | 2% per transaction | 99.9% | Manual payment |
| AWS SNS | SMS notifications | $0.00645/SMS (India) | 99.9% | Email fallback |
| Amazon SES | Email notifications | $0.10/1000 emails | 99.9% | SMS fallback |
| Twilio | WhatsApp notifications | $0.005/message | 99.95% | SMS fallback |
| Google Maps API | Location services | $5/1000 requests | 99.9% | Manual entry |
| SerpAPI | Market research | $50/month (5K searches) | 99% | Cached data |

**Optional Integrations (Post-MVP):**
- Crunchbase API: VC database ($29/month)
- Statista API: Market data ($49/month)
- FedEx/DHL APIs: Shipping rates (free)

### 4.3 Data Requirements

**Data Sources & Collection Strategy:**

| Dataset | Size | Source | Collection Method | Update Frequency | Storage |
|---------|------|--------|-------------------|------------------|---------|
| Government schemes | 500+ | Startup India, Ministry websites | Automated scraping + Manual curation | Weekly | RDS + OpenSearch |
| VC database | 1,000+ | Crunchbase, VCCEdge, Public sources | API + Manual curation | Monthly | RDS |
| Legal rules | 20+ business types | Government portals, Legal databases | Rule engine + Expert input | Quarterly | RDS |
| Market data | 50+ sectors | IBEF, Statista, SerpAPI | API + Web scraping | Quarterly | RDS + Cache |
| Export guides | 100+ countries | DGFT, Trade.gov, Shipping APIs | Manual + API | Quarterly | RDS + S3 |
| Custom vocabulary | 500+ terms | Manual curation, User feedback | Crowdsourcing | Monthly | Transcribe |

**Data Quality Requirements:**
- Accuracy: 95%+ (verified by manual review)
- Completeness: 100% for required fields
- Freshness: <7 days for scheme data, <30 days for other data
- Consistency: No duplicate entries, normalized formats

**Data Governance:**
- Ownership: Government data (public domain), Licensed data (Crunchbase, Statista)
- Retention: Schemes (all versions), User data (delete on request), Analytics (aggregate only)
- Privacy: No PII in datasets, DPDPA compliance, Anonymize user contributions

### 4.4 API Specifications

**REST API Endpoints:**

```yaml
Base URL: https://api.startupsaathi.in/v1

Authentication:
  Type: JWT Bearer Token
  Header: Authorization: Bearer <token>
  Expiry: 1 hour (access token), 7 days (refresh token)

Rate Limiting:
  Free Tier: 100 requests/minute
  Premium Tier: 1000 requests/minute
  Burst: 2x rate limit for 10 seconds

Endpoints:

# Authentication
POST /auth/register
  Request: { email, password, phone, language }
  Response: { user_id, access_token, refresh_token }
  Rate Limit: 5 requests/hour per IP

POST /auth/login
  Request: { email, password }
  Response: { user_id, access_token, refresh_token }
  Rate Limit: 10 requests/hour per IP

POST /auth/refresh
  Request: { refresh_token }
  Response: { access_token }
  Rate Limit: 20 requests/hour

# Voice Processing
POST /voice/transcribe
  Request: { audio_file (multipart), language? }
  Response: { text, language_detected, confidence }
  Max File Size: 10 MB
  Supported Formats: WAV, MP3, M4A
  Rate Limit: 20 requests/hour (free), unlimited (premium)

POST /voice/synthesize
  Request: { text, language, voice_id? }
  Response: { audio_url, duration_seconds }
  Rate Limit: 50 requests/hour (free), unlimited (premium)

# AI Analysis
POST /analysis/product-recommendations
  Request: { profile: { skills, location, budget, time, education } }
  Response: { recommendations: [{ name, score, details }] }
  Processing Time: 2-3 minutes
  Rate Limit: 5 requests/day (free), unlimited (premium)

POST /analysis/scheme-matching
  Request: { profile: { business_type, location, stage, entity_type } }
  Response: { schemes: [{ id, name, relevance_score, details }] }
  Processing Time: 30 seconds
  Rate Limit: 10 requests/day (free), unlimited (premium)

POST /analysis/legal-checklist
  Request: { business_type, location, entity_type, revenue_stage }
  Response: { checklist: [{ id, name, priority, details }] }
  Processing Time: 10 seconds
  Rate Limit: 10 requests/day (free), unlimited (premium)

POST /analysis/marketing-plan
  Request: { business_type, budget, timeline, target_customers, location }
  Response: { plan: { monthly_tactics, budget_allocation, templates } }
  Processing Time: 1-2 minutes
  Rate Limit: 5 requests/day (free), unlimited (premium)

# Conversational AI
POST /chat/message
  Request: { message, conversation_id?, language? }
  Response: { reply, conversation_id, sources }
  Rate Limit: 5 messages/month (free), unlimited (premium)

GET /chat/history
  Request: { conversation_id }
  Response: { messages: [{ role, content, timestamp }] }
  Rate Limit: 100 requests/hour

# Schemes
GET /schemes/list
  Request: { filters: { industry?, location?, stage? }, page, limit }
  Response: { schemes: [...], total, page, limit }
  Rate Limit: 100 requests/hour

GET /schemes/{id}
  Request: { id }
  Response: { scheme: { id, name, details, eligibility, benefits } }
  Rate Limit: 100 requests/hour

# Notifications
POST /notifications/subscribe
  Request: { channels: [sms, email, whatsapp], preferences }
  Response: { subscription_id }
  Rate Limit: 10 requests/hour

GET /notifications/preferences
  Request: { user_id }
  Response: { preferences: { categories, frequency, time } }
  Rate Limit: 50 requests/hour

# Image Analysis
POST /images/analyze
  Request: { image_file (multipart), analysis_type }
  Response: { insights: { quality, suggestions, pricing } }
  Max File Size: 10 MB
  Supported Formats: JPEG, PNG
  Rate Limit: 10 requests/day (free), 100 (premium)

Error Responses:
  400: Bad Request (invalid input)
  401: Unauthorized (invalid/expired token)
  403: Forbidden (insufficient permissions)
  404: Not Found (resource doesn't exist)
  429: Too Many Requests (rate limit exceeded)
  500: Internal Server Error
  503: Service Unavailable (maintenance)

Error Format:
  {
    "error": {
      "code": "RATE_LIMIT_EXCEEDED",
      "message": "You have exceeded the rate limit",
      "details": "Try again in 60 seconds",
      "retry_after": 60
    }
  }
```

### 4.5 Compliance & Regulatory Requirements

**Data Protection (DPDPA 2023):**
- Explicit user consent for data collection
- Right to access personal data
- Right to delete personal data
- Right to correct inaccurate data
- Data breach notification within 72 hours
- Data localization (store in India)
- Appoint Data Protection Officer (DPO)

**IT Act 2000:**
- Digital signatures for legal documents
- Cybersecurity measures
- Data retention policies
- Incident response plan

**SEBI Guidelines (Investment Content):**
- Not applicable (no investment/stock recommendations in MVP)
- Future consideration if feature is added

**FSSAI (Food Business Examples):**
- Accurate food safety information
- No misleading claims
- Proper licensing guidance

**Startup India Registration:**
- Partnership opportunities
- Access to government schemes
- Credibility boost

**Accessibility (WCAG 2.1 Level AA):**
- Keyboard navigation
- Screen reader support
- Color contrast ratios (4.5:1 for text)
- Alt text for images
- Captions for videos
- Resizable text (up to 200%)

### 4.6 Service Level Agreements (SLAs)

**Availability:**
- Target: 99.5% uptime (43.8 hours downtime/year)
- Measurement: Monthly uptime percentage
- Exclusions: Scheduled maintenance (announced 48 hours in advance)

**Performance:**
- Page load time: <2 seconds (p95) on 3G
- API response time: <500ms (p95)
- Voice transcription: <3 seconds (p95)
- AI analysis: <3 minutes (p95)

**Support:**
- Free Tier: Email support (48-hour response)
- Premium Tier: Email + Chat support (24-hour response)
- Critical Issues: 4-hour response time

**Data Backup:**
- Frequency: Daily automated backups
- Retention: 7 days
- Recovery Point Objective (RPO): 24 hours
- Recovery Time Objective (RTO): 4 hours

### 4.7 Dependency Management

**Critical Dependencies:**

| Dependency | Version | License | Alternatives | Risk Level |
|------------|---------|---------|--------------|------------|
| Next.js | 14.x | MIT | Remix, Nuxt | Low |
| React | 18.x | MIT | Vue, Svelte | Low |
| PostgreSQL | 15.x | PostgreSQL | MySQL, MongoDB | Low |
| Amazon Bedrock | Latest | AWS | OpenAI, Anthropic | Medium |
| Amazon Transcribe | Latest | AWS | Google Speech-to-Text | Medium |
| Razorpay | Latest | Proprietary | Stripe, PayU | Medium |

**Dependency Update Policy:**
- Security patches: Apply within 48 hours
- Minor updates: Monthly review and update
- Major updates: Quarterly review, test in staging first
- Breaking changes: Plan migration 3 months in advance

### 4.8 Rollback & Disaster Recovery

**Rollback Strategy:**
- Blue/Green deployment for zero-downtime rollback
- Keep last 3 versions deployable
- Automated rollback on health check failure
- Manual rollback option via CI/CD pipeline

**Disaster Recovery Plan:**
- Multi-AZ deployment for high availability
- Cross-region backup (optional for production)
- Database snapshots every 6 hours
- S3 versioning enabled for critical data
- Runbook for common failure scenarios

**Incident Response:**
- P0 (Critical): 15-minute response, 4-hour resolution
- P1 (High): 1-hour response, 24-hour resolution
- P2 (Medium): 4-hour response, 72-hour resolution
- P3 (Low): 24-hour response, 1-week resolution

## 5. Assumptions & Dependencies

### 5.1 Assumptions
- Users have smartphones with internet access
- Users can speak one of the 12 supported languages
- Government scheme data is publicly available
- AWS Free Tier credits available for MVP
- OpenAI/Anthropic APIs remain accessible

### 5.2 Dependencies
- AWS account with necessary permissions
- Domain name registration
- SSL certificate
- Third-party API keys (OpenAI, Anthropic, Google, SerpAPI)
- Government scheme data sources
- Beta user recruitment (50-100 users)

## 6. Success Criteria

### 6.1 MVP Launch (Month 3)
- ✅ 100 beta users onboarded
- ✅ 70%+ onboarding completion rate
- ✅ 4.5+ star rating
- ✅ 50+ scheme applications submitted
- ✅ <5 critical bugs
- ✅ 99%+ uptime

### 6.2 Public Launch (Month 6)
- ✅ 5,000-10,000 total users
- ✅ 500+ successful scheme applications
- ✅ ₹20 Cr+ funding accessed via platform
- ✅ 30%+ referral rate
- ✅ 2-3 incubator partnerships
- ✅ Media coverage (2+ articles)

### 6.3 User Satisfaction
- ✅ 4.5+ star average rating
- ✅ 80%+ would recommend to others
- ✅ 50%+ return within 30 days
- ✅ <10% churn rate

## 7. Out of Scope (Future Phases)

### 7.1 Not in MVP
- Mobile native apps (iOS/Android) - PWA only
- VC pitch deck generation
- Direct VC introductions (premium feature for later)
- Advanced competitor analysis
- White-label solutions for incubators
- API access for third parties
- Blockchain/Web3 features
- International expansion (non-India)

### 7.2 Premium Features (Post-MVP)
- Unlimited AI consultations
- Direct VC warm introductions
- Detailed competitor SWOT analysis
- Specific stock portfolio recommendations
- Export documentation assistance
- Priority 24-hour support
- Monthly check-in calls

## 8. Risks & Mitigation

### 8.1 Technical Risks
| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| AI API rate limits | High | Medium | Use AWS Bedrock as primary, cache responses, implement queue |
| Voice recognition accuracy | High | Medium | Use Amazon Transcribe, allow text fallback, user confirmation |
| Database performance | Medium | Low | Use read replicas, caching, query optimization |
| Third-party API downtime | Medium | Low | Implement retry logic, fallback to cached data |

### 8.2 Business Risks
| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| Low user adoption | High | Medium | Free tier, partnerships, content marketing |
| Government scheme data outdated | Medium | High | Weekly automated scraping, community flagging |
| Competition from established players | Medium | Medium | Focus on voice-first, regional languages, free model |
| Regulatory changes | Low | Low | Legal counsel, compliance monitoring |

## 9. Glossary

- **DPIIT:** Department for Promotion of Industry and Internal Trade
- **SISFS:** Startup India Seed Fund Scheme
- **PMFME:** PM Formalisation of Micro Food Processing Enterprises
- **DPR:** Detailed Project Report
- **IEC:** Import Export Code
- **FSSAI:** Food Safety and Standards Authority of India
- **GST:** Goods and Services Tax
- **VC:** Venture Capital
- **MSME:** Micro, Small and Medium Enterprises
- **PWA:** Progressive Web App
- **OCR:** Optical Character Recognition
- **SIP:** Systematic Investment Plan
- **ETF:** Exchange Traded Fund
- **MAU:** Monthly Active Users
- **NPS:** Net Promoter Score
- **KPI:** Key Performance Indicator
- **SLA:** Service Level Agreement
- **RPO:** Recovery Point Objective
- **RTO:** Recovery Time Objective
- **DPDPA:** Digital Personal Data Protection Act
- **WCAG:** Web Content Accessibility Guidelines
- **JWT:** JSON Web Token
- **API:** Application Programming Interface
- **CDN:** Content Delivery Network
- **IaC:** Infrastructure as Code

## 10. Appendix

### 10.1 User Journey Maps

**Journey 1: First-Time Entrepreneur (Voice-First)**

```
Stage 1: Discovery (Day 0)
├─ User hears about Startup Saathi from friend
├─ Visits website on mobile (3G connection)
├─ Sees "Start with Voice" button in Hindi
└─ Clicks to begin

Stage 2: Onboarding (Day 0, 5-10 minutes)
├─ Grants microphone permission
├─ Speaks business idea in Hindi
├─ System transcribes and confirms
├─ Asks follow-up questions (skills, location, budget)
├─ User provides answers via voice
└─ Profile created

Stage 3: Analysis (Day 0, 2-3 minutes)
├─ System shows "Analyzing..." with progress bar
├─ AI generates recommendations
├─ User sees dashboard with results
└─ Explores top 3 product recommendations

Stage 4: Scheme Discovery (Day 0-1)
├─ User clicks "Government Schemes"
├─ Sees 5 matched schemes with relevance scores
├─ Clicks on SISFS (Startup India Seed Fund)
├─ Reads eligibility, benefits, documents
├─ Downloads DPR template
└─ Sets reminder for deadline

Stage 5: Legal Compliance (Day 1-7)
├─ User clicks "Legal Checklist"
├─ Sees prioritized list (Critical → Low)
├─ Starts with FSSAI license (food business)
├─ Follows step-by-step guide
├─ Downloads PDF checklist
└─ Completes first compliance item

Stage 6: Ongoing Engagement (Week 2+)
├─ Receives WhatsApp reminder (scheme deadline)
├─ Asks AI chat: "How to write business plan?"
├─ Gets personalized response with examples
├─ Downloads marketing plan
└─ Refers 2 friends to platform

Stage 7: Success (Month 3)
├─ Submits scheme application
├─ Receives ₹10L funding
├─ Launches business
├─ Leaves 5-star review
└─ Becomes premium user
```

**Journey 2: Professional (Text-First)**

```
Stage 1: Discovery (Day 0)
├─ Searches Google: "startup guidance India"
├─ Finds Startup Saathi in results
├─ Reads landing page
└─ Signs up with email

Stage 2: Onboarding (Day 0, 3-5 minutes)
├─ Fills profile form (text input)
├─ Selects business type: SaaS
├─ Provides skills: Software development, Product management
├─ Sets budget: ₹5L
└─ Submits profile

Stage 3: Analysis (Day 0, 2-3 minutes)
├─ Receives product recommendations
├─ Sees "AI-powered HR SaaS" as top match (95% score)
├─ Reviews market demand, competition, costs
└─ Decides to proceed

Stage 4: Deep Dive (Day 1-3)
├─ Explores legal checklist
├─ Learns about company registration, GST, IT Act
├─ Downloads marketing plan
├─ Reviews VC database
└─ Identifies 10 relevant VCs

Stage 5: Execution (Week 1-4)
├─ Completes legal compliance
├─ Builds MVP
├─ Uses marketing templates
├─ Applies to 3 schemes
└─ Reaches out to VCs

Stage 6: Success (Month 6)
├─ Receives seed funding from VC
├─ Hires team
├─ Upgrades to premium tier
└─ Recommends to startup community
```

### 10.2 Edge Cases & Error Handling

**Voice Recognition Edge Cases:**

| Scenario | Expected Behavior | Fallback |
|----------|-------------------|----------|
| Heavy background noise | Show warning: "Noisy environment detected" | Offer text input |
| Unclear speech | Ask user to repeat | Offer text input |
| Unsupported language | Detect and notify user | Offer supported languages |
| Network interruption | Save partial transcription | Resume on reconnect |
| Audio file too large | Compress before upload | Show error if >10MB |
| Profanity detected | Filter and warn user | Block if repeated |

**AI Analysis Edge Cases:**

| Scenario | Expected Behavior | Fallback |
|----------|-------------------|----------|
| Insufficient profile data | Request missing information | Provide generic recommendations |
| No matching schemes | Show "No exact matches, here are similar ones" | Show top 5 general schemes |
| API rate limit exceeded | Queue request | Show cached results |
| AI service down | Use cached responses | Show error message |
| Ambiguous business idea | Ask clarifying questions | Provide multiple interpretations |
| Unrealistic budget | Warn user and adjust expectations | Show budget-appropriate options |

**Payment Edge Cases:**

| Scenario | Expected Behavior | Fallback |
|----------|-------------------|----------|
| Payment gateway down | Retry 3 times | Show error, offer alternative |
| Insufficient funds | Show clear error message | Offer lower-tier plan |
| Currency mismatch | Convert to INR | Show error if unsupported |
| Duplicate payment | Detect and refund | Notify user |
| Refund request | Process within 7 days | Manual review if >₹10K |

**Data Quality Edge Cases:**

| Scenario | Expected Behavior | Fallback |
|----------|-------------------|----------|
| Stale scheme data | Show "Last updated: X days ago" | Flag for manual review |
| Broken scheme URL | Show error, offer alternative | Report to admin |
| Duplicate schemes | Deduplicate automatically | Manual review if uncertain |
| Missing eligibility criteria | Show "Contact scheme authority" | Provide general guidance |
| Conflicting information | Show both sources | Ask user to verify |

### 10.3 A/B Testing Plan

**Experiment 1: Voice vs Text Onboarding**
- Hypothesis: Voice-first onboarding increases completion rate by 20%
- Variants: A (Voice-first), B (Text-first)
- Sample size: 1,000 users (500 each)
- Duration: 2 weeks
- Success metric: Onboarding completion rate
- Decision criteria: >15% improvement with p<0.05

**Experiment 2: AI Recommendation Format**
- Hypothesis: Detailed recommendations increase user satisfaction
- Variants: A (Brief), B (Detailed with visuals)
- Sample size: 500 users (250 each)
- Duration: 1 week
- Success metric: User satisfaction rating
- Decision criteria: >10% improvement with p<0.05

**Experiment 3: Notification Frequency**
- Hypothesis: 2 notifications/week is optimal
- Variants: A (1/week), B (2/week), C (3/week)
- Sample size: 900 users (300 each)
- Duration: 4 weeks
- Success metric: Notification open rate + unsubscribe rate
- Decision criteria: Highest open rate with <5% unsubscribe

**Experiment 4: Pricing Tiers**
- Hypothesis: ₹499/month is optimal price point
- Variants: A (₹299), B (₹499), C (₹999)
- Sample size: 600 users (200 each)
- Duration: 1 month
- Success metric: Conversion rate
- Decision criteria: Highest revenue (conversion × price)

### 10.4 Internationalization (i18n) Strategy

**Translation Approach:**
- Use professional translators (not Google Translate)
- Cultural adaptation (not just literal translation)
- Regional examples and case studies
- Local currency and date formats

**Language Support Matrix:**

| Language | Code | Script | Voice Support | Text Support | Priority |
|----------|------|--------|---------------|--------------|----------|
| Hindi | hi-IN | Devanagari | ✅ | ✅ | P0 |
| English | en-IN | Latin | ✅ | ✅ | P0 |
| Tamil | ta-IN | Tamil | ✅ | ✅ | P1 |
| Telugu | te-IN | Telugu | ✅ | ✅ | P1 |
| Bengali | bn-IN | Bengali | ✅ | ✅ | P1 |
| Marathi | mr-IN | Devanagari | ✅ | ✅ | P1 |
| Gujarati | gu-IN | Gujarati | ✅ | ✅ | P2 |
| Kannada | kn-IN | Kannada | ✅ | ✅ | P2 |
| Malayalam | ml-IN | Malayalam | ✅ | ✅ | P2 |
| Punjabi | pa-IN | Gurmukhi | ✅ | ✅ | P2 |
| Odia | or-IN | Odia | ✅ | ✅ | P3 |
| Assamese | as-IN | Bengali | ✅ | ✅ | P3 |

**Translation Workflow:**
1. Extract strings from codebase (i18next)
2. Send to professional translators
3. Review by native speakers
4. QA testing in each language
5. Deploy to production
6. Monitor user feedback

**Content to Translate:**
- UI labels and buttons
- Error messages
- Email templates
- SMS templates
- WhatsApp messages
- Legal disclaimers
- Help documentation
- Video subtitles

**Content NOT to Translate:**
- User-generated content
- Scheme names (keep original)
- Legal terms (provide glossary)
- Brand name (Startup Saathi)

### 10.5 Security Threat Model

**Threat 1: SQL Injection**
- Attack Vector: Malicious input in forms
- Impact: Data breach, data loss
- Mitigation: Parameterized queries, input validation, ORM
- Detection: WAF logs, database audit logs
- Response: Block IP, patch vulnerability, notify users

**Threat 2: Cross-Site Scripting (XSS)**
- Attack Vector: Malicious scripts in user input
- Impact: Session hijacking, data theft
- Mitigation: Content Security Policy, input sanitization, output encoding
- Detection: WAF logs, browser console errors
- Response: Block IP, sanitize data, notify users

**Threat 3: Distributed Denial of Service (DDoS)**
- Attack Vector: Flood of requests from multiple sources
- Impact: Service unavailability
- Mitigation: AWS Shield, CloudFront, rate limiting
- Detection: CloudWatch alarms, traffic spikes
- Response: Enable DDoS protection, block IPs, scale infrastructure

**Threat 4: Data Breach**
- Attack Vector: Unauthorized access to database
- Impact: PII exposure, regulatory fines
- Mitigation: Encryption, access controls, audit logs
- Detection: Unusual database queries, failed login attempts
- Response: Isolate breach, notify users within 72 hours, forensic analysis

**Threat 5: API Abuse**
- Attack Vector: Excessive API calls, scraping
- Impact: Increased costs, service degradation
- Mitigation: Rate limiting, API keys, CAPTCHA
- Detection: CloudWatch metrics, unusual patterns
- Response: Throttle requests, block API keys, contact user

**Threat 6: Social Engineering**
- Attack Vector: Phishing, impersonation
- Impact: Account takeover, data theft
- Mitigation: 2FA, security awareness, email verification
- Detection: Unusual login locations, password reset requests
- Response: Lock account, notify user, investigate

### 10.6 Performance Benchmarks

**Load Testing Results (Expected):**

| Metric | 100 Users | 500 Users | 1,000 Users | 5,000 Users |
|--------|-----------|-----------|-------------|-------------|
| Avg Response Time | 150ms | 250ms | 400ms | 800ms |
| p95 Response Time | 300ms | 500ms | 800ms | 1,500ms |
| p99 Response Time | 500ms | 1,000ms | 1,500ms | 3,000ms |
| Error Rate | 0.1% | 0.5% | 1% | 2% |
| CPU Utilization | 20% | 40% | 60% | 80% |
| Memory Usage | 30% | 50% | 70% | 85% |
| Database Connections | 10 | 30 | 50 | 100 |

**Optimization Targets:**

| Component | Current | Target | Strategy |
|-----------|---------|--------|----------|
| Page Load Time | 3s | <2s | Code splitting, lazy loading, CDN |
| API Response Time | 800ms | <500ms | Caching, query optimization, indexing |
| Voice Transcription | 5s | <3s | Batch processing, compression |
| AI Analysis | 5min | <3min | Parallel processing, prompt optimization |
| Database Queries | 200ms | <100ms | Indexing, read replicas, connection pooling |
| Image Upload | 10s | <5s | Compression, S3 transfer acceleration |

---

**Document Status:** Draft v1.1 (Enhanced)  
**Last Updated:** February 15, 2026  
**Next Review:** After stakeholder feedback  
**Approved By:** [Pending Amazon Head of Engineering Review]  
**Change Log:**
- v1.0: Initial draft
- v1.1: Added detailed KPIs, API specs, SLAs, edge cases, A/B testing plan, i18n strategy, security threat model, performance benchmarks
