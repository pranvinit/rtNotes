### Roles in WordPress

#### Commonly used functions

1. `add_role()`: Adds a new role.
    - `$role`: The role name.
    - `$display_name`: The role display name.
    - `$capabilities`: The role capabilities.
  
2. `remove_role()`: Removes a role.
    - `$role`: The role name.

3. `get_role()`: Retrieves a role.
    - `$role`: The role name.

4. `add_cap()`: Adds a capability to a role.
    - `$role`: The role name.
    - `$capability`: The capability name.
    - `$grant`: Whether to grant the capability.

5. `remove_cap()`: Removes a capability from a role.
    - `$role`: The role name.
    - `$capability`: The capability name.

**Note**: The user roles and their capabilities are stored in the `wp_options` table with the option name `wp_user_roles`.