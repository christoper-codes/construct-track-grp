# 📂 ConstructTrack-GRP

Government Resource Planning (GRP) system built with **ASP.NET** (backend) and **Vue.js** (frontend).  
It streamlines the management of construction projects and material procurement, ensuring transparency and efficiency in public works.

---

## Features
- **Tender Management**: Models, DTOs, validators, repositories, services, and controllers for handling tenders.  
- **Document Types**: Support for `TenderDocumentType`, `TenderDocumentTypeTender`, and related entities.  
- **Resource Distribution**: Manage allocation of resources across projects.  
- **Funding Sources**: Track and validate tender funding sources.  
- **External API Integration**: Integration with **Dipomex API** for external data.  
- **Smart Refactoring**: Updated namespaces, renamed entities (`ServiceType → AreaServiceType`, `PriceType → TenderPriceType`).  
- **Client Features**: Vue-based frontend with new dependencies and features.  

---

## Tech Stack
- **Backend**: ASP.NET Core (C#)  
- **Frontend**: Vue.js  
- **Database**: Entity Framework Core  
- **API**: RESTful services with DTOs, validators, and repositories  
- **Design Pattern**: Repository Pattern (Parent Repository) for consistent data access and separation of concerns
