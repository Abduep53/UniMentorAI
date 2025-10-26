# UniMentorAI Model Card

## Model Details

**Model Name**: UniMentorAI Recommendation Engine  
**Version**: 1.0  
**Date**: 2025-01  
**Developed By**: Neuro League  
**Language**: English (primary), multilingual support in development

## Intended Use

**Primary Use Cases**:
- University recommendation for international students
- Admission probability estimation
- Academic profile evaluation
- Scholarship matching
- Application timeline planning
- Essay analysis and feedback

**Intended Users**:
- High school students (11th-12th grade)
- Gap year students
- International students
- University transfer applicants
- Educational advisors and counselors

**Out-of-Scope Use**:
- Not a replacement for official university consultation
- Not a guarantee of admission outcomes
- Not suitable for children under 13
- Not designed for postgraduate applications (yet)

## Model Architecture

**Components**:
- **Language Model**: OpenAI GPT-3.5-turbo
- **Matching Algorithm**: Multi-factor scoring system
- **Prediction Engine**: Historical data regression models
- **Profile Scorer**: Weighted factor analysis

**Input Types**:
- Academic metrics (GPA, SAT, ACT, IELTS, TOEFL)
- Personal information (demographics, nationality, age)
- Academic interests (intended major, career goals)
- Extracurricular activities and achievements
- Financial constraints (budget ranges)
- Geographic preferences

**Output Types**:
- University recommendations with match percentages
- Admission probability estimates
- Personal profile scores
- Scholarship opportunities
- Essay analysis and feedback
- Application timelines

## Training Data

**Data Sources**:
- University official websites (1,500+ institutions)
- QS World University Rankings 2024-2025
- Times Higher Education World University Rankings
- U.S. News & World Report rankings
- Historical admission data (aggregated, anonymized)
- Public scholarship databases

**Coverage**:
- **Geographic**: 115+ countries
- **Institutional**: 1,500+ universities
- **Academic**: All major fields of study
- **Time Period**: 2020-2025 admission cycles

**Data Limitations**:
- Historical data may not predict future trends
- University requirements change annually
- Rankings updated annually
- International data availability varies by region

## Performance Metrics

**University Matching**:
- User satisfaction with recommendations: High (based on feedback)
- Recommendation relevance: Validated through outcome tracking
- Accuracy: Continuous improvement through user feedback

**Admission Prediction**:
- Calibration: Aligned with actual outcome patterns
- Discrimination: Good separation between likely and unlikely admits
- Confidence intervals: Provided with all predictions

**Essay Analysis**:
- Grammar detection accuracy: High (validated against known errors)
- Style consistency: Human evaluators validate AI assessments
- Feedback helpfulness: User-reported improvement scores

**Limitations**:
- Cannot account for all admission factors (essays, interviews, etc.)
- Based on historical patterns that may shift
- Probabilistic estimates, not deterministic predictions

## Ethical Considerations

**Fairness**:
- Recommendations based solely on academic merit and stated preferences
- No bias based on protected characteristics
- Geographic diversity in recommendations
- Economic accessibility considered

**Transparency**:
- Explainable reasoning for all recommendations
- Clearly stated confidence levels
- Disclaimers about limitations and uncertainties
- Open about AI usage and model versions

**Privacy**:
- Minimum necessary data collection
- GDPR compliant processing
- Secure data storage
- User control over data deletion
- No unauthorized data sharing

**Human Oversight**:
- AI provides suggestions, users make final decisions
- No automated admission decisions
- Human review of sensitive recommendations
- Escalation process for edge cases

## Safety & Reliability

**Failures & Limitations**:
- May recommend universities with changing requirements
- Cannot predict scholarship availability changes
- May not account for unique personal circumstances
- Essay analysis is supplemental, not authoritative

**Mitigations**:
- Regular data updates (quarterly)
- Clear disclaimers on all outputs
- "Get second opinion" messaging
- Encouragement of independent verification

**Robustness**:
- Handles missing data gracefully
- Provides fallback recommendations
- Multiple recommendation algorithms
- A/B tested for consistency

## User Instructions

**How to Use**:
1. Create accurate profile with honest information
2. Review recommendations with necessary context
3. Verify information independently
4. Consult with counselors for major decisions
5. Use predictions as one factor among many

**Appropriate Expectations**:
- Guidance, not guarantees
- Probabilistic estimates
- Suggestions to complement (not replace) research
- Tools to enhance, not automate, application process

## Limitations & Known Issues

**Accuracy Limitations**:
- Cannot predict holistic admission reviews
- Doesn't account for legacy, athletic, or special consideration admissions
- Essay evaluation is subjective supplement to human review

**Coverage Gaps**:
- Some universities have incomplete data
- New universities may not be in database immediately
- Regional-specific requirements may vary

**Technical Constraints**:
- Requires internet connection
- May experience latency during high traffic
- Mobile optimization in progress

## Future Improvements

**Planned Enhancements**:
- Expanded university coverage (target: 2,000+)
- Multi-language support
- Mobile app development
- Enhanced essay templates and examples
- Video interview preparation
- Alumni network integration

**Model Updates**:
- Quarterly data refresh
- Continuous algorithm refinement
- User feedback integration
- Improved prediction calibration

## Contact & Support

**Questions About Models**:
- Email: neuroleague.ai@gmail.com
- Website: https://unimentorai.com

**Privacy Concerns**:
- privacy@unimentorai.com
- Data deletion requests processed within 30 days

**Feedback**:
- Use in-app feedback mechanisms
- Contact support for feature requests
- Report issues through help desk

## Disclaimers

**No Guarantee**:
These AI models provide probabilistic guidance based on historical data and pattern recognition. They do not guarantee admission outcomes, which depend on numerous factors including essays, interviews, letters of recommendation, and institutional priorities that cannot be fully modeled.

**Independent Verification**:
Users should verify all information independently and consult with qualified counselors before making major decisions. UniMentorAI is a tool to enhance, not replace, the application process.

**Continuous Improvement**:
Models are updated regularly based on new data and feedback. Users should check for updates and understand that recommendations may change as data and algorithms evolve.

