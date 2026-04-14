## Introduction

This file aims to list the instructions for generating the fundamental rules for improving the cursor experience. You must add the `cursor-rules.mdc` and `self-improvement.mdc` files to the root of your project. From these and a series of commands, other new rules will be automatically generated, and you can also create your own if needed.


## Foundational rules

### 1. The Cursor Rules

The first rule you need to add is a rule for Cursor rules themselves. Having this in place will ensure all other rules we make later won't be created in the wrong location and have a good structure.

### 2. The self-improvement rule

The second foundational rule is the self-improvement rule. This actually "teaches Cursor" how to create more rules by itself. It will look at patterns and repeated instructions and create more rules based on that.

### 3. Directory structure rule

This one is a fantastic hack. Basically, you don't want every Cursor chat to half-ass file-listing part of your directories or even worse ― duplicating some of the locations in another directory.

This also "teaches Cursor" what's already implemented, so when you ask it to add a new feature it's better at understanding the context.

```
@cursor-rules.mdc List all source files and folders in the project,
and create a new cursor rule outlining the directory structure and important files and folders.
```

After it does this, you'll want to check a few things:

Ensure that all directories were expanded and the AI was not lazy and wrote [+20 more], ...other directories etc.

Ensure that it didn't include config files or common folders such as .git, that won't be helpful.

Ensure that it captured utilities, shared components and conventions that are not obvious to the AI.

This is gonna be super neat because it's going to eliminate some of the silly mistakes AI sometimes does and prevent it from reinventing the wheel, duplicating code and setup etc.

### 4. Tech stack rule

This is easily the rule that'll reduce most of the mistakes AI makes. You won't have to explain to it what's the latest version of your favorite framework, what's the new way of doing things etc.

```
@cursor-rules.mdc @package.json Analyze all major dependencies
and create a cursor rule outlining the stack of the application
and the versions I'm using, and any remarks on best practices on those versions.
```

If you want to update the dependencies.

```
@cursor-rules.mdc @package.json Analyze all major dependencies
and update the @tech-stack.mdc rule with the latest versions of the dependencies, outlining the best practices for those versions.
```

### 5. Generating rules generically for any file type

With this rule, you can create a cursor rule that will create a generation pattern for any file, component, or structure. Simply attach the file or folder to the command.

For example, creating a React component:

```
@cursor-rules.mdc @components/ui/button.tsx
/Generate Cursor Rules
I want to generate a cursor rule for this React component. Please analyze it carefully and outline all of the conventions found. Output as one rule file only.
```

### 6. Cursor rules for utility functions

You can essentially do this with any single file. Let's take another example and generate a rule for a utility function.

```
@cursor-rules.mdc @utils/base64ToBlob.ts
/Generate Cursor Rules
I want to generate a cursor rule for this utility function.
Analyze it carefully and outline all of the conventions found. Output as one rule file only.
```

## Final considerations

Always use your best files as a reference when creating rules. Because AI will extract patterns and write them down much better than you could.

To generate other cursor rule generators, the following pattern must be followed:

1. Attach the relevant file(s)
2. /Generate Cursor Rules
3. Describe what you want analyzed

You can improve rule generation by being more specific, for example:

- "Identify the testing patterns"
- "Focus on the error handling patterns"
- "Look at the styling approach"
- "Extract the TypeScript conventions"

### Creating a reference for other rules

You can make rules reference each other. At the bottom of a rule file, you might see:

```
Follow @cursor-rules.mdc for proper rule formatting and structure.
````

If you open a rule file in TextEdit/Notepad, you can see that Cursor references the cursor-rules.mdc with some sort of internal link:

```
Follow [cursor-rules.mdc](mdc:.cursor/rules/cursor-rules.mdc) for proper rule formatting and structure.
```

You can also add these internal links yourself, but there's a catch. It seems like typing them in Cursor doesn't create the link. You can either ask in chat to create the link for you, or you can open the rule outside of Cursor to manually add the link.

### Scaling to large codebases and monorepos

In larger codebases or monorepos, you might want to group these rules under directories representing a certain domain.
You should also change the rules from Always (attach) to Auto attached and pass a glob pattern that matches e.g. your backend files.

For example, you might have these directories:

```
.cursor/rules/
├─── frontend-components
│   ├─── landing-components.mdc
│   ├─── newsletter-components.mdc
│   ├─── pricing-components.mdc
│   ├─── ...
├─── backend-services
│   ├─── api-routes.mdc
│   ├─── database-queries.mdc
│   ├─── ...
│─── self-improvement.mdc
│─── project-structure.mdc
│─── cursor-rules.mdc
```

By the way, absolutely share these rules when working with a larger team on the same codebase.

Since they're based on actual code patterns, they serve as living documentation of your team's coding standards.

### Common mistakes when generating Cursor rules

Over-generating rules
Don't create a rule for every single file. Focus on:

- Patterns that repeat across multiple files
- Common sources of bugs or confusion
- Framework-specific best practices
- Team coding standards

### Rules that are too specific

Avoid rules that are so specific they only apply to one file. Good rules should be general enough to apply to multiple similar situations.

### Always have excellent rules

Don't create too many rules that are of poor quality, don't cover major cases, or are irrelevant.