# Coding Standards

## API Development Standards
- Use PHP v8.4 features.
- Follow PSR-12 coding standards
- Follow pint.json coding rules.
- Enforce strict types and array shapes via PHPStan.
- Use type hints and return types
- Document classes and methods with PHPDoc
- Use eager loading to avoid N+1 queries
- Implement caching where appropriate
- Avoid DB::; use Model::query() only.
- Avoid as much as possible anything that would lock-in a specific db engine e.g. `LIKE` or `ILIKE`
- app/Http/Controllers
    - No abstract/base controllers.
- app/Http/Requests
    - Use FormRequest for validation.
    - Name with Create, Update, Delete.

## API Response Implementation
- Always use the `ApiResponse` class for all API responses
- Structure responses consistently with message, error flag, data and appropriate HTTP status codes
- Paginate large result sets
- Use Gates and Policies for authorization, using Spatie's Role/Permission Management
- Validate all input data, and always use the validated information, never the raw request input data
- For searching, always use `q` as the search param unless told otherwise.
- Use resource classes for consistent API responses
- For paginated collections, use `ApiResponse::paginatedWithMeta()`
- For single items:
  ```php
  return ApiResponse::make(
      'Item retrieved successfully.',
      new ItemResource($item),
      false,
      Response::HTTP_OK
  );
  ```
- For collections:
  ```php
  return ApiResponse::make(
      'Items retrieved successfully.',
      ItemResource::collection($items),
      false,
      Response::HTTP_OK
  );
  ```

## OpenAPI/Swagger Documentation
- Document all API endpoints with OpenAPI annotations
- Group related endpoints under the same tag
- Include comprehensive request/response examples
- For body documentation, make sure to annotate for both JSON and form-data

## Enum Implementation Guidelines
- Use string-based enums for values exposed in APIs
- Implement a `getName()` method for human-readable labels
- Test enum values, names, and order
