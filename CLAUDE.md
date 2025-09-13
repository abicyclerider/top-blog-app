# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Setup and Server
- `bin/setup` - Initial setup of the application
- `bin/dev` or `bin/rails server` - Start the development server
- `bundle install` - Install Ruby dependencies

### Database
- `bin/rails db:create` - Create the database 
- `bin/rails db:migrate` - Run database migrations
- `bin/rails db:rollback` - Rollback database migrations
- `bin/rails db:test:prepare` - Prepare test database

### Testing and Quality
- `bin/rails test` - Run all tests except system tests
- `bin/rails test:system` - Run system tests
- `bin/rails test:db` - Reset database and run tests
- `bin/rubocop` - Run Ruby linting (Rubocop with Rails Omakase style)
- `bin/brakeman` - Run security vulnerability scanning

## Architecture and Structure

This is a Rails 8.0 application named TopBloggApp using:

### Key Technologies
- **Rails 8.0.2+** with modern defaults
- **Ruby 3.3.5** (specified in .ruby-version)
- **SQLite3** for database
- **Puma** web server
- **Hotwire** (Turbo + Stimulus) for frontend interactivity
- **Propshaft** for asset pipeline
- **Importmap** for JavaScript module management

### Solid Suite Integration
Uses Rails' "Solid" suite for caching and background jobs:
- **Solid Cache** - Database-backed Rails.cache
- **Solid Queue** - Database-backed Active Job
- **Solid Cable** - Database-backed Action Cable

### Code Quality Tools
- **Rubocop Rails Omakase** - Ruby styling (configured in .rubocop.yml)
- **Brakeman** - Security vulnerability scanning
- **Debug gem** - Debugging in development/test

### Current Application State
- Basic Rails application with an `ArticlesController` 
- Route configured: `GET /articles` → `articles#index`
- Uses standard Rails MVC structure
- Test suite configured with parallel test execution
- Deployment ready with Docker support (Kamal + Thruster)

### Testing Framework
- Uses Rails' built-in testing framework (Minitest)
- System testing with Capybara and Selenium WebDriver
- Parallel test execution enabled
- Test files located in `test/` directory

## Development Workflow Notes

- Run `bin/rubocop` before committing to ensure code style compliance
- Use `bin/brakeman` to check for security issues
- The application follows Rails conventions - prefer Rails generators for new components
- Docker deployment is configured with Kamal - see config/deploy.yml