# 목차
- [Act with Prudence](#act-with-prudence)
- [Apply Functional Programming principles](#apply-funtional-programming-principles)
- [Ask What Would the User Do?](#ask-what-would-the-user-do)
- [Automate Your Coding Standard](#automate-your-coding-standard)
- [Beauty Is in Simplicity](#beauty-is-in-simplicity)
- [Before You Refactor](#before-you-refactor)
- [Beware the Share](#beware-the-share)
- [The Boy Scout Rule](#the-boy-scout-rule)
- [Check Your Code First Before Looking to Blame Others](#check-your-code-first-before-looking-to-blame-others)
- [Choose Your Tools with Care](#choose-your-tools-with-care)
- [Code in the Language of The Domain](#code-in-the-language-of-the-domain)
- [Code Is Design](#code-is-design)
- [Code Layout Matters](#code-layout-matters)
- [Code Reviews](#code-reviews)  
- [Coding with Reason](#coding-with-reason)


## Act with Prudence

## Apply functional Programming Principles
- Mastery of the functional programming paradigm can greatly improve the quality of the code you write in other contexts.
## Ask What would the User do
- The best way to find out how a user thinks is to wathch one. Ask a user to complete a task using a similar picece of software to what you're devleoping.
- Users try to complete tasks in the same order - and they make the same mistakes in the same places. you should design around that core behavior.
## Auto Your Coding Standard
- Just try to indent a messy class by hand to find out for yourself.
- One reason to format the code in a uniform way is so that nobody can own a picece of code just by formatting it in him or her private way.
- A coding standard should make it easier to work in the project and maintain development speed from the beginning to the end.
## Beauty Is in Simplicty
- Beauty of style and harmony and grace and good rhythm depends on simplicity
  
## Before You Refactor
- the best approach for restructuring starts by taking stock of the existing codebase and the tests wrtten against that code.
- Avoid the temptation to rewrite everything. It is best to reuse ad much code ad possible.
- Many incremental changes are better than on massive change.
- After each development iteration, it is important to ensure that the existing tests pass.
- Personal preferences and ego shouldn't
  get in the way. 
- New technonlogy is an insufficient reason to refactor.
- Restructuring will not always guarantee that the new code will be better. 
## Beware the Share
- The context of these dependencies is critical - had they been localized, the sharing may gave been justified and had some positive value.
## The boy Scout Rule
- Always check a module in cleaner than when you checked it out
- you simply have to make it a little bit better than when you checked it out.
  
## Check your Code First Before Looking to Blame Others
- Given how rare compiler bugs are, you are far better putting your time and energy into finding the error in your code than into proving that the compilier is wrong.
- simplicity of design is paramount.

## Choose your Tools with Care
- My personal strategy to mitigate these problems is to start small by using only the tools that are absolutely necessary.
- I also tend to isolate the external tools from my business domain objects by means of interfaces and layering.
## Code in the language of The Domain
- Making domain concepts explicit in tour code means other programmers can gather the intent of the code much more easily than by trying to retrofit an algorithm into what they understand about a domain.


## Code Is Design
- software design isn't complete until it is validated with a brutal battery of tests
- there is inescapable fact : great designs are produced by great designers dedicating themselves to the mastery of their craft. Code is no different.
## Code Layout Matters
- Easy to scan
- Express layout
- Compact format
## Code Review
- the purpose of code reviews should be to share knowledge and establish common coding guidelines.

## Coding with Reason

- The underlying approach is to divide all the code under consideration into short sections - form a single line, such as a functions call, to blocks of less than 10 lines -and argue about thier correctness.
- A section should be chosen so that at each endpoint, the state of the program(namely, the program counter and the values of all "living" objects) satisfies an easily described property, and so that the functionality of that section(state transformation) is easy to describe as a single task.
  
      - Avoid using goto statements, ad they make remote sections highly interdependent.
      - Avoid using modifiable global variables, as they make all section that use them dependent.
      - Each variable should have the smallest possible scope. For example, a local object can be declared right before its first usage.
      - make objects immutable whenever relevant.
      - Make the code readable by using spacing, both horizontal and vertical - e,g, aligning related structrures and using an empty line to seperate two sections. 
      - Make the code self-documenting by choosing descriptive (but relatively short) neames for objects, types, funtions, etc,
      - If you need a nested section, make it a funtion.
      - Make your funtions short and focused on a single task. The old 24 line limit still apply.
      - Funtions should have few parameters (four is a good upper bound).
      - Each unit of code, from a block to a library, should have a narrow interface. in other words. encapsulation is all - and only - about narrow interfaces.
      - In order to preserve class invariants, usage of setters should be discouraged. 

