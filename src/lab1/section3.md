# Assignment

## Guide

Za uspješno odrađivanje vježbe potrebno je kod pushati na stranicu [Github Classroom](https://classroom.github.com/a/reQhmOKi).

Na stranici će pisati 3 stvari:

- potvrda da ste prihvatili zadatak
- link na vaš početni github template
- rok predaje

Nije potrebno kreirati posebnu granu jer se projekt generiara zasebno za svakog studenta.

Promjene dodajete u **master** granu.

**Pull request** ne morate raditi jer je automatski napravljen prema **feedback** grani.

Napravite **commit** kad završite određenu funkcionalnost.

Na primjer:

```bash
git commit "Added GetCompany feature"
git commit "Added DeleteEmployeeForCompany feature"
git commit "Fixed unit test for GetCompany feature"
```

**Projekt se mora pokretati bez error-a !!!**

**Rok predaje je do 4.4 (3.4 do ponoći)**

Provjerite jeste li sve promjene uspješno podigli na stranicu.

**Warning** tretirajte kao **error** kako bi vaš kod bio efikasniji i uredniji.

Feedback s komentarima i bodovanjem ću vam ostaviti na vašem projektu prije idućih vježbi.

## Tasks

Aplikacija treba imati:

1. CRUD operacije za model Company

   - Controller:
     - GetCompany(Guid id)
     - GetCompanyCollection([ModelBinder(BinderType = typeof(ArrayModelBinder))] IEnumerable<Guid> ids)
     - CreateCompany([FromBody] CompanyForCreationDto company)
     - CreateCompanyCollection ([FromBody] IEnumerable<Company> companyCollection)
     - UpdateCompany(Guid id, [FromBody] CompanyForUpdateDto company)
     - DeleteCompany(Guid id)
   - Service:
     - Task<Company> CreateCompanyAsync(Company company);
     - Task<(IEnumerable<Company> companies, string ids)> CreateCompanyCollectionAsync(IEnumerable<Company> companyCollection);
     - Task DeleteCompanyAsync(Guid companyId, bool trackChanges);
     - Task<IEnumerable<Company>> GetByIdsAsync(IEnumerable<Guid> ids, bool trackChanges);
     - Task<Company> GetCompanyAsync(Guid companyId, bool trackChanges);
     - Task UpdateCompanyAsync(Guid companyid, Company companyForUpdate, bool trackChanges);
   - Repository:
     - void CreateCompany(Company company);
     - void DeleteCompany(Company company);
     - Task<IEnumerable<Company>> GetByIdsAsync(IEnumerable<Guid> ids, bool trackChanges);

1. CRUD operacije za model Employee

   - Controller:
     - GetEmployeesForCompany(Guid companyId)
     - GetEmployeeForCompany(Guid companyId, Guid id)
     - DeleteEmployeeForCompany(Guid companyId, Guid id)
     - UpdateEmployeeForCompany(Guid companyId, Guid id, [FromBody] Employee employee)

   * Service:
     - Task DeleteEmployeeForCompanyAsync(Guid companyId, Guid id, bool trackChanges);
     - Task<Employee> GetEmployeeAsync(Guid companyId, Guid id, bool trackChanges);
     - Task<IEnumerable<Employee>> GetEmployeesAsync(Guid companyId, bool trackChanges);
     - Task UpdateEmployeeForCompanyAsync(Guid companyId, Guid id, Employee employee, bool compTrackChanges, bool empTrackChanges);
   * Repository:
     - void CreateEmployeeForCompany(Guid companyId, Employee employee);
     - void DeleteEmployee(Employee employee);
     - Task<Employee?> GetEmployeeAsync(Guid companyId, Guid id, bool trackChanges);
     - Task<IEnumerable<Employee>> GetEmployeesAsync(Guid companyId, bool trackChanges);\*

1. Minimalno 5 Unit testova (po želji birate želite li testirati controller, service ili repository). Testirajte rubne slučajeve.

1. Opcionalno\*: U projektu CompanyEmployees.Shared kreirajte mapu DataTransferObject i kreirajte CompanyDto i EmployeeDto.
1. Opcionalno\*: Kreirajte Custom Exceptions za hvatanje pogrešaka npr. CompanyNotFound, EmployeeNotFound...
