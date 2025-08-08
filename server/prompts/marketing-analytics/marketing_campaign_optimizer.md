# Marketing Campaign Optimizer

## Description
End-to-end campaign optimization workflow: performance analysis, audience insights, creative recommendations, and budget allocation

## User Message Template

# Marketing Campaign Optimization Workflow

Campaign Data: {{campaign_data}}
{% if budget %}Budget: {{budget}}{% endif %}
{% if goals %}Goals: {{goals}}{% endif %}

Execute comprehensive campaign optimization including:
1. Performance analysis and issue identification
2. Deep audience insights and behavior analysis  
3. Creative strategy recommendations
4. Optimal budget allocation planning


## Chain Steps

1. promptId: maya_audit_phase1
   stepName: Performance Analysis
   inputMapping:
     campaign_data: timeframe
   outputMapping:
     performance_issues: issues

2. promptId: deep_research
   stepName: Audience Insights
   inputMapping:
     campaign_data: topic
   outputMapping:
     audience_analysis: insights

3. promptId: advanced_analysis_engine
   stepName: Creative Recommendations
   inputMapping:
     issues: topic
     insights: previous_context
   outputMapping:
     creative_strategy: recommendations

4. promptId: expert_code_implementation
   stepName: Budget Allocation
   inputMapping:
     budget: requirements
     recommendations: refined_query
   outputMapping:
     allocation_plan: final_plan

