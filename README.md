# Typescript code agreement
##### Current state: **In development**
#### Digression
> ##### All information in this repository is used solely by the author and is solely the author's personal opinion. Do not take for granted that the information presented here is the only true information. The author does not claim to have the only correct point of view.


# Chapter - Structure and naming

## Case rules
>- **Files** *- PascalCase `ex: SomeFile.ts`*
>- **Folders** *- PascalCase `ex: ./FolderName/`*
>- **Classes** *- PascalCase `ex: class ClassName {}`*

### Enums
>- **Keys** *- UPPER_CASE_SNAKE_CASE*
>- **Values** *- snake_case*

### Classes
>- **Class name** *- PascalCase*
>- **Properties** *- public/protected: camelCase*
>- **Properties** *- private: _camelCase*
>- **Methods** *- PascalCase*

#### Examples:
>```typescript
>export enum A {
>    KEY: 'some_value'
>}
>```
>```typescript
>class ClassName {
>    // SORT: public/protected/private
>    public a: number = 1;
>    protected b: number = 1;
>    private _c: number = 1;
>
>    // constructor always on top
>    construct() {}
>
>    // SORT: public/protected/private
>    public Method(): void {}
>    protected Method(): void {}
>    private Method(): void {}
>}
>```

## Folder naming
>- **./Details/** - *Any types, interfaces, consts, enums, etc. declaration files*
>- **./Components/** - *Any Cocos components for using in scenes*

## File naming / prefix rules [ Cite ]
>- **C** *- constants*
>- **I** *- interface*
>- **T** *- types*
>- **E** *- enums*
>- **AC** *- abstract class*
#### Examples:
>```typescript
>// ISomeInterface.ts
>export interface ISomeInterface {}
>```
>```typescript
>// CSomeConst.ts
>export const CSomeConst {}
>```
>```typescript
>// ACSomeClass.ts
>export abstract class ACSomeClass {}
>```

#### For information:
> ##### *1. One file must export one value. Bulk exports are not allowed, except in exceptional cases*
> ##### *2. File name and export value must be indent*
---
## Basic project architecture:
> - **App.ts** *- File to connect the core and the game*
> - **./Core** *- Project Core. Pulled from a remote repository*
> - **./Game** *- Game scripts for your fantasies*
> - **./Modules** *- Modules that are pulled from a remote repository*
---
## Module architecture
> - **index.ts** *- Main export file of module*
> - **types.d.ts** *- A file with global types for the project*
> - **./SomeFolders** *- Use naming from `Folder naming`*
> - **./../SomeFile.ts** *- Use naming from `File naming`*

#### For information:
> ##### *1. Include the types.d.ts file with the `/// <reference path="" />` operator.*
> ##### *2. Do not use any `import '../'` constructs inside a module that call files from outside. Only imports within the current module are allowed, as well as the `import 'App.ts'` file. If you want to call files from other libraries, use the appropriate managers from the App/Core file.*
#### Example arch:
>```
>|-App.ts
>|-Core
>| |-index.ts
>| \-types.d.ts
>|-Game
>| |-index.ts
>| \-types.d.ts
>|-Modules
>| \-SomeModule
>|   |-index.ts
>|   |-types.d.ts
>|   |-Details
>|   | |-ISomeInterface.ts
>|   | |-ESomeEnum.ts
>|   |-Components
>|   | |-SomeComponent
>|   | | |-View1.ts
>|   | | \-View2.ts
>|   | \-SomeComponent.ts
>|   \-Controllers
>|     \-Controller.ts
>\-types.d.ts
>```