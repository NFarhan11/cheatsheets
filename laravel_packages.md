# Laravel Packages

## Spatie Laravel-Permission

### Installation

```bash
composer require spatie/laravel-permission
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
php artisan migrate
```

### Models Setup

- Add `HasRoles` trait to `User` model.

```php
use Spatie\Permission\Traits\HasRoles;

class User extends Authenticatable
{
    use HasRoles;
}
```

### Creating Roles and Permissions

```php
use Spatie\Permission\Models\Role;
use Spatie\Permission\Models\Permission;

// Create Roles
Role::create(['name' => 'admin']);
Role::create(['name' => 'user']);

// Create Permissions
Permission::create(['name' => 'edit articles']);
Permission::create(['name' => 'delete articles']);
```

### Assigning Roles and Permissions

```php
$user = User::find(1);

// Assign Role
$user->assignRole('admin');

// Assign Permission
$user->givePermissionTo('edit articles');

// Assign Role and Permissions to Role
$role = Role::findByName('admin');
$role->givePermissionTo('edit articles');
$role->givePermissionTo(['edit articles', 'delete articles']);
```

### Checking Roles and Permissions

```php
// Check Role
$user->hasRole('admin'); // true or false

// Check Permission
$user->can('edit articles'); // true or false

// Check Multiple Roles
$user->hasAnyRole(['admin', 'editor']); // true if user has at least one role
$user->hasAllRoles(['admin', 'editor']); // true only if user has all roles
```

### Removing Roles and Permissions

```php
// Remove Role
$user->removeRole('admin');

// Remove Permission
$user->revokePermissionTo('edit articles');

// Remove All Roles
$user->syncRoles([]);

// Remove All Permissions
$user->syncPermissions([]);
```

### Retrieving Data

```php
// Get Roles
$user->getRoleNames(); // Collection of role names

// Get Permissions
$user->getPermissionNames(); // Collection of permission names

// Get Users with Role
User::role('admin')->get();

// Get Users with Permission
User::permission('edit articles')->get();
```

### Middleware

```php
Route::group(['middleware' => ['role:admin']], function () {
    // Only accessible by 'admin' role
});

Route::group(['middleware' => ['permission:edit articles']], function () {
    // Only accessible by 'edit articles' permission
});
```

### Advanced Features

- Wildcards in Permissions

```php
$user->can('articles.*'); // Matches all permissions starting with 'articles.'
```

- **Events**: Listen for permission and role changes:

```php
Spatie\Permission\Events\RoleAssigned
Spatie\Permission\Events\RoleRemoved
Spatie\Permission\Events\PermissionAssigned
Spatie\Permission\Events\PermissionRevoked
```

## Laravel NestedSet

### Setup

1. Migration Example:

```php
Schema::create('categories', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->nestedSet(); // Adds `lft`, `rgt`, `parent_id`, and `depth` columns
    $table->timestamps();
});
```

2. Model Setup with `NodeTrait`:

```php
use Kalnoy\Nestedset\NodeTrait;

class Category extends Model
{
    use NodeTrait;
}
```

### Basic Operations

1. Create a **Root Node**:

```php
Category::create(['name' => 'Root']);
```

2. Create a **Child Node**:

```php
$parent = Category::find(1);
$parent->children()->create(['name' => 'Child Node']);
```

3. Insert Sibling Nodes:

   - After a Node:

   ```php
   $node = Category::find(2);
   $node->insertAfterNode(Category::create(['name' => 'Sibling']));
   ```

   - Before a Node:

   ```php
   $node = Category::find(2);
   $node->insertBeforeNode(Category::create(['name' => 'Sibling']));
   ```

### Tree Queries

1. Get All Root Node:

```php
$roots = Category::whereIsRoot()->get();
```

2. Get All Descendants of a Node:

```php
$descendants = $node->descendants()->get();
```

3. Get Direct Children:

```php
$children = $node->children()->get();
```

4. Get Ancestors of a Node:

```php
$ancestors = $node->ancestors()->get();
```

5. Get Depth:

```php
$depth = $node->depth;
```

### Tree Modifications

1. Move a Node:
   - To Another Parent:
   ```php
   $node->appendToNode($newParent)->save();
   ```
   - As Root:
   ```php
   $node->makeRoot()->save();
   ```
2. Delete a Node whth Descendants:

```php
$node->delete();
```

3. Prune the Tree (Remove Unused Space):

```php
Category::fixTree();
```

### Tree Traversal

1. Flat Array:

```php
$tree = Category::defaultOrder()->get()->toTree();
```

2. Nested Tree Array:

```php
$nestedTree = Category::get()->toTree();
```

3. Flatten Tree or Dropdown:

```php
$flatTree = Category::pluck('name', 'id');
```

### Additional Utilities

1. Check If Node is Root

```php
$isRoot = $node->isRoot();
```

2. Check If Node is Leaf:

```php
$isLeaf = $node->isLeaf();
```

3. Check If Node is Ancestor of Another Node:

```php
$isAncestor = $node->isAncestorOf($otherNode);
```
