## BookStoreApi

Minimal API for managing a MongoDB-backed list of books. The project targets .NET 8 and exposes CRUD endpoints under `/api/books`.

## Prerequisites

- [.NET SDK 8.0+](https://dotnet.microsoft.com/download)
- A running MongoDB instance (default connection string: `mongodb://localhost:27017`)

You can override the database settings in `appsettings.json` or with environment variables:

- `BookStoreDatabase__ConnectionString`
- `BookStoreDatabase__DatabaseName`
- `BookStoreDatabase__BooksCollectionName`

## Running the project

1. Restore dependencies:
   ```bash
   dotnet restore BookStoreApi.sln
   ```
2. Start MongoDB locally (or point the connection string to your cluster).
3. Run the API:
   ```bash
   dotnet run --project BookStoreApi/BookStoreApi.csproj
   ```
4. Open Swagger UI (development only) at `https://localhost:7002/swagger` or `http://localhost:5000/swagger` depending on your ASP.NET Core URLs.

## Testing the endpoints

- Use the included `BookStoreApi/BookStoreApi.http` file with the Visual Studio/VS Code REST client, or issue requests manually. Example:
  ```bash
  curl -X POST "https://localhost:7002/api/books" \
    -H "Content-Type: application/json" \
    -d '{"Name":"The Pragmatic Programmer","Price":42.00,"Category":"Software","Author":"Hunt & Thomas"}'
  ```
  (Adjust the base URL to match the host/port from your `dotnet run` output.)

For more background, see the original tutorial: https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-mongo-app?view=aspnetcore-8.0&tabs=visual-studio
