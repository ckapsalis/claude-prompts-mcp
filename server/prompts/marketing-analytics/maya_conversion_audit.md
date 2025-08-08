# Maya Conversion Audit

## Description
Comprehensive cross-platform conversion analysis identifying setup issues, naming inconsistencies, and platform-specific conversion mapping discrepancies through systematic evaluation

## User Message Template
Execute Maya Conversion Audit for timeframe: {% if timeframe %}{{ timeframe }}{% else %}Last 30 days{% endif %}

{% if min_volume %}Minimum Volume: {{ min_volume }}{% endif %}
{% if value_threshold %}Value Threshold: {{ value_threshold }}{% endif %}  
{% if platforms %}Platforms: {{ platforms }}{% endif %}

## Chain Steps

1. promptId: maya_audit_phase1
   stepName: Setup Health Assessment
   inputMapping:
     timeframe: timeframe
     min_volume: min_volume
     value_threshold: value_threshold
     platforms: platforms

2. promptId: maya_audit_phase2
   stepName: Temporal Activity Analysis
   inputMapping:
     timeframe: timeframe
     min_volume: min_volume

3. promptId: maya_audit_phase3
   stepName: Value Attribution Validation
   inputMapping:
     value_threshold: value_threshold

4. promptId: maya_audit_phase4
   stepName: Cross-Platform Consistency Check
   inputMapping:

5. promptId: maya_audit_facebook
   stepName: Facebook Attribution Analysis
   inputMapping:

6. promptId: maya_audit_deliverables
   stepName: Generate Final Audit Report
   inputMapping:
     timeframe: timeframe
     min_volume: min_volume
     value_threshold: value_threshold
     platforms: platforms

