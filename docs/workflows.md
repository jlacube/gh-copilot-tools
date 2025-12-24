# Agent Workflow Integration

## Complete Development Lifecycle

The nine agents are designed to work together across the complete development lifecycle:

```
Pre-Planning → Planning → Implementation → Documentation → Maintenance
     ↓            ↓             ↓               ↓              ↓
Idea Scout → Spec Architect → Spec-Kitty  → Retro-Spec → Spec Steward
             Tech Radar       Coding Buddy   Architect    
             Spec Validator                  Retro-Spec
                                             Validator
```

---

## Workflow Scenarios

### Scenario 1: New Greenfield Project (Full Lifecycle)

**Phase 1: Pre-Planning (Days 1-2)**
1. **Idea Scout**: Transform vague idea into validated problem statement
   - Conduct market research and competitor analysis
   - Generate idea brief with solution approaches
   - Output: `idea_brief.md`

**Phase 2: Planning (Days 3-7)**
2. **Tech Radar**: Research technology stack options
   - Evaluate frameworks, libraries, tools
   - Verify versions and compatibility
   - Output: Technology recommendations with pros/cons

3. **Spec Architect**: Design architecture and generate specifications
   - Conduct 5-10 batch questions for requirements
   - Create functional and technical specifications
   - Output: `specs/<feature>/` with comprehensive docs

4. **Spec Validator**: Review specifications before implementation
   - Validate completeness and consistency
   - Identify gaps and ambiguities
   - Output: Validation report with issues to address

**Phase 3: Implementation (Weeks 2-N)**
5. **Spec-Kitty Buddy**: Structured feature development
   - Follow Spec-Kitty workflow with work packages
   - Mandatory 10+ batch Q&A at gates
   - Execute and validate all generated code
   - Output: Implemented features in `.kittify/` structure

6. **Coding Buddy**: Ad-hoc tasks and bug fixes
   - Handle unplanned coding tasks
   - Debug and fix issues
   - Refactor and optimize code
   - Output: Executed code changes with validation

**Phase 4: Maintenance (Ongoing)**
7. **Spec Steward**: Keep specifications synchronized
   - Monitor code-to-spec drift
   - Update documentation as code evolves
   - Track documentation quality metrics
   - Output: Updated specs and quality reports

---

### Scenario 2: Existing Undocumented Codebase

**Phase 1: Reverse Engineering (Week 1-2)**
1. **Retro-Spec Architect**: Analyze codebase and generate specs
   - Discover architecture and patterns
   - Extract features and requirements
   - Generate reverse-engineered specifications
   - Output: `retro-specs/<module>/` with comprehensive docs

2. **Retro-Spec Validator**: Validate generated specifications
   - Verify link integrity (all code references valid)
   - Check coverage completeness
   - Validate technology versions
   - Output: Validation report with gaps prioritized

**Phase 2: Enhancement (Week 3+)**
3. **Spec Architect**: Design new features based on existing architecture
   - Use reverse-engineered specs as context
   - Generate specifications for new features
   - Output: `specs/<new-feature>/` integrated with existing docs

4. **Spec-Kitty Buddy** OR **Coding Buddy**: Implement enhancements
   - Use Spec-Kitty for structured features
   - Use Coding Buddy for smaller changes
   - Output: Implemented features validated

**Phase 3: Ongoing Maintenance**
5. **Spec Steward**: Maintain documentation as code evolves
   - Detect drift between code and specs
   - Update reverse-engineered specifications
   - Track documentation health
   - Output: Synchronized documentation

---

### Scenario 3: Quick Feature Development (No Formal Planning)

**Use Case**: Small feature or bug fix, no comprehensive planning needed

1. **Coding Buddy**: Direct implementation
   - Research-first with 5+ fetch operations
   - Generate and execute code immediately
   - Validate execution before handoff
   - Output: Working code with execution logs

**When to skip planning**: 
- Bug fixes
- Small enhancements to existing features
- Refactoring with clear scope
- Prototypes and experiments

---

### Scenario 4: Technology Evaluation

**Use Case**: Deciding between multiple technology options

1. **Tech Radar**: Comprehensive technology research
   - Compare frameworks/libraries
   - Verify versions and compatibility
   - Research best practices and gotchas
   - Output: Data-driven recommendation report

2. **Spec Architect**: Incorporate chosen tech into specifications
   - Update technical specifications
   - Design architecture using selected stack
   - Output: Updated `technical_spec.md` and `tech_stack.md`

---

### Scenario 5: Specification Quality Assurance

**Use Case**: Ensure specifications are ready for implementation

1. **Spec Validator**: Review forward-engineered specs
   - Validate completeness and consistency
   - Check technical accuracy
   - Ensure implementability
   - Output: Validation report with action items

2. **Retro-Spec Validator**: Validate reverse-engineered specs
   - Verify code references are accurate
   - Check coverage completeness
   - Detect documentation drift
   - Output: Validation report with prioritized gaps

---

## Workflow Decision Tree

**Starting Point: What are you building?**

```
┌─ Vague idea? → Idea Scout → Spec Architect → Spec-Kitty Buddy
│
├─ Clear requirements? → Spec Architect → Spec Validator → Spec-Kitty Buddy
│
├─ Legacy codebase? → Retro-Spec Architect → Retro-Spec Validator → Spec Steward
│
├─ Quick fix/feature? → Coding Buddy
│
├─ Need tech decision? → Tech Radar → Spec Architect
│
└─ Maintain docs? → Spec Steward
```

**During Development: Which agent for what task?**

| Task | Agent | Why |
|------|-------|-----|
| Explore problem space | Idea Scout | Market research, solution brainstorming |
| Research technologies | Tech Radar | Version tracking, ecosystem assessment |
| Create specifications | Spec Architect | Architecture design, comprehensive docs |
| Review specifications | Spec Validator | Quality assurance before implementation |
| Structured development | Spec-Kitty Buddy | Work packages, quality gates, batch Q&A |
| Quick coding tasks | Coding Buddy | Immediate implementation, execution validation |
| Document legacy code | Retro-Spec Architect | Reverse engineering, pattern recognition |
| Validate legacy docs | Retro-Spec Validator | Link integrity, coverage analysis |
| Maintain documentation | Spec Steward | Drift detection, ongoing synchronization |

---

## Agent Handoffs

Agents are designed to produce outputs that serve as inputs for the next agent:

1. **Idea Scout → Spec Architect**
   - Input: Vague idea or problem
   - Output: `idea_brief.md` with problem statement, market analysis, solution approaches
   - Handoff: Spec Architect uses idea brief as context for specifications

2. **Tech Radar → Spec Architect**
   - Input: Technology evaluation request
   - Output: Technology comparison and recommendation
   - Handoff: Spec Architect incorporates tech stack into technical specifications

3. **Spec Architect → Spec Validator**
   - Input: Project or feature concept
   - Output: Comprehensive specifications in `specs/<feature>/`
   - Handoff: Spec Validator reviews for completeness before implementation

4. **Spec Validator → Spec-Kitty Buddy**
   - Input: Specifications to validate
   - Output: Validation report with gaps identified
   - Handoff: Spec-Kitty Buddy implements validated specifications

5. **Retro-Spec Architect → Retro-Spec Validator**
   - Input: Legacy codebase
   - Output: Reverse-engineered specifications in `retro-specs/<module>/`
   - Handoff: Retro-Spec Validator checks accuracy against actual code

6. **Retro-Spec Validator → Spec Steward**
   - Input: Reverse-engineered specifications
   - Output: Validation report with issues prioritized
   - Handoff: Spec Steward sets up ongoing maintenance and monitoring

7. **Any Agent → Coding Buddy**
   - Input: Ad-hoc coding request
   - Output: Implemented and executed code
   - Handoff: No formal handoff, immediate task completion

---

## When NOT to Use Multiple Agents

Direct to **Coding Buddy** for:
- Simple bug fixes with clear root cause
- Small refactoring with obvious scope
- Quick prototypes or experiments
- Single-file changes
- Immediate coding questions

Direct to **Spec Architect** (skip Idea Scout) when:
- Requirements are already clear
- Problem validation is complete
- Time-sensitive projects

Direct to **Spec-Kitty Buddy** (skip Spec Architect) when:
- Specifications already exist
- Following existing patterns
- Extending existing features

---

## Quick Reference Guide

### By Lifecycle Phase

**Pre-Planning**
- **Idea Scout**: Vague problem → Validated solution approach

**Planning**
- **Tech Radar**: Need technology evaluation → Data-driven recommendations
- **Spec Architect**: Clear requirements → Comprehensive specifications
- **Spec Validator**: Have specifications → Quality assurance report

**Implementation**
- **Spec-Kitty Buddy**: Structured development → Work packages with gates
- **Coding Buddy**: Quick coding tasks → Immediate implementation

**Documentation**
- **Retro-Spec Architect**: Legacy codebase → Reverse-engineered specs
- **Retro-Spec Validator**: Have retro-specs → Validation report

**Maintenance**
- **Spec Steward**: Evolving codebase → Synchronized documentation
