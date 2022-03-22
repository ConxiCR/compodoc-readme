# Compodoc
<p align="left"> 
  <img src="https://avatars3.githubusercontent.com/u/23202313" alt="Compodoc: The missing documentation tool for your Angular application" width="50">
  <b>To do documentation easy to be maintained.</b>
</p>

[Official Documentation. Compodoc.app](https://compodoc.app/)
 
[Official Github](https://github.com/compodoc/compodoc)
 
 
 
 

  

### Checked if:
- **npm is installed** if not installed - `npm install`
- **tsconfig.app.json** is installed after installation

## Installation:

**Global installation:**

- Install from npm : `npm install -g @compodoc/compodoc`
- If you use PowerShell on Windows, add quotes : `npm install -g "@compodoc/compodoc"`

**Local installation:**

- Install with Angular CLI : `ng add @compodoc/compodoc` (npm scripts + special tsconfig.doc.json file will be created.)
- or directly:  `npm install --save-dev @compodoc/compodoc`



## Define a script task for it in your package.json:

    "scripts": {
        "compodoc": "npx compodoc -p tsconfig.doc.json"
    }   

## Run Compodoc: 

><h3>npm run compodoc</h3>

=>Create a directory called `documentation`

### Principals Flags we need:

- `-d`- Where to store the generated documentation

- `-o`- Open the generated documentation
- `-s`- Serve generated documentation (default http://localhost:8080/)
- `-w`- Watch source files after serve and force documentation rebuild
- `-n`- Title of the documentation
- `--theme`- Choose one of available themes, default is 'gitbook' (laravel, original, material, postmark, readthedocs, stripe, vagrant)
- `--hideGenerator` - Do not print the Compodoc logo at the bottom of the page
- [Others Flags options:](https://compodoc.app/guides/options.html)

## result

><h4>"compodoc": "npx compodoc -p tsconfig.doc.json -o -s -w --theme material -n \"Title of the documentation\" --hideGenerator"</h4>

## Documentation form

### Comments (inside .ts files)

Compodoc use Typescript AST parser and it's internal APIs, so the comments have to be JSDoc comments :

    /**
    *
    **/

### 
`@deprecated` Deprecated description

    /**
    * This is my class
    * @deprecated This class is deprecated
    */
    class MyClass {}
`@returns` {Type} Description

    /**
    * @param {string} target  The target to process
    * @returns The processed target number
    */
    function processTarget(target:string):number;
`@ignore, @internal`
These tags indicate that a symbol in your code should never appear in the documentation.

@ignore works inside a class, component or injectable, but also for the entire component.

    /**
    * @ignore
    */
    @Component({
        selector: 'app-root',
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.css'],
    })
    export class AppComponent {}
    /**
    * Footer component
    */
    @Component({
        selector: 'the-footer',
        templateUrl: './footer.component.html',
        styleUrls: ['./footer.component.css'],
    })
    export class FooterComponent {
        /**
        * @ignore
        */
        ignoredProperty: string;

        /**
        * @ignore
        */
        @Input() ignoredInput: string;

        /**
        * @ignore
        */
        @Output() ignoredOutput;

        /**
        * @ignore
        */
        ignoredFunction() {}
    }
`@param` {Type} Name Description

    /**
    * @example
    * This is a good example
    * processTarget('yo')
    *
    * @param {string} target  The target to process see {@link Todo}
    * @returns The processed target number
    */
    function processTarget(target:string):number;

`@link` : you can use these three syntax like JSDoc:
    //for an internal reference

{@link Todo}
[Todo]{@link Todo}
{@link Todo|TodoClass}

Anchors are supported : [Todo]{@link Todo#myproperty}

//for an external link

    [Google]{@link http://www.google.com}
    {@link http://www.apple.com|Apple}
    {@link https://github.com GitHub}

@example : for giving an example on directives, components and pipes decorators, use @example or markdown :
INDENTATION WARNING : TypeScript has an internal margin for new lines, if you want to keep a level of indentation, put a minimum of 13 space characters like in the next example.









