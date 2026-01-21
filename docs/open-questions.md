# Open Questions - Music Band T-Shirt E-Commerce Store

## Overview

This document captures ambiguities, assumptions, and open questions that require clarification or decision-making to ensure successful project execution.

---

## Business & Product Questions

### 1. Product Catalog & Inventory

**Q1.1**: What is the initial catalog size at MVP launch?

- **Status**: ✅ Decided
- **Impact**: High - affects database seeding, testing, and marketing strategy
- **Options**:
  - Option A: 50-100 unique designs (minimal viable catalog)
  - Option B: 200-300 designs (comprehensive catalog)
  - Option C: 500+ designs (extensive catalog)
- **Recommendation**: Start with 100-150 designs to validate product-market fit
- **Decision By**: Week 1 of development

↪️ **Decision**: Option A 50-100 unique designs (minimal viable catalog)

**Q1.2**: Will products be print-on-demand or pre-stocked inventory?

- **Status**: ✅ Decided
- **Impact**: High - affects fulfillment workflow, inventory management, and financial model
- **Options**:
  - Option A: Print-on-demand (lower risk, higher per-unit cost, longer fulfillment)
  - Option B: Pre-stocked inventory (higher upfront cost, faster fulfillment)
  - Option C: Hybrid approach (bestsellers pre-stocked, others on-demand)
- **Recommendation**: Start with print-on-demand to minimize risk, transition to hybrid based on sales data
- **Decision By**: Week 1 of development

↪️ **Decision**: Option A: Print-on-demand (lower risk, higher per-unit cost, longer fulfillment)

**Q1.3**: How will band/artist licensing be handled?

- **Status**: ✅ Decided
- **Impact**: Critical - affects legal compliance and product availability
- **Considerations**:
  - Official licensed merchandise vs fan art
  - Licensing agreements with bands/labels
  - Copyright compliance and DMCA takedown process
  - Legal review required
- **Recommendation**: Consult with entertainment attorney, establish clear licensing policy
- **Decision By**: Before MVP launch

↪️ **Decision**: Official licensed merchandise vs fan art

**Q1.4**: What product categories beyond T-shirts will be offered?

- **Status**: ✅ Decided
- **Assumption**: MVP focuses on T-shirts only; Phase 2+ may add hoodies, hats, posters
- **Validation Needed**: Confirm with stakeholders

↪️ **Decision**: T-shirts only - we can gather info about customer's preferences on new merchandise 

### 2. Pricing & Payments

**Q2.1**: What is the target price range for T-shirts?

- **Status**: ✅ Decided
- **Impact**: Medium - affects positioning, marketing, and profit margins
- **Market Research**:
  - Standard band T-shirts: $20-30
  - Premium/limited edition: $35-50
  - Exclusive collaborations: $50+
- **Recommendation**: $25-45 range with most products at $30-35
- **Decision By**: Week 2 of development

↪️ **Decision**: We will keep a standard and premium price between $20 to $50

**Q2.2**: Will international payments and currencies be supported at MVP?

- **Status**: ✅ Decided
- **Decision**: USD only for MVP; multi-currency in Phase 3
- **Rationale**: Reduce complexity for initial launch

**Q2.3**: What is the refund/return policy?

- **Status**: ✅ Decided
- **Impact**: High - affects customer satisfaction and operational complexity
- **Considerations**:
  - Return window (30 days, 60 days, 90 days)
  - Return shipping cost (customer pays or free returns)
  - Restocking fees
  - Condition requirements (unworn, tags attached)
- **Recommendation**: 30-day return window, customer pays return shipping, no restocking fee
- **Decision By**: Week 2 of development

↪️ **Decision**: 30-day return window, customer pays return shipping, no restocking fee

### 3. Shipping & Fulfillment

**Q3.1**: What shipping carriers and options will be offered?

- **Status**: ✅ Decided
- **Impact**: High - affects costs, delivery times, and customer satisfaction
- **Options**:
  - USPS (economical, slower)
  - UPS/FedEx (faster, more expensive)
  - DHL (international)
  - Offer multiple tiers (standard, expedited, overnight)
- **Recommendation**: USPS for domestic standard, UPS for expedited
- **Decision By**: Week 3 of development

↪️ **Decision**: USPS for domestic standard, UPS for expedited - make customer know both offers

**Q3.2**: What countries will be supported for shipping at MVP?

- **Status**: ✅ Decided
- **Decision**: US and Canada for MVP; expand internationally in Phase 3
- **Rationale**: Focus on primary market, reduce complexity

**Q3.3**: How will shipping costs be calculated?

- **Status**: ✅ Decided
- **Impact**: Medium - affects profitability and customer experience
- **Options**:
  - Flat rate (e.g., $5.99 per order)
  - Weight-based calculated shipping
  - Free shipping threshold (e.g., free over $50)
  - Zone-based pricing
- **Recommendation**: Flat $5.99 for MVP, free over $75
- **Decision By**: Week 3 of development

↪️ **Decision**: Weight-based calculated shipping - later free over $75 can be apply

### 4. Marketing & Customer Acquisition

**Q4.1**: What is the customer acquisition strategy?

- **Status**: ✅ Decided
- **Impact**: High - determines marketing budget and launch success
- **Channels to Consider**:
  - Social media advertising (Facebook, Instagram, TikTok)
  - Google Ads (search, display)
  - Influencer partnerships
  - Music blogs and communities
  - Email marketing
  - SEO and content marketing
- **Recommendation**: Multi-channel approach with focus on social media and influencer partnerships
- **Decision By**: Week 4 (before MVP launch)

↪️ **Decision**: Multi-channel approach with focus on social media and influencer partnerships

**Q4.2**: What is the pre-launch marketing timeline?

- **Status**: ✅ Decided
- **Impact**: High - affects launch momentum
- **Milestones**:
  - 8 weeks before: Teaser campaign, build email list
  - 4 weeks before: Product reveals, influencer outreach
  - 2 weeks before: Launch promotions announced
  - Launch day: Press release, social media blitz
- **Recommendation**: Start pre-launch marketing 8 weeks before MVP
- **Decision By**: Week 1 of development

↪️ **Decision**: Start pre-launch marketing 8 weeks before MVP

---

## Technical Questions

### 5. Infrastructure & Hosting

**Q5.1**: What cloud provider will be used?

- **Status**: ✅ Decided
- **Decision**: AWS or DigitalOcean based on budget
- **Preference**: DigitalOcean for simplicity and cost-effectiveness at MVP scale

**Q5.2**: What is the expected initial traffic volume?

- **Status**: ✅ Decided
- **Impact**: High - affects infrastructure sizing and costs
- **Estimates Needed**:
  - Concurrent users
  - Monthly page views
  - Orders per day
- **Assumption**: 1,000 MAU, 50,000 monthly page views, 10-20 orders/day at launch
- **Validation**: Adjust infrastructure based on actual traffic

↪️ **Decision**: 1,000 MAU, 50,000 monthly page views, 10-20 orders/day at launch

**Q5.3**: What is the disaster recovery plan?

- **Status**: ✅ Decided
- **Impact**: High - affects business continuity
- **Considerations**:
  - Database backup frequency (daily, hourly)
  - Backup retention period
  - Recovery Time Objective (RTO)
  - Recovery Point Objective (RPO)
- **Recommendation**: Daily automated backups, 30-day retention, <4 hour RTO, <1 hour RPO
- **Decision By**: Week 2 of development

↪️ **Decision**: Daily automated backups, 2 months retention, <6 hours RTO, <3 hours RPO

### 6. Data & Privacy

**Q6.1**: What data privacy regulations must be complied with?

- **Status**: ✅ Decided
- **Requirements**:
  - GDPR (European customers in Phase 3)
  - CCPA (California customers)
  - General privacy best practices
- **Action Items**:
  - Privacy policy creation
  - Cookie consent implementation (Phase 3)
  - Data retention policy definition
  - GDPR compliance for international expansion

**Q6.2**: How long will customer data be retained?

- **Status**: ✅ Decided
- **Impact**: Medium - affects storage costs and compliance
- **Considerations**:
  - Active customer data: Indefinitely (or until account deletion)
  - Order history: 7 years (for accounting/legal)
  - Inactive accounts: Delete after 3 years of inactivity
  - Guest order data: 2 years
- **Recommendation**: Above retention periods with automated cleanup
- **Decision By**: Week 2 of development

↪️ **Decision**:
  - Customer data is retained according to activity and legal needs: active accounts are kept until deletion.
  - Order history is stored for 7 years.
  - Inactive accounts are removed after three years.
  - Guest order data is deleted or anonymized after two years.

### 7. Integrations & Third-Party Services

**Q7.1**: Which email service provider will be used?

- **Status**: ✅ Decided
- **Decision**: SendGrid for reliable transactional emails
- **Alternative**: Mailgun as backup option

**Q7.2**: Will there be integration with social media platforms for inventory sync?

- **Status**: ⚠️ Needs Answer for Phase 3
- **Impact**: Low - can be deferred to Phase 3
- **Platforms**: Instagram Shopping, Facebook Shops, Pinterest
- **Recommendation**: Evaluate after MVP launch based on social media traffic

↪️ **Decision**: *TBD*

**Q7.3**: Will there be integration with accounting software?

- **Status**: ⚠️ Needs Answer
- **Impact**: Medium - affects financial reporting
- **Options**: QuickBooks, Xero, manual export
- **Recommendation**: Manual CSV export for MVP, API integration in Phase 2
- **Decision By**: Week 4 of development

↪️ **Decision**: *TBD*

---

## Design & UX Questions

### 8. Branding & Visual Identity

**Q8.1**: What is the brand identity and visual style?

- **Status**: ✅ Decided
- **Impact**: High - affects all design work
- **Deliverables Needed**:
  - Logo and brand guidelines
  - Color palette
  - Typography
  - Imagery style (photography, illustrations)
  - Tone of voice
- **Recommendation**: Align with music/band culture aesthetic
- **Decision By**: Week 1 of development (design phase)

↪️ **Decision**:
  - Modern, music-culture–inspired visual identity (skull and blood ☠️🩸).
  - Dark high-contrast colors (black&white base).
  - Dark, gothic and intensitive typography
  - Authentic imagery, and a confident, community-oriented tone of voice.

**Q8.2**: Will there be a mobile app or just responsive web?

- **Status**: ✅ Decided
- **Decision**: Responsive web only for MVP and all phases
- **Rationale**: Lower development cost, faster time to market
- **Future Consideration**: Native mobile app if web traffic >50% mobile

### 9. User Experience

**Q9.1**: What level of accessibility compliance is required?

- **Status**: ✅ Decided
- **Decision**: WCAG 2.1 AA compliance by Phase 3
- **MVP**: Basic accessibility (semantic HTML, keyboard navigation)
- **Phase 3**: Full WCAG 2.1 AA compliance with audit

**Q9.2**: Will there be a guest checkout option?

- **Status**: ✅ Decided
- **Decision**: Yes, guest checkout available at MVP
- **Rationale**: Reduce friction for first-time buyers

**Q9.3**: What is the cart expiration policy?

- **Status**: ✅ Decided
- **Impact**: Low - affects user experience
- **Options**:
  - No expiration (persist indefinitely)
  - 30-day expiration
  - 7-day expiration
- **Recommendation**: 30-day expiration for logged-in users, 7-day for guest carts
- **Decision By**: Week 2 of development

↪️ **Decision** 30-day expiration for logged-in users, 7-day for guest carts

---

## Operational Questions

### 10. Customer Support

**Q10.1**: What customer support channels will be offered?

- **Status**: ✅ Decided
- **Impact**: High - affects operational costs and customer satisfaction
- **Options**:
  - Email support (ticketing system)
  - Live chat (automated or human)
  - Phone support
  - Social media support
  - FAQ/Help center
- **Recommendation**: Email support + live chat (with chatbot) + comprehensive FAQ for MVP
- **Decision By**: Week 3 of development

↪️ **Decision**: Email support + live chat (with chatbot) + comprehensive FAQ for MVP

**Q10.2**: What are the support hours?

- **Status**: ✅ Decided
- **Impact**: Medium - affects staffing
- **Options**:
  - 24/7 support
  - Business hours (9am-5pm EST)
  - Extended hours (7am-10pm EST)
- **Recommendation**: Business hours for MVP with email ticket queue
- **Decision By**: Week 3 of development

↪️ **Decision**: Business hours

**Q10.3**: What is the expected support ticket volume?

- **Status**: ✅ Decided
- **Impact**: Medium - affects staffing and tool selection
- **Assumptions**: 5-10% of orders generate support tickets, 50-100 tickets/month at MVP
- **Validation**: Adjust staffing based on actual volume

↪️ **Decision**: 5-10% of orders generate support tickets, 50-100 tickets/month at MVP

### 11. Content Management

**Q11.1**: Who will create and manage blog content?

- **Status**: ✅ Decided
- **Impact**: Medium - affects Phase 2 planning
- **Options**:
  - Dedicated content creator (hire or contract)
  - Community-contributed content
  - AI-assisted content creation
- **Recommendation**: Contract content creator for initial content, evaluate ongoing model
- **Decision By**: End of MVP phase

↪️ **Decision**: Contract content creator for initial content, evaluate ongoing model

**Q11.2**: What is the content publication frequency?

- **Status**: ✅ Decided
- **Impact**: Medium - affects content strategy
- **Recommendation**: 2-3 blog posts per week
- **Decision By**: End of MVP phase

↪️ **Decision**: 2-3 blog posts per week

---

## Legal & Compliance Questions

### 12. Legal & Regulatory

**Q12.1**: What legal entity will operate the store?

- **Status**: ⚠️ Needs Answer
- **Impact**: Critical - affects taxes, liability, compliance
- **Considerations**:
  - LLC, Corporation, or other structure
  - State of incorporation
  - Tax implications
- **Recommendation**: Consult with attorney and accountant
- **Decision By**: Before MVP launch

↪️ **Decision**: TBD

**Q12.2**: What terms of service and policies are required?

- **Status**: ⚠️ Needs Creation
- **Impact**: High - affects legal compliance
- **Required Documents**:
  - Terms of Service
  - Privacy Policy
  - Return/Refund Policy
  - Shipping Policy
  - Cookie Policy (Phase 3)
- **Recommendation**: Legal review of all policies before launch
- **Decision By**: Week 6 of development

↪️ **Decision**: TBD

**Q12.3**: Are there age restrictions for purchasing?

- **Status**: ⚠️ Needs Answer
- **Impact**: Low - standard practice
- **Recommendation**: 13+ to comply with COPPA, 18+ for creating account (or parental consent)
- **Decision By**: Week 4 of development

↪️ **Decision**:
  - Content will be accessible to users aged 13 and older in compliance with COPPA.
  - Content classified as 16–17 will be restricted to that age group with appropriate labeling.
  - Account creation is limited to adults (18+) or minors with verified parental consent, and all 18+ content remains strictly age-gated.

---

## Financial Questions

### 13. Budget & Pricing

**Q13.1**: What is the total project budget?

- **Status**: ⚠️ Needs Answer
- **Impact**: Critical - affects scope and timeline
- **Components**:
  - Development costs (team salaries)
  - Infrastructure costs
  - Third-party service costs
  - Marketing budget
  - Legal and administrative costs
- **Recommendation**: Define budget with detailed breakdown
- **Decision By**: Project kickoff

↪️ **Decision**: TBD

**Q13.2**: What are the revenue targets for Year 1?

- **Status**: ⚠️ Needs Answer
- **Impact**: High - affects business viability
- **Milestones**:
  - Month 1-3 (MVP): $10,000-20,000 GMV
  - Month 4-6 (Phase 1): $30,000-50,000 GMV
  - Month 7-12 (Phase 2-3): $100,000-200,000 GMV
- **Recommendation**: Set realistic targets based on market research
- **Decision By**: Week 2 of development

↪️ **Decision**: TBD

**Q13.3**: What is the break-even timeline?

- **Status**: ⚠️ Needs Answer
- **Impact**: High - affects investor expectations
- **Factors**:
  - Operating costs
  - Customer acquisition costs
  - Profit margins
  - Growth rate
- **Recommendation**: Develop financial model with break-even analysis
- **Decision By**: Week 2 of development

↪️ **Decision**: TBD

---

## Risk & Assumptions

### 14. Key Assumptions

**Assumption 1**: Market Demand

- **Assumption**: There is sufficient demand for band T-shirts through a specialized e-commerce platform
- **Validation Method**: Pre-launch marketing, MVP sales data
- **Mitigation**: Market research, competitive analysis, customer interviews

**Assumption 2**: Fulfillment Partnership

- **Assumption**: Reliable print-on-demand or fulfillment partner available
- **Validation Method**: Partner vetting, test orders
- **Mitigation**: Identify backup fulfillment partners

**Assumption 3**: Payment Processing

- **Assumption**: Stripe payment processing meets all requirements
- **Validation Method**: Integration testing, test transactions
- **Mitigation**: PayPal as backup payment option (Phase 2)

**Assumption 4**: Technical Team Capacity

- **Assumption**: 4-person team (Tech Lead, Backend, Frontend, UI/UX) can deliver MVP in 8 weeks
- **Validation Method**: Sprint velocity tracking
- **Mitigation**: Adjust scope or timeline based on actual velocity

**Assumption 5**: Copyright Compliance

- **Assumption**: Band licensing and copyright issues can be managed within legal guidelines
- **Validation Method**: Legal consultation
- **Mitigation**: Clear DMCA process, licensing agreements, legal review

---

## Decision Log

### Decisions Made

| Decision                          | Date       | Made By       | Rationale                                   |
| --------------------------------- | ---------- | ------------- | ------------------------------------------- |
| Technology stack: FastAPI + React | 2024-11-21 | Tech Lead     | Modern, performant, team expertise          |
| MVP duration: 8 weeks             | 2024-11-21 | Product Owner | Balance between features and time-to-market |
| Clean Architecture + DDD          | 2024-11-21 | Tech Lead     | Maintainability, scalability, testability   |
| Guest checkout enabled            | 2024-11-21 | Product Owner | Reduce friction for first-time buyers       |
| USD only for MVP                  | 2024-11-21 | Product Owner | Simplify MVP, add multi-currency later      |

### Decisions Pending

| Question                        | Target Date | Owner          | Priority |
| ------------------------------- | ----------- | -------------- | -------- |
| Initial catalog size            | Week 1      | Product Owner  | High     |
| Print-on-demand vs inventory    | Week 1      | Product Owner  | High     |
| Brand identity and visual style | Week 1      | UI/UX Engineer | High     |
| Shipping carriers and rates     | Week 3      | Product Owner  | High     |
| Customer support channels       | Week 3      | Product Owner  | Medium   |
| Legal entity and policies       | Week 6      | Business Owner | Critical |

---

## Next Steps

1. **Week 1**: Resolve all "High" and "Critical" priority questions
2. **Week 2**: Finalize business decisions (pricing, budget, policies)
3. **Week 3**: Resolve operational questions (support, shipping)
4. **Week 4**: Final review before MVP launch preparation

---

**Document Status**: ✅ Active (update regularly as questions are answered)  
**Last Updated**: January 21, 2026  
**Version**: 1.0  
**Owner**: Product Owner

**Review Cadence**: Weekly during development, updated as decisions are made
