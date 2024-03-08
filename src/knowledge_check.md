# Knowledge check
Predviđeno vrijeme: 1.5h

Riješite teorijska pitanja i izradite projekt.

Projekt podignite na Github i podijelite link.

## Pitanja

Objasni troslojnu arhitekturu?

Nabroji nekoliko HTTP glagola i navedi za što se koriste.

Što je MVC?

Što je to Middleware?

Što je to Dependency injection?

Koje su opcije dostupne za registriranje servisa?

Što je to ORM?

Koje su karakteristike REST API-ja?

Što je to LINQ i što omogućava?

Što je to SignalR? Navedi nekoliko karakteristika.

## Projekt - EmployeeAPI

Izradite jednostavan EmployeeAPI za dodavanje zaposlenika i tvrtki. Primjer modela:

```csharp
public class Employee
{
	public Guid Id { get; set; }

	public string? Name { get; set; }

	public int Age { get; set; }

	public string? Position { get; set; }

	public Guid CompanyId { get; set; }

	public Company? Company { get; set; }
}

public class Company
{
	public Guid Id { get; set; }

	public string? Name { get; set; }

	public string? Address { get; set; }

	public string? Country { get; set; }

	public ICollection<Employee>? Employees { get; set; }
}
```
Koristite ASP.NET Core Web API template. Za testiranje API-ja koristite Swagger ili Postman.

Aplikacija treba imati:
1. CRUD operacije za model Employee
    * GetEmployees
    * GetEmployeeById
    * CreateEmployee
    * UpdateEmployee
    * DeleteEmployee

1. CRUD operacije za model Company
    * GetCompanies
    * GetCompanyById
    * CreateCompany
    * UpdateCompany
    * DeleteCompany

1. Repository - Service Pattern
1. Seed data
1. Validations

1. Dodatno*: Kod izrade projekta koristite 
    * N-Layer Architecture 
    * CQRS 
    * DTOs