# Competitive Intelligence Suite

## Description
Complete competitive intelligence workflow: market analysis, competitor research, strategic insights, and actionable recommendations

## User Message Template

# Competitive Intelligence Analysis

Business Context: {{business_context}}
{% if competitor_list %}Known Competitors: {{competitor_list}}{% endif %}
Analysis Depth: {{analysis_depth | default("comprehensive")}}

Execute complete competitive intelligence workflow:
1. Market landscape mapping
2. Strategic research planning  
3. Competitive intelligence gathering
4. Strategic analysis and insights
5. Actionable strategy recommendations


## Chain Steps

1. promptId: topic-exploration
   stepName: Market Landscape
   inputMapping:
     business_context: topic
   outputMapping:
     market_overview: landscape

2. promptId: research-planning
   stepName: Research Planning
   inputMapping:
     business_context: topic
     landscape: keyAreas
   outputMapping:
     research_plan: plan

3. promptId: information-gathering
   stepName: Competitive Intelligence
   inputMapping:
     competitor_list: subtopics
     plan: researchPlan
   outputMapping:
     competitive_data: intelligence

4. promptId: critical-analysis
   stepName: Strategic Analysis
   inputMapping:
     intelligence: collectedData
     business_context: topic
   outputMapping:
     strategic_insights: analysis

5. promptId: synthesis-integration
   stepName: Action Planning
   inputMapping:
     analysis: keyInsights
     business_context: topic
   outputMapping:
     action_plan: strategy

