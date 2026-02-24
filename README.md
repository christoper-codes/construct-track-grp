# ConstructTrack-GRP

Government Resource Planning (GRP) system for managing construction projects and material procurement.  
Built with **ASP.NET Core 8** (backend) and **Vue 3 + Vite** (frontend), it ensures transparency and efficiency in public works.

---

## Repository Structure

```
construct-track-grp/
├── manage-grp.Server/   # ASP.NET Core 8 Web API (C#)
├── manage-grp.client/   # Vue 3 + Vite frontend (TypeScript)
└── manage-grp.sln       # Visual Studio solution file
```

### `manage-grp.Server/`
RESTful API built with ASP.NET Core 8. Includes:
- Controllers, DTOs, Domain models, and Entity Framework Core data access
- Repository pattern for consistent data access and separation of concerns
- JWT authentication via `Microsoft.AspNetCore.Authentication.JwtBearer`
- FluentValidation for request validation
- Swagger/OpenAPI documentation (available at `/swagger` in Development)
- Integration with the **Dipomex API** for state/municipality data

### `manage-grp.client/`
Single-page application built with Vue 3, Vite, and Vuetify. Includes:
- Vue Router, Pinia state management, and Vee-Validate forms
- Tailwind CSS + Vuetify component library
- Axios for HTTP communication with the backend

---

## Prerequisites

| Tool | Version | Notes |
|------|---------|-------|
| [.NET SDK](https://dotnet.microsoft.com/download) | 8.x | Required for the backend |
| [Node.js](https://nodejs.org/) | 18+ (LTS) | Required for the frontend |
| SQL Server | Any recent version | Local or remote instance |

---

## Setup & Run

### 1. Clone the repository

```bash
git clone https://github.com/christoper-codes/construct-track-grp.git
cd construct-track-grp
```

### 2. Configure the backend

Copy or edit `manage-grp.Server/appsettings.json` and update the connection string and JWT settings for your environment (see [Configuration](#configuration) below).

### 3. Apply database migrations

```bash
cd manage-grp.Server
dotnet ef database update
```

### 4. Run the backend

```bash
# From manage-grp.Server/
dotnet run
```

The API will be available at `https://localhost:7083` (HTTPS) or `http://localhost:5253` (HTTP).  
Swagger UI is available at `https://localhost:7083/swagger` when running in Development mode.

### 5. Install frontend dependencies

```bash
cd manage-grp.client
npm install
```

### 6. Run the frontend

```bash
npm run dev
```

The client dev server starts on `https://localhost:50232` by default.

> **Tip:** When using Visual Studio or `dotnet run` from the solution root, the SPA proxy launches the frontend automatically alongside the backend.

### Build for production

```bash
# Frontend
cd manage-grp.client
npm run build   # Output in manage-grp.client/dist/
```

---

## Configuration

### Backend — `manage-grp.Server/appsettings.json`

| Key | Description |
|-----|-------------|
| `ConnectionStrings:Connection` | SQL Server connection string |
| `JWT:Audience` | Expected JWT audience — update to match your server URL |
| `JWT:Issuer` | JWT issuer — update to match your server URL |
| `JWT:IssuerSigningKey` | Secret key used to sign/validate JWT tokens |
| `Dipomex:APIKEY` | API key for the Dipomex states/municipalities API |

Environment-specific overrides go in `appsettings.Development.json` (already gitignored for secrets).  
For production secrets, use [.NET User Secrets](https://learn.microsoft.com/aspnet/core/security/app-secrets) or environment variables.

### Frontend — `manage-grp.client/.env`

Create a `.env` file in `manage-grp.client/` to override Vite environment variables as needed (e.g., backend API base URL).

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | ASP.NET Core 8, C#, Entity Framework Core 9, SQL Server |
| Frontend | Vue 3, Vite, TypeScript, Vuetify 3, Pinia, Vue Router |
| Auth | JWT Bearer tokens |
| Validation | FluentValidation (server), Vee-Validate + Yup (client) |
| API Docs | Swagger / OpenAPI (Swashbuckle) |
