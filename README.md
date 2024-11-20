# @esmkit/math

The Math namespace object contains static properties and methods for mathematical constants and functions.

## Installation

```bash
npm install @esmkit/math
bun add @esmkit/math
```

## ceil

Computes number rounded up to precision.

This function takes a number and an optional precision value, and returns the number rounded up to the specified number of decimal places.

### Signature

```ts
function ceil(number: number | string, precision: number | string = 0): number;
```

#### Parameters

- `number` (`number | string`): The number to round up.
- `precision` (`number | string`, Optional): The precision to round up to, defaults to `0`.

#### Returns

(`number`): The rounded up number.

### Example

```ts
import { ceil } from '@esmkit/math';

ceil(4.006); // => 5
ceil(6.004, 2); // => 6.01
ceil(6040, -2); // => 6100
```

## clamp

Clamps a number within the inclusive lower and upper bounds.

This function takes a number and two bounds, and returns the number clamped within the specified bounds.
If only one bound is provided, it returns the minimum of the value and the bound.

### Signature

```ts
function clamp(value: number, maximum: number): number;
function clamp(value: number, minimum: number, maximum: number): number;
```

#### Parameters

- `value` (`number`): The number to clamp.
- `minimum` (`number`): The minimum bound to clamp the number.
- `maximum` (`number`): The maximum bound to clamp the number.

#### Returns

(`number`): The clamped number within the specified bounds.

### Examples

```ts
import { clamp } from '@esmkit/math';

const result1 = clamp(10, 5); // result1 will be 5, as 10 is clamped to the bound 5
const result2 = clamp(10, 5, 15); // result2 will be 10, as it is within the bounds 5 and 15
const result3 = clamp(2, 5, 15); // result3 will be 5, as 2 is clamped to the lower bound 5
const result4 = clamp(20, 5, 15); // result4 will be 15, as 20 is clamped to the upper bound 15
```

## floor

Computes number rounded down to precision.

This function takes a number and an optional precision value, and returns the number rounded down to the specified number of decimal places.

### Signature

```ts
function floor(number: number | string, precision: number | string = 0): number;
```

#### Parameters

- `number` (`number | string`): The number to round down.
- `precision` (`number | string`, Optional): The precision to round down to, defaults to `0`.

#### Returns

(`number`): The rounded down number.

### Example

```ts
import { floor } from '@esmkit/math';

floor(4.006); // => 4
floor(0.046, 2); // => 0.04
floor(4060, -2); // => 4000
```

## inRange

Checks if the value is within a specified range.

### Signature

```ts
export function inRange(value: number, maximum: number): boolean;
export function inRange(value: number, minimum: number, maximum: number): boolean;
```

#### Parameters

- `value` (`number`): The value to check.
- `minimum` (`number`): The lower bound of the range (inclusive).
- `maximum` (`number`): The upper bound of the range (exclusive).

#### Returns

(`boolean`): `true` if the value is within the specified range, otherwise `false`.

#### Throws

Throws an error if the `minimum` is greater or equal than the `maximum`.

### Examples

```ts
import { inRange } from '@esmkit/math';

const result1 = inRange(3, 5); // result1 will be true.
const result2 = inRange(1, 2, 5); // result2 will be false.
const result3 = inRange(1, 5, 2); // If the minimum is greater or equal than the maximum, an error is thrown.
```

## mean

Calculates the average of an array of numbers.

If the array is empty, this function returns `NaN`.

### Signature

```ts
function mean(nums: number[]): number;
```

#### Parameters

- `nums` (`number[]`): An array of numbers to calculate the average.

#### Returns

(`number`): The average of all the numbers in the array.

### Examples

```ts
import { mean } from '@esmkit/math';

const numbers = [1, 2, 3, 4, 5];
const result = mean(numbers); // result will be 3
```

## meanBy

Calculates the average of an array of numbers when applying the `getValue` function to each element.

If the array is empty, this function returns `NaN`.

### Signature

```ts
export function meanBy<T>(items: T[], getValue: (element: T) => number): number;
```

#### Parameters

- `items` (`T[]`): An array to calculate the average.
- `getValue` (`(item: T) => number`): A function that selects a numeric value from each element.

#### Returns

(`number`): The average of all the numbers as determined by the `getValue` function.

### Examples

```ts
import { meanBy } from '@esmkit/math';

meanBy([{ a: 1 }, { a: 2 }, { a: 3 }], x => x.a); // Returns: 2
meanBy([], x => x.a); // Returns: NaN
```

## median

Calculates the median of an array of numbers.

The median is the middle value of a sorted array.
If the array has an odd number of elements, the median is the middle value.
If the array has an even number of elements, it returns the average of the two middle values.

If the array is empty, this function returns `NaN`.

### Signature

```ts
function median(nums: number[]): number;
```

#### Parameters

- `nums` (`number[]`): An array of numbers to calculate the median.

#### Returns

(`number`): The median of all the numbers in the array.

### Examples

```ts
import { median } from '@esmkit/math';

const arrayWithOddNumberOfElements = [1, 2, 3, 4, 5];
const result = median(arrayWithOddNumberOfElements); // result will be 3

const arrayWithEvenNumberOfElements = [1, 2, 3, 4];
const result = median(arrayWithEvenNumberOfElements); // result will be 2.5
```

## medianBy

Calculates the median of an array of elements when applying the `getValue` function to each element.

The median is the middle value of a sorted array.
If the array has an odd number of elements, the median is the middle value.
If the array has an even number of elements, it returns the average of the two middle values.

If the array is empty, this function returns `NaN`.

### Signature

```ts
export function medianBy<T>(items: T[], getValue: (element: T) => number): number;
```

#### Parameters

- `items` (`T[]`): An array to calculate the median.
- `getValue` (`(element: T) => number`): A function that selects a numeric value from each element.

#### Returns

(`number`): The median of all the numbers as determined by the `getValue` function.

### Examples

```ts
import { medianBy } from '@esmkit/math';

medianBy([{ a: 1 }, { a: 2 }, { a: 3 }, { a: 4 }, { a: 5 }], x => x.a); // Returns: 3
medianBy([{ a: 1 }, { a: 2 }, { a: 3 }, { a: 4 }], x => x.a); // Returns: 2.5
medianBy([], x => x.a); // Returns: NaN
```

## random

Generate a random number within the given range. The number can be an integer or a decimal.

If only one argument is provided, a number between `0` and the given number is returned.

### Signature

```ts
function random(maximum: number): number;
function random(minimum: number, maximum: number): number;
```

#### Parameters

- `minimum` (`number`): The lower bound for the random number (inclusive).
- `maximum` (`number`): The upper bound for the random number (exclusive).

#### Returns

- (`number`): A random number within the specified range. The number can be an integer or a decimal.

### Examples

```ts
import { random } from '@esmkit/math';

const result1 = random(0, 5); // Returns a random number between 0 and 5.
const result2 = random(5, 0); // If the minimum is greater than the maximum, an error is thrown
const result3 = random(5, 5); // If the minimum is equal to the maximum, an error is thrown.
```

## randomInt

Generate a random integer within the given range.

If only one argument is provided, a number between `0` and the given number is returned.

### Signature

```ts
function randomInt(maximum: number): number;
function randomInt(minimum: number, maximum: number): number;
```

#### Parameters

- `minimum` (`number`): The lower bound for the random integer (inclusive).
- `maximum` (`number`): The upper bound for the random integer (exclusive).

#### Returns

- (`number`): A random integer within the specified range.

### Examples

```ts
import { randomInt } from '@esmkit/math';

const result1 = randomInt(0, 5); // Returns a random integer between 0 and 5.
const result2 = randomInt(5, 0); // If the minimum is greater than the maximum, an error is thrown
const result3 = randomInt(5, 5); // If the minimum is equal to the maximum, an error is thrown.
```

## range

Returns an array of numbers from `start` to `end`, incrementing by `step`.

If `step` is not provided, it defaults to `1`. Note that `step` must be a non-zero integer.

### Signature

```ts
function range(end: number): number[];
function range(start: number, end: number): number[];
function range(start: number, end: number, step: number): number[];
```

#### Parameters

- `start` (`number`): The starting number of the range (inclusive).
- `end` (`number`): The end number of the range (exclusive).
- `step` (`number`): The step value for the range. (default: `1`)

#### Returns

- (`number[]`): An array of numbers from `start` to `end` with the specified `step`.

### Examples

```ts
import { range } from '@esmkit/math';

range(4); // Returns [0, 1, 2, 3]
range(0, 20, 5); // Returns [0, 5, 10, 15]
range(0, 21, 5); // Returns [0, 5, 10, 15, 20]
range(0, -4, -1); // Returns [0, -1, -2, -3]
range(1, 4, 0); // Throws an error: The step value must be a non-zero integer.

```

## rangeRight

Returns an array of numbers from `end` to `start`, decrementing by `step`.

If `step` is not provided, it defaults to `1`. Note that `step` must be a non-zero integer.

### Signature

```ts
function rangeRight(end: number): number[];
function rangeRight(start: number, end: number): number[];
function rangeRight(start: number, end: number, step: number): number[];
```

#### Parameters

- `start` (`number`): The starting number of the range (inclusive).
- `end` (`number`): The end number of the range (exclusive).
- `step` (`number`): The step value for the range. (default: `1`)

#### Returns

- (`number[]`): An array of numbers from `end` to `start` with the specified `step`.

### Examples

```ts
import { rangeRight } from '@esmkit/math';

rangeRight(4); // Returns [3, 2, 1, 0]
rangeRight(0, 20, 5); // Returns [15, 10, 5, 0]
rangeRight(0, 21, 5); // Returns [20, 15, 10, 5, 0]
rangeRight(0, -4, -1); // Returns [-3, -2, -1, 0]
rangeRight(1, 4, 0); // Throws an error: The step value must be a non-zero integer.
```

## round

Rounds a number to a specified precision.

This function takes a number and an optional precision value, and returns the number rounded
to the specified number of decimal places.

### Signature

```typescript
function round(value: number, precision?: number): number;
```

#### Parameters

- `value` (`number`): The number to round.
- `precision` (`number`, optional): The number of decimal places to round to. Defaults to 0.

#### Returns

(`number`): The rounded number.

### Examples

```ts
import { round } from '@esmkit/math';

const result1 = round(1.2345); // result1 will be 1
const result2 = round(1.2345, 2); // result2 will be 1.23
const result3 = round(1.2345, 3); // result3 will be 1.235
const result4 = round(1.2345, 3.1); // This will throw an error
```

## sum

Calculates the sum of an array of numbers.

This function takes an array of numbers and returns the sum of all the elements in the array.

### Signature

```ts
function sum(nums: number[]): number;
```

#### Parameters

- `nums` (`number[]`): An array of numbers to be summed.

#### Returns

(`number`): The sum of all the numbers in the array.

### Examples

```ts
import { sum } from '@esmkit/math';

const numbers = [1, 2, 3, 4, 5];
const result = sum(numbers); // result will be 15
```

## sumBy

Calculates the sum of an array of numbers when applying the `getValue` function to each element.

If the array is empty, this function returns `0`.

### Signature

```ts
export function sumBy<T>(items: T[], getValue: (element: T) => number): number;
```

#### Parameters

- `items` (`T[]`): An array to calculate the sum.
- `getValue` (`(item: T) => number`): A function that selects a numeric value from each element.

#### Returns

(`number`): The sum of all the numbers as determined by the `getValue` function.

### Examples

```ts
import { sumBy } from '@esmkit/math';

sumBy([{ a: 1 }, { a: 2 }, { a: 3 }], x => x.a); // Returns: 6
sumBy([], x => x.a); // Returns: 0
```

## max

Finds the element in an array that has the maximum value.

If the list is empty, returns `undefined`.

### Signature

```typescript
function max<T>(items: [T, ...T[]]): T;
function max(): undefined;
function max<T>(items?: T[]): T | undefined;
```

#### Parameters

- `items` (`T[]`): The array of elements to search.

#### Returns

(`T`): The element with the maximum value.

### Example

```ts
import { max } from '@esmkit/math';

max([1, 2, 3]); // Returns: 3
max(['a', 'b']); // Returns: 'b'
```

## min

Finds the element in an array that has the minimum value.

### Signature

```ts
function min<T>(items: [T, ...T[]]): T;
function min(): undefined;
function min<T>(items?: T[]): T | undefined;
function min<T>(items: T[]): T;
```

#### Parameters

- `items` (`T[]`): The array of elements to search. Defaults to an empty array.

#### Returns

(`T`): The element with the minimum value.

## parseInt

Converts `string` to an integer of the specified radix. If `radix` is undefined or 0, a `radix` of 10 is used unless `string` is a hexadecimal, in which case a `radix` of 16 is used.

### Signature

```typescript
function parseInt(string: string, radix?: number, guard?: unknown): number;
```

#### Parameters

- `string` (`string`): The string to convert to an integer.
- `radix` (`number`, Optional): The radix to use when converting the string to an integer. Defaults to `0`.
- `guard` (`unknown`, Optional): Enables use as an iteratee for methods like `Array#map`.

#### Returns

(`number`): The converted integer.

### Examples

```ts
import { parseInt } from '@esmkit/math';

parseInt('08'); // => 8
parseInt('0x20'); // => 32

parseInt('08', 10); // => 8
parseInt('0x20', 16); // => 32

['6', '08', '10'].map(parseInt); // => [6, 8, 10]
```

## License

MIT © BILLGO.ME
