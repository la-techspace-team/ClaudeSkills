---
name: resume-customizer
description: "Intelligent resume customization system that analyzes job descriptions, extracts relevant experience from a resume databank, researches company context, and provides recruiter-perspective feedback. This skill automates the process of tailoring resumes to specific job opportunities with strategic relevance ranking."
license: MIT
---

# Resume Customizer

This skill provides an automated workflow for customizing resumes to specific job opportunities by analyzing job descriptions, extracting relevant experience, researching company context, and providing recruiter feedback.

## Overview

The Resume Customizer follows a systematic 5-step process to create targeted resumes:
1. **Job Analysis** - Parse and understand job requirements
2. **Experience Mining** - Extract relevant projects from resume databank
3. **Company Research** - Investigate company strategy and products
4. **Content Ranking** - Organize and prioritize experience by relevance
5. **Recruiter Analysis** - Provide feedback and gap analysis

## Workflow

### Step 1: Job Description Analysis

**Input Required**: Job listing text (copy-paste or file upload)

**Process**:
```python
# Extract key information from job description
job_analysis = {
    "title": "",
    "company": "",
    "required_skills": [],
    "preferred_skills": [],
    "experience_level": "",
    "key_responsibilities": [],
    "industry": "",
    "department": "",
    "location": ""
}
```

**Analysis Focus**:
- Technical skills and technologies mentioned
- Years of experience required
- Key responsibilities and deliverables
- Company values and culture keywords
- Industry-specific terminology
- Hard vs. soft skill requirements

### Step 2: Resume Databank Processing

**Input Required**: "Resume Databank" document

**Process**:
1. Read and parse the databank document
2. Extract all projects organized by company
3. Identify skills, technologies, and achievements for each project
4. Create searchable project database

**Data Structure**:
```python
projects_db = {
    "company_name": {
        "projects": [
            {
                "title": "",
                "description": "",
                "technologies": [],
                "achievements": [],
                "relevance_keywords": [],
                "impact_metrics": []
            }
        ]
    }
}
```

### Step 3: Company and Industry Research

**Research Targets**:
- Company's current strategic priorities
- Recent product launches or initiatives
- Department-specific goals and challenges
- Industry trends and competitive landscape
- Technology stack and tooling preferences

**Search Queries** (use web_search):
```
1. "{company_name} {department} strategy 2024 2025"
2. "{company_name} products services offerings"
3. "{company_name} technology stack engineering"
4. "{industry} trends {current_year}"
5. "{company_name} recent news initiatives"
```

**Information to Capture**:
- Strategic business priorities
- Technology investments and direction
- Market positioning and competitive advantages
- Growth areas and expansion plans
- Cultural values and work methodology

### Step 4: Relevance Ranking and Content Compilation

**Scoring Algorithm**:

```python
def calculate_relevance_score(project, job_requirements, company_context):
    score = 0
    
    # Technical skill alignment (40% weight)
    tech_match = len(set(project.technologies) & set(job_requirements.required_skills))
    score += tech_match * 0.4
    
    # Responsibility alignment (30% weight)
    resp_keywords = extract_keywords(project.description)
    resp_match = len(set(resp_keywords) & set(job_requirements.key_responsibilities))
    score += resp_match * 0.3
    
    # Company strategic alignment (20% weight)
    strategy_match = len(set(project.relevance_keywords) & set(company_context.priorities))
    score += strategy_match * 0.2
    
    # Impact and scale (10% weight)
    if project.impact_metrics:
        score += 0.1
    
    return score
```

**Output Organization**:
- Rank all projects by relevance score
- Group by company with 2-4 top bullet points per company
- Ensure diverse skill representation
- Maintain chronological coherence

**Bullet Point Formatting**:
```
• [Action Verb] [Specific Achievement] using [Technology/Method] resulting in [Quantified Impact] for [Business Context]
```

### Step 5: Recruiter Analysis and Gap Assessment

**Analysis Framework**:

**Strengths Assessment**:
- Technical skill coverage vs. job requirements
- Experience level alignment
- Industry relevance and transferable skills
- Achievement quality and quantification

**Gap Analysis**:
- Missing technical skills
- Experience level mismatches
- Industry knowledge gaps
- Soft skill deficiencies

**Recruiter Perspective Simulation**:
```
As a recruiter for [Company] hiring for [Position], here's my assessment:

STRENGTHS:
• Strong alignment in: [specific areas]
• Impressive achievements: [highlight 2-3 standout accomplishments]
• Relevant experience: [match to job requirements]

CONCERNS:
• Missing skills: [list critical gaps]
• Experience gaps: [identify areas needing development]
• Questions I'd ask: [potential interview questions about gaps]

RECOMMENDATION: [Pass to interview/Request more info/Pass]
CONFIDENCE LEVEL: [High/Medium/Low]
```

## Implementation Guidelines

### Document Creation
- Create Google Docs version for collaborative editing and sharing
- Generate clean, copy-paste ready text blocks for Canva import
- Maintain consistent formatting across all sections
- Include relevant keywords naturally within bullet points
- Optimize for ATS (Applicant Tracking System) compatibility

### Canva Text Preparation
**Format for easy copy-paste into Canva:**
```
SECTION: EXPERIENCE
COMPANY: [Company Name]
DATES: [Start Date - End Date]
TITLE: [Job Title]

• [Bullet point 1]
• [Bullet point 2]
• [Bullet point 3]
• [Bullet point 4]

---

SECTION: SKILLS
TECHNICAL: [Comma-separated list]
TOOLS: [Comma-separated list]
SOFT SKILLS: [Comma-separated list]

---

SECTION: SUMMARY
[2-3 sentence professional summary tailored to the role]
```

**Text Formatting Guidelines for Canva:**
- Use bullet points (•) for consistency
- Separate sections with clear headers
- Keep line breaks clean and consistent
- Avoid special characters that don't transfer well
- Provide character counts for design space planning

### Research Quality
- Prioritize recent information (last 12-18 months)
- Use authoritative sources (company websites, press releases, industry reports)
- Cross-reference multiple sources for accuracy
- Focus on strategic rather than tactical information

### Content Optimization
- Lead with quantified achievements
- Use industry-standard terminology
- Align language with job description phrasing
- Emphasize transferable skills for career transitions

## Quality Checklist

Before finalizing the customized resume:

**Content Quality**:
- [ ] All bullet points start with strong action verbs
- [ ] Achievements are quantified where possible
- [ ] Technical skills match job requirements
- [ ] No spelling or grammatical errors
- [ ] Consistent tense and formatting

**Strategic Alignment**:
- [ ] Top projects directly address job requirements
- [ ] Company research insights inform content selection
- [ ] Skills gaps are acknowledged and addressed
- [ ] Resume tells a coherent career story

**Canva Design Readiness**:
- [ ] Text blocks are properly separated and labeled
- [ ] Character counts provided for space planning
- [ ] Clean bullet point formatting with consistent symbols
- [ ] No problematic special characters or formatting
- [ ] Section headers clearly marked for easy identification

**Recruiter Review**:
- [ ] Honest assessment of candidate fit
- [ ] Specific, actionable feedback provided
- [ ] Clear recommendation with reasoning
- [ ] Interview preparation guidance included

## Output Deliverables

1. **Customized Resume** (Google Docs format for easy sharing and collaboration)
2. **Copy-Paste Resume Text** (clean, formatted text optimized for Canva design import)
3. **Company Research Summary** (key insights and strategic priorities)
4. **Relevance Analysis** (project rankings with scores and reasoning)
5. **Recruiter Assessment Report** (strengths, gaps, and recommendations)
6. **Interview Preparation Notes** (potential questions and talking points)

## Best Practices

### Research Efficiency
- Start with company official sources
- Use Google search operators for targeted results
- Leverage LinkedIn for recent company updates
- Check industry publications for context

### Content Strategy
- Lead with most relevant experience
- Use reverse chronological order within companies
- Balance technical depth with business impact
- Maintain authenticity while optimizing presentation

### Feedback Quality
- Provide specific, actionable recommendations
- Balance honesty with encouragement
- Include concrete steps for addressing gaps
- Offer interview strategy guidance

This skill transforms resume customization from a manual, time-intensive process into a strategic, research-backed workflow that maximizes relevance and improves interview success rates.
