# TypeScript泛型进阶

## 基本泛型
```typescript
function identity<T>(arg: T): T {
    return arg;
}
```

## 约束泛型
```typescript
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}
```

## 条件类型
```typescript
type IsString<T> = T extends string ? true : false;
type Flatten<T> = T extends Array<infer U> ? U : T;
```

## 映射类型
```typescript
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
};

type Partial<T> = {
    [P in keyof T]?: T[P];
};
```

## 工厂模式
```typescript
function createStore<S>(initialState: S) {
    let state = initialState;
    return {
        getState: () => state,
        setState: (newState: S) => { state = newState; }
    };
}
```

---
*更新时间: {DATETIME_STR}*
