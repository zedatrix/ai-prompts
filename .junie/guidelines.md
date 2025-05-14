# ROWS Backend Developer Guidelines

## Project Overview
ROWS is a labor management solution that streamlines the employee lifecycle from recruitment to payroll and compliance. Developed with insights from the healthcare industry, it unifies all aspects of workforce management to eliminate inefficiencies, reduce errors, and ensure compliance.

## Tech Stack
- **Framework**: Laravel 12 (PHP)
- **Database**: PostgreSQL
- **Caching**: Redis
- **Development Environment**: Laravel Sail (Docker)
- **Authentication**: Laravel Sanctum
- **API Documentation**: Swagger/OpenAPI
- **Testing**: Pest/PHPUnit
- **Role/Permission Management**: Spatie Permission
- **Search**: Laravel Scout

## Project Structure & Architecture
- Stick to existing structure-no new folders.
- No dependency changes without approval.

## Running Tests & Finalizing
- To run individual tests (which you should always do when working on tests or fixing them, as opposed to running the full suite to save time), you can use this command:`./vendor/bin/sail test tests/Unit/YourTestFile.php`
When you are finished and want to run the last set of tests before completing your work:
- Check models: `./vendor/bin/sail artisan models:check-imports`
- Run pint: `./vendor/bin/sail php ./vendor/bin/pint`
- Run larastan: `./vendor/bin/sail php ./vendor/bin/phpstan analyse`
- Run all tests: `./vendor/bin/sail artisan test --coverage --parallel --processes=8`

## Testing
- Always aim for 100% code coverage for new features
- Write only unit tests, not feature tests
- Prefer real tests over mocks when possible
- Generate a {Model}Factory with each model.
- Don't remove tests without approval.
- Ensure your tests cover error conditions and edge cases.
