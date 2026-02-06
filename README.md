# Source Control with Power BI & Microsoft Fabric
## Enterprise Guide – PBIP / Git Integration & Deployment Flow

This repository demonstrates a production-ready source control architecture for Power BI using Microsoft Fabric and Git (GitHub or Azure DevOps), based on Power BI Projects (PBIP).

The focus is operational: how reports and semantic models move from local development to Git and then to Fabric workspaces, and how teams collaborate safely using branches, pull requests, and environment isolation.

---

## 1. Why Source Control Matters in Power BI & Fabric

Before PBIP and Fabric Git integration:

- PBIX files were opaque binaries
- Collaboration was fragile
- Rollbacks were manual and risky
- CI/CD was nearly impossible

With PBIP + Git + Fabric:

- Reports and models become structured text assets
- Every change is diffable and reviewable
- Fabric workspaces become deployable environments
- Governance and promotion flows become enforceable

Without PBIP, Power BI is a desktop tool.
With PBIP + Git + Fabric, Power BI becomes an enterprise platform.

---

## 2. High-Level Architecture

At a high level:

- GitHub or Azure DevOps is the system of record
- Power BI Desktop (PBIP) is the local authoring environment
- Microsoft Fabric is the execution and consumption platform
- Pull Requests act as the governance gate

All synchronization relies on standard Git operations.

---

## 3. Prerequisites

- Git
- GitHub or Azure DevOps
- Power BI Desktop (latest version)
- Dataset ![Free Test Dataset](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/tree/fdf424e4c12683e2da8ffbaeef7293fcb1ab5334/data)
- Microsoft Fabric tenant enabled

---

## 4. Repository Setup

Create a new repository in GitHub or Azure DevOps.

This repository will store:

- Power BI report definitions
- Semantic model metadata
- Version history and approvals

Clone the repository locally:

    git clone <repo-url>

This local folder becomes the root of your Power BI project.

---

## 5. Create the Power BI Report

Create your report in Power BI Desktop using either your own data source or the free sample dataset used in this example.

At this stage, development is local only.

---

![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/PBI%20reports.png)

---

## 6. Save as Power BI Project (PBIP)

Save the report inside the cloned repository as a Power BI Project (.pbip).

When saved as PBIP:

- Reports and semantic models are stored as plain text files
- A clear, predictable folder structure is created
- Artifacts are immediately Git-friendly

---

![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/save%20as.png)

---

![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/save%20as%20V2.png)

---

## 7. Push to the Remote Repository

    git add .
    git commit -m "Initial Power BI project"
    git push origin dev

From this point forward, Git becomes the source of truth.

---

## 8. Fabric Workspace Strategy

Create two Fabric workspaces:

- Dev workspace
- Prod workspace

Each workspace represents a deployment boundary.

---

## 9. Configure Git Integration in Fabric

For each workspace:

1. Go to Workspace Settings
2. Open Git integration
3. Connect to GitHub or Azure DevOps

Branch mapping:

- Dev workspace uses the dev branch
- Prod workspace uses the main (or prod) branch

---
![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/Create%20Fabric%20Workspaces.png)
---
![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/workspace%20settings.png)
---
![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/Git%20integration.png)
---
![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/GitHub%20integration%20set%20up.png)
---
## 10. Sync Repository to Fabric

Once connected, sync the workspace.

Fabric will automatically materialize reports and semantic models directly from the repository.

Data refresh and data source configuration are intentionally out of scope.

---

![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/synced%20reports%20from%20remote%20repo.png)

---

![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/all%20reports.png)



---

## 11. End-to-End Flow Validation

Local to Git to Fabric:

1. Modify or create a report locally
2. Save changes as PBIP
3. Commit and push to the dev branch
4. Fabric detects pending changes
5. Sync applies them to the Dev workspace

![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/pending%20changes%20in%20fabric%20after%20PR%20approval.png)
---



---

## 12. Pull Request Flow

1. Open a Pull Request from a dev branch to dev and finally to prod
2. Reviewer validates model and visual changes
3. Approve and merge
4. Sync the Prod workspace

This enforces review gates, ownership, and safe deployments.

![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/vendor%20push.png)

---
![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/PR%20example.png)
---


---

## 13. Bidirectional Sync

The integration works both ways:

- Local to Git to Fabric
- Fabric to Git to Local

Everything is backed by standard Git mechanics.


---

![alt-text](https://github.com/DavidArayaS/Source-Control-with-Power-BI-and-Fabric/blob/19669dbb858f1e11646f0f1dc60cc492403868dd/Pictures/delete%20commit%20options.png)

---

## 14. Note

To interact with the reports exactly in the same way they are created in Power BI Desktop the Dataset has to be imported, that is beyond this guide.

---
## 15. References

Power BI Projects Overview
https://learn.microsoft.com/power-bi/developer/projects/projects-overview

Microsoft Fabric – Git Integration
https://learn.microsoft.com/fabric/cicd/git-integration/intro-to-git-integration

Power BI on-premises data gateway
https://learn.microsoft.com/en-us/power-bi/connect-data/service-gateway-onprem


