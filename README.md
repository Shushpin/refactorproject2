### README для виправленої версії коду

# Програма для управління замовленнями в магазині

Цей проект являє собою відрефакторену версію програми для управління замовленнями в магазині. Вона включає в себе класи `Item`, `Order`, `Store`, `DiscountManager`, `CustomerTypeDiscount`, `OrderBuilder`, а також `Main` клас для демонстрації функціональності.

## Опис класів

### Клас `Item`

Клас для зберігання інформації про товар:
- `name` - назва товару
- `price` - ціна товару
- `quantity` - кількість товару

Методи:
- `calculateTotalPrice()` - розраховує загальну вартість товару

### Клас `Order`

Клас для зберігання інформації про замовлення:
- `items` - список товарів у замовленні
- `customerType` - тип клієнта
- `hasMembership` - чи має клієнт членство
- `hasCoupon` - чи має клієнт купон
- `total` - загальна сума замовлення

Методи:
- `addItem(Item item)` - додає товар до замовлення
- `calculateItemsTotal()` - розраховує загальну суму товарів у замовленні
- `applyDiscount()` - застосовує знижки до замовлення
- `getTotal()` - повертає загальну суму замовлення

### Клас `Store`

Клас для управління замовленнями:
- `orders` - список всіх замовлень

Методи:
- `addOrder(Order order)` - додає замовлення до списку
- `printAllOrders()` - виводить всі замовлення на екран

### Клас `DiscountManager`

Клас для управління знижками:

Методи:
- `applyCustomerTypeDiscount(Order order)` - застосовує знижку залежно від типу клієнта
- `applyMembershipDiscount(Order order)` - застосовує знижку для клієнтів з членством
- `applyCouponDiscount(Order order)` - застосовує знижку для клієнтів з купоном

### Клас `CustomerTypeDiscount`

Абстрактний клас `Discount` та його підкласи для різних типів клієнтів:
- `RegularCustomerDiscount`
- `VIPCustomerDiscount`
- `NewCustomerDiscount`

Методи:
- `applyDiscount(double total)` - застосовує відповідну знижку до загальної суми

### Клас `OrderBuilder`

Клас для створення об'єктів `Order` з використанням паттерну будівельника:

Методи:
- `withCustomerType(String customerType)` - встановлює тип клієнта
- `withMembership(boolean hasMembership)` - встановлює наявність членства
- `withCoupon(boolean hasCoupon)` - встановлює наявність купона
- `addItem(Item item)` - додає товар до замовлення
- `build()` - створює об'єкт `Order`

### Клас `Main`

Головний клас для демонстрації роботи програми. Він створює кілька замовлень і виводить їх на екран.

## Виправлені проблеми та переваги

### Long Method

Метод `calculateTotal()` був розбитий на декілька менших методів (`calculateItemsTotal()` та `applyDiscount()`), що зробило код більш зрозумілим та підтримуваним.

### Feature Envy

Логіка знижок була винесена в окремий клас `DiscountManager`, що зменшило залежність між класами та покращило розподіл обов'язків.

### Inappropriate Intimacy

Клас `Order` більше не містить логіки знижок, що зменшило його складність та покращило підтримуваність.

### Primitive Obsession

Тип клієнта тепер обробляється через класи `CustomerTypeDiscount` та його підкласи, що зменшило використання магічних рядків.

### Shotgun Surgery

Логіка знижок тепер зосереджена в класі `DiscountManager`, що зменшило кількість місць у коді, які потрібно змінювати при оновленні логіки.

### Duplicate Code

Логіка знижок була централізована в класі `DiscountManager`, що зменшило дублювання коду.

### Data Clumps

Поля `customerType`, `hasMembership` та `hasCoupon` були об'єднані в об'єкти `Order`, що зменшило повторюваність коду.

### Large Class

Логіка знижок була винесена з класу `Order`, що зменшило його розмір та зробило його більш зрозумілим.

### Temporary Field

Поле `total` тепер розраховується лише один раз при створенні замовлення, що підвищило ефективність.

### Data Class

Клас `Item` тепер має метод `calculateTotalPrice()`, що зробило його більш об'єктно-орієнтованим.

## Висновок

Відрефакторений код є більш структурованим, логічно розподіленим по класах з чіткими зонами відповідальності. Це покращило читабельність, підтримуваність та розширюваність коду, що значно спрощує майбутню роботу з ним.
