# Maya Attribution Source/Medium Taxonomy Mapping

## Description
WORKFLOW: Prerequisite source/medium taxonomy mapping across all marketing platforms. Maps GA4 attribution sources to platform-specific tracking for accurate cross-platform conversion validation. Must run before maya_conversion_audit for proper attribution comparison.

## System Message
You are Maya's Attribution Mapping Specialist. Create comprehensive source/medium taxonomy that enables accurate cross-platform conversion validation. This analysis is the prerequisite foundation for all subsequent conversion tracking audits and must run BEFORE maya_conversion_audit.

## User Message Template
EXECUTE MAYA ATTRIBUTION SOURCE/MEDIUM MAPPING WORKFLOW:

**STEP 1: GA4 SOURCE/MEDIUM DISCOVERY**
Build complete inventory of all traffic attribution sources.

Action Required:
**GA4 Source/Medium Breakdown** (Category: "GA4"):
- Primary: "'Analytics Measures'[-GA4 Sessions #]"
- Secondary: "'Analytics Measures'[-GA4 Key Events #]"
- Slice: "'_Campaigns'[Campaign Maya Source Medium]"
- Secondary Slice: "'_Campaigns'[Campaign Source Actual]"
- Tertiary Slice: "'_Campaigns'[Campaign Medium Actual]"

**GA4 Campaign Attribution** (Category: "GA4"):
- Primary: "'Analytics Measures'[-GA4 Sessions #]"
- Slice: "'_Campaigns'[Campaign Actual]"
- Filter: Sessions > {% if traffic_threshold %}{{ traffic_threshold }}{% else %}100{% endif %}

Output: Complete inventory of all source/medium combinations with session volumes

**STEP 2: PLATFORM-SPECIFIC SOURCE/MEDIUM IDENTIFICATION**
Categorize and map sources to marketing platforms.

Action Required:
**SEM Source/Medium Patterns**:
- Identify: google / cpc, bing / cpc, yahoo / cpc patterns
- Flag: google / organic (not SEM), google / (not set)
- Map: Campaign names to SEM account structure
- Validate: Paid search vs. organic search attribution

**Social Media Source/Medium Patterns**:
- Facebook: facebook / cpc, facebook / social, facebook / referral
- LinkedIn: linkedin / cpc, linkedin / social  
- Twitter: twitter / social, t.co / referral
- YouTube: youtube / social, youtube / referral

**Email Marketing Source/Medium Patterns**:
- Email: newsletter / email, campaign / email, mailchimp / email
- Marketing automation: klaviyo / email, hubspot / email
- Internal: internal / email, viva / email

**Direct & Referral Traffic**:
- Direct: (direct) / (none), (direct) / (not set)
- Referral: Partner sites, affiliate links, PR mentions
- Organic: google / organic, bing / organic

**STEP 3: CROSS-PLATFORM ATTRIBUTION VALIDATION**
Validate platform data alignment with GA4 source attribution.

Action Required:
**SEM Attribution Cross-Check**:
- Compare SEM spend data (Category: "SEM") with GA4 google/cpc sessions
- Calculate session-to-conversion ratios by platform
- Flag major discrepancies in volume or attribution timing
- Document SEM campaign name mapping inconsistencies

**Facebook Attribution Cross-Check**:
- Compare Facebook spend data (Category: "Facebook") with GA4 facebook/cpc sessions  
- Validate Facebook pixel vs. GA4 conversion event alignment
- Check UTM parameter consistency in campaign tracking
- Identify Facebook organic vs. paid attribution gaps

**Email Marketing Attribution Cross-Check**:
- Compare Email Marketing data (Category: "Email Marketing") with GA4 email medium sessions
- Validate campaign name consistency across platforms
- Check for missing UTM parameters in email campaigns
- Identify email click vs. GA4 session attribution discrepancies

**STEP 4: SOURCE/MEDIUM STANDARDIZATION FRAMEWORK**
Create unified attribution taxonomy for cross-platform analysis.

Output Required:
**Standardized Source/Medium Mapping**:
```
PLATFORM ATTRIBUTION MAP:
├── Paid Search (SEM)
│   ├── GA4 Sources: google/cpc, bing/cpc, yahoo/cpc
│   ├── Maya Category: "SEM"
│   └── Validation: Compare with SEM spend data
├── Social Media Paid
│   ├── Facebook: facebook/cpc, facebook/social (paid)
│   ├── LinkedIn: linkedin/cpc  
│   ├── Maya Category: "Facebook" 
│   └── Validation: Compare with Facebook spend data
├── Email Marketing
│   ├── GA4 Sources: */email, newsletter/*, mailchimp/*
│   ├── Maya Category: "Email Marketing"
│   └── Validation: Compare with email send data
├── Organic Channels
│   ├── SEO: google/organic, bing/organic
│   ├── Social Organic: facebook/social (unpaid), youtube/social
│   ├── Maya Category: "SEO", "FB Organic"
│   └── Validation: Compare with organic performance data
└── Direct & Referral
    ├── Direct: (direct)/(none), (direct)/(not set)
    ├── Referral: Partner domains, affiliate links
    └── Validation: Manual review of top referrers
```

**STEP 5: ATTRIBUTION DISCREPANCY IDENTIFICATION**
Flag source/medium mapping issues that affect conversion validation.

Action Required:
**Data Quality Issues**:
- Missing UTM parameters: High (direct)/(none) traffic from paid campaigns
- Inconsistent naming: Same campaign with multiple source/medium combinations
- Platform leakage: Facebook traffic showing as google/cpc due to referrer issues
- Attribution gaps: Sessions without corresponding platform spend data

**Critical Validation Gates**:
- ✅ SEM GA4 sessions align with SEM spend periods (±20% variance acceptable)
- ✅ Facebook GA4 sessions correlate with Facebook impression data  
- ✅ Email GA4 sessions match email send volume patterns
- ✅ No major "unattributed" traffic spikes during campaign periods

**STEP 6: CROSS-PLATFORM CONVERSION READINESS ASSESSMENT**
Validate attribution framework for accurate conversion comparison.

Action Required:
**Platform Attribution Health Score**:
- SEM Attribution Accuracy: [Score/10] (based on GA4 vs. platform data alignment)
- Facebook Attribution Accuracy: [Score/10]
- Email Attribution Accuracy: [Score/10]  
- Overall Attribution Framework Health: [Score/10]

**Conversion Validation Readiness**:
- ✅ Platform source/medium mapping complete
- ✅ Attribution discrepancies <30% identified and documented
- ✅ Campaign naming inconsistencies flagged for cleanup
- ✅ UTM parameter gaps identified for tracking improvement

**STEP 7: ATTRIBUTION FRAMEWORK FOR CONVERSION ANALYSIS**
Provide standardized framework for maya_conversion_audit usage.

Output Required: 
**Conversion Validation Framework**:
```
FOR SEM CONVERSION VALIDATION:
- GA4 Filter: "'_Campaigns'[Campaign Maya Source Medium]" IN 
  ("google / cpc", "bing / cpc", "yahoo / cpc")
- Compare to: Category "SEM" conversion data
- Expected variance: <30% (due to attribution model differences)

FOR FACEBOOK CONVERSION VALIDATION:  
- GA4 Filter: "'_Campaigns'[Campaign Maya Source Medium]" IN
  ("facebook / cpc", "facebook / social", "instagram / social")
- Compare to: Category "Facebook" conversion data  
- Expected variance: <25% (tighter pixel integration)

FOR EMAIL CONVERSION VALIDATION:
- GA4 Filter: "'_Campaigns'[Campaign Maya Source Medium]" CONTAINS "email"
- Compare to: Category "Email Marketing" conversion data
- Expected variance: <40% (longer attribution windows)
```

FRAMEWORK PARAMETERS:
- Analysis Timeframe: {% if analysis_timeframe %}{{ analysis_timeframe }}{% else %}last 3 months{% endif %}
- Traffic Threshold: {% if traffic_threshold %}{{ traffic_threshold }}{% else %}100 sessions minimum{% endif %}
- Platform Focus: {% if platform_focus %}{{ platform_focus }}{% else %}All integrated platforms{% endif %}

CRITICAL OUTPUT: This attribution mapping is MANDATORY before running maya_conversion_audit. Without accurate source/medium taxonomy, conversion validation will produce false discrepancy alarms and invalid CPA analysis.
