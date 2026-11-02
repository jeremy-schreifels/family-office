# Family Office AI Skills Repository

This repository contains the prompts, guidelines, schemas, and shared context for a modular AI system. This system manages the operations of a micro family office. The system uses a central Orchestrator to route queries to specialized agent personas.

## Architecture and Routing

The system uses a hub-and-spoke model. The **Orchestrator** is the single point of entry for all user requests. The Orchestrator analyzes intent and routes the task to the correct specialized skill. Each skill operates independently with its own instructions and references.

## Repository Structure

```text
family-office/
├── README.md                       # System overview and routing logic (this file)
├── shared/                         # Global context for all skills
│   ├── family_charter.md           # Core values, mission, and governance principles
│   ├── family_profile.md           # Family members and interests
│   ├── entity_and_tax_map.md       # Anonymized trust, LLC, and corporate hierarchies
│   ├── estate_and_risk_register.md # Insurance and risk information
│   ├── master_balance_sheet.md     # Aggregate financial positions
│   └── operations_vault.md.        # Key advisors, vendors, and stakeholders
│
├── orchestrator/                   # Central routing agent
│   ├── instructions.md             # Intent recognition and delegation logic
│   └── routing_schema.json         # Mapping of intents to specific personas
│
├── tax-estate-advisor/             # Persona: Tax and Estate Strategy
│   ├── instructions.md
│   └── tax_reference.md            # Multi-state residency rules, FBAR/FATCA protocols
│
├── wealthops-manager/              # Persona: Household and Concierge Operations
│   ├── instructions.md 
│   └── maintenance_templates.json  # Real estate upkeep, vendor tracking, travel specs
│
├── cio/                            # Persona: Chief Investment Officer
│   ├── instructions.md
│   └── investment_mandate.md       # Buy box criteria, liquidity rules, portfolio drift
│
└── governance-facilitator/         # Persona: Philanthropy and Family Meetings
    ├── instructions.md
    └── meeting_frameworks.md       # Next-gen education and DAF management protocols

```

## Available Skill Personas

1. **Orchestrator:** The Orchestrator is the main entry point. It receives incoming requests, determines the required expertise, and sends the prompt to the correct persona/skill.
2. **Tax, Estate, and Risk Advisor:** This persona/skill evaluates tax strategies, audits beneficiary designations, manages trust compliance, and reviews insurance coverage.
3. **WealthOps and Concierge Manager:** This persona/skill handles the physical logistics of the family office. These logistics include residence maintenance, vendor coordination, and travel planning.
4. **Chief Investment Officer (CIO):** This persona/skill monitors net worth, models portfolio rebalancing, tracks capital calls, and screens new investments.
5. **Family Governance and Philanthropy Facilitator:** This persona/skill organizes annual family meetings, structures financial education for the next generation, and manages charitable giving workflows.

## Add a New Skill

To add a new specialized capability to the system, do these steps:

1. Create a new directory in the root folder. Name the directory for the skill (for example, `legal-counsel/`).
2. Add a `skill.md` file. This file must define the role, purpose, tone, and rules.
3. Add domain-specific data schemas or markdown references to the folder.
4. Update `orchestrator/routing_schema.json` and `orchestrator/skill.md`. The Orchestrator uses these files to route queries to the new skill.
