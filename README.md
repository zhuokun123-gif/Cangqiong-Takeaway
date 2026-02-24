# Cangqiong-Takeaway -- Golang Implementation

This project provides an initial architectural framework along with its
core design philosophy.

Through this project, you may gain the following knowledge and
experience:

1.  How to choose appropriate design patterns and structure architecture
    in Go Web development.
2.  How to encapsulate Gorm features such as Hook, Transaction, and
    Dynamic SQL, and understand practical use cases of Context in Gorm.
3.  How to design and use RouteGroup to handle complex and dynamic
    middleware loading scenarios.
4.  Practical development best practices and experience.

------------------------------------------------------------------------

## Requirements Documentation

Sky Take-Out (apifox.com)\
https://apifox.com/apidoc/shared-93dd7a4f-adbc-4d2b-b6f5-24976908bc1c

------------------------------------------------------------------------

## Quick Start

1.  Navigate to the web frontend directory and start nginx.exe\
2.  Start Redis\
3.  Start the Golang backend service\
4.  Visit http://localhost

------------------------------------------------------------------------

# Feature Modules

## Admin System

Used internally by restaurant staff.

  -----------------------------------------------------------------------
  Module                       Description
  ---------------------------- ------------------------------------------
  Login / Logout               Staff must log in to access the management
                               backend

  Employee Management          Admin can manage employee information
                               including query, add, edit, disable

  Category Management          Manage dish categories or set meal
                               categories (query, add, edit, delete)

  Dish Management              Maintain dish information (query, add,
                               edit, delete, enable/disable sale)

  Set Meal Management          Maintain combo/set meal information
                               (query, add, edit, delete, enable/disable
                               sale)

  Order Management             Manage user orders from the mobile client
                               (query, cancel, dispatch, complete, export
                               reports)

  Data Statistics              Statistical analysis including revenue,
                               user count, order metrics
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## User System

  -----------------------------------------------------------------------
  Module                       Description
  ---------------------------- ------------------------------------------
  Login / Logout               Integrates with WeChat Mini Program Open
                               API for authentication

  Order -- Menu                Users select dish or set meal categories
                               and browse items accordingly

  Order -- Shopping Cart       Add items to cart (view, add, remove,
                               clear cart)

  Order Payment                Checkout and pay for selected dishes or
                               set meals

  Personal Center              Manage order history and delivery
                               addresses (set default, add, edit, delete)
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Tech Stack

-   Gin -- A lightweight HTTP web framework written in Go.
-   Gorm -- Object Relational Mapping library.
-   go-redis -- Redis client library for Go.
-   go-jwt -- JWT authentication library for Go.
-   GoCron -- Scheduled task library.

------------------------------------------------------------------------

## Environment Requirements

-   MySQL\
-   Redis

------------------------------------------------------------------------

## Run Server

Default (development configuration):

go run main.go

Specify release configuration:

go run main.go --env=release

------------------------------------------------------------------------

## Docker Compose Startup

1.  Clone the project
2.  Create required shared volumes for configuration
3.  Copy configuration files into shared volume
4.  Run docker-compose up -d

------------------------------------------------------------------------

## Project Structure

client/ \# Web client\
common/ \# Common utilities and shared components\
├── e/ \# Custom errors, error codes, messages\
├── enum/ \# Custom enums, constants, variables\
├── utils/ \# Utility functions (JWT, rate limiting, email, generic
tools)\
└── result.go \# Unified response format

config/ \# Configuration files\
global/ \# Global instances (GormDB, RedisClient, Config)\
initialize/ \# Initialization components (gorm, redis, router)\
internal/ \# Core business logic\
├── api/\
├── model/\
├── repository/\
├── router/\
└── service/

logger/ \# Logging management\
middle/ \# Middleware (authentication, authorization, rate limiting)\
script/ \# Initialization and DevOps scripts

go.mod \# Project dependency file\
main.go \# Application entry point

------------------------------------------------------------------------

Reference Implementation Includes:

-   Dashboard\
-   Data Statistics\
-   Order Management\
-   Set Meal Management\
-   Mobile Shopping Cart\
-   Mobile Order History
