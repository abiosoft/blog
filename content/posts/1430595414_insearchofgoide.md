+++
comments = true
date = "2015-05-02T22:56:54+01:00"
draft = false
image = ""
tags = ["go", "golang", "ide", "eclipse", "vim", "atom", "sublime", "intellij"]
title = "In search of Go IDE"
description = "In search of Go IDE"
toc =  false
readTime = true
autonumber = false
+++
One of the early day complaints about Go (after lack of Generics _shhh..._) is unavailability of a proper IDE.
But as time passes, different projects emerged to offer a good coding experience for Go, ranging from basic features like syntax highlighting to wholesale features like intellisense and code refactoring.
The following are my experiences with different Go IDEs.

A moment of appreciation for [gocode](https://github.com/nsf/gocode) and its creator. The project was the beginning of the end of Go's lack of IDE criticism. If you are wondering why, all Go IDEs that I am aware of (except IntelliJ) provides autocomplete via gocode.

### GoClipse
[Installation Instructions](https://github.com/GoClipse/goclipse/blob/latest/documentation/Installation.md#installation) |
[Project Page](https://github.com/GoClipse/goclipse).

GoClipse (an [Eclipse](http://eclipse.org) plugin) is one of the early IDEs for Go. It offers only the essentials and you will be underwhelmed if you are used to what other Eclipse based IDEs offer.

#### Features
* Autocomplete
* Error detection on save
* Project templates
* Jump to definition
* Build and run

#### Drawbacks
* Periodic notable lags
* Feels buggy

### GoSublime
[Installation Instructions](https://github.com/DisposaBoy/GoSublime#installation)
| [Project Page](https://github.com/DisposaBoy/GoSublime)

GoSublime is a very effective and lightweight Go plugin for [Sublime Text](http://sublimetext.com). It was my favourite for a very long time after moving from GoClipse.

#### Features
* Autocomplete
* Error detection as you type
* Jump to definition
* goimports integration
* Status bar info for subject under cursor
* godoc documentation integration
* Minimal terminal simulation
* play.golang.org integration

#### Drawbacks
* You still need the Terminal to run and for more intensive building/testing

### vim-go
[Installation Instructions](https://github.com/fatih/vim-go#install)
| [Project Page](https://github.com/fatih/vim-go)

vim-go is a plugin for Vim. It integrates virtually all available Go tools.
I made a switch from GoSublime without looking back.

#### Features
* Autocomplete
* Jump to definition
* goimports integration
* Status bar info for subject under cursor
* godoc documentation integration
* Source analysis with oracle
* Building, running and testing with coverage
* play.golang.org integration
* Context aware refactor with gorename
* Other go tools (golint, go vet)
* Terminal

#### Drawbacks
* Installation experience was not smooth (Disclaimer: I'm a Vim rookie)

### Go-Plus
[Installation Instructions](https://github.com/joefitzgerald/go-plus#installing)
| [Project Page](https://github.com/joefitzgerald/go-plus)

Go-Plus is a plugin for [Atom](http://atom.io). Unlike my other experiences, I took the time to customize Atom.
I have use cases for both `gofmt` and `goimports` but Go-Plus would only let me use one of them.
To satisfy my needs, I wrote a [plugin](https://atom.io/packages/go-imports) for `goimports`, wrote a [theme](https://atom.io/themes/simplistic-syntax),
changed the autocomplete select key from `tab` to `return` and installed terminal ([term2](https://atom.io/packages/term2)).

Even though the features are limited, the experience is good.

#### Features
* Autocomplete
* Error detection on save
* goimports integration
* Building and testing with coverage
* Context aware refactor with gorename
* Other go tools (golint, go vet)
* Terminal (via another package)

#### Drawbacks
* Atom editor is buggy
* Could do with more features

### IntelliJ
[Installation Instructions](https://github.com/go-lang-plugin-org/go-lang-idea-plugin#pre-release-builds)
| [Project Page](https://github.com/go-lang-plugin-org/go-lang-idea-plugin)

IntelliJ is indisputably my favourite IDE and I would gladly welcome the availability of Go plugin.
The project started a few years back and looks to have hit a dead end. But recently, it got back to active development and has received contributions from official IntelliJ team members.
It offers full IDE features comparable to what IntelliJ offers Java and it is my favourite at the moment.

#### Features
* Full autocomplete (including unimported packages).
* Error detection as you type
* Jump to definition/view source
* Building, running and testing with coverage
* Context aware refactor
* Source analysis
* Auto import/remove packages
* Inbuilt version control tool
* Inbuilt Terminal
* godoc documentation integration
* Scratch files (alternative to play.golang.org)

#### Drawbacks
* Pre-release build, not yet stable


### My Take
I regard Terminal as a feature because it comes handy once in a while and it is a plus if you do not need to leave your IDE to use the terminal.

I will rate the five IDEs in the categories of Ease of Install, Features, Stability and Potential with scores 5 to 1 for the highest ranked to the lowest ranked.

#### Ease of Install
How easy the installation process is.

| Rank | IDE       | Score |
| ---- | --------- | ----- |
| 1    | Go-Plus   | 5     |
| 2    | GoSublime | 4     |
| 3    | GoClipse  | 3     |
| 4    | IntelliJ  | 2     |
| 5    | vim-go    | 1     |

#### Features
The quality of features provided.

| Rank | IDE       | Score |
| ---- | --------- | ----- |
| 1    | IntelliJ  | 5     |
| 2    | vim-go    | 4     |
| 3    | GoSublime | 3     |
| 4    | Go-Plus   | 2     |
| 5    | GoClipse  | 1     |

#### Stability
Which one crashes and lags the least.

| Rank | IDE       | Score |
| ---- | --------- | ----- |
| 1    | GoSublime | 5     |
| 2    | vim-go    | 4     |
| 3    | IntelliJ  | 3     |
| 4    | Go-Plus   | 2     |
| 5    | GoClipse  | 1     |

#### Potential
How much progress would it have made in few years considering the current pace of development and current features.

| Rank | IDE        | Score |
| ---- | ---------- | ----- |
| 1    | IntelliJ   | 5     |
| 2    | vim-go     | 4     |
| 3    | Go-Sublime | 3     |
| 4    | Go-Plus    | 2     |
| 5    | GoClipse   | 1     |

#### Final Ranking
| Rank | IDE       | Score |
| ---- | --------- | ----- |
| 1    | GoSublime | 15    |
| -    | IntelliJ  | 15    |
| 3    | vim-go    | 13    |
| 4    | Go-Plus   | 11    |
| 5    | GoClipse  | 6     |

GoSublime and IntelliJ are joint winners.

What do you think? I know I may not represent your opinion but I should not be far off.
