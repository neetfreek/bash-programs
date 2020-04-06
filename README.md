# Bash Programs

This is a collection of home-made bash commands I keep in my ~/bin/ directory.

All names begin with a `,` to make finding them more convenient and prevent naming clashes with other programs as per the reasoning provided by [Brandon Rhodes](https://rhodesmill.org/brandon/2009/commands-with-comma/).

## Index

- [Setup](##-setup)
- [Convert Currency](###convert-currency)
- [Search with Duck Duck Go](###-search-with-duck-duck-go)
- [Get the Weather with wttr](###-get-the-weather-with-wttr)

## Setup

A convenient way to set up user-defined commands is to place them in the `~/bin` directory, which in turn you can add to your PATH.

**Step 0:** Clone this repository to your local environment:

```bash
git clone https://github.com/neetfreek/bash-programs.git
```

**Step 1:** Create the `bin` directory:

```bash
mkdir ~/bin
```

**Step 2:** Add the `bin` directory to your PATH in, for example, `~/.profile`, where you'd add the following:

```bash
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.local/bin" ] ; then
     PATH="$HOME/.local/bin:$PATH"
fi
```

**Step 3:** Copy commands into your `~/bin`directory;

... either some:

```bash
cp bash-programs/,ddg ~/bin/,ddg
```

... or all:

```bash
cp bash-programs/* ~/bin/
```

**Step 4:** Change the file system modes (user permissions) for the commands;

... either using numerical modes:

```bash
chmod 744 ,ddg
```

... or using symbolic modes:

```bash
chmod u=rwx ,ddg
```

## Commands

### Convert Currency

Compare exchange rates between a provided currency and Euro (default), or between two provided currencies. Uses the [ECB SDMX 2.1 RESTful web service API](https://sdw-wsrest.ecb.europa.eu/).

Currencies are provided as arguments, formatted in the SP00/ISO 4217 currency reference rate code format (key supplied).

- Requires [xpath](https://manpages.ubuntu.com/manpages/precise/en/man1/xpath.1p.html) be installed in your environment.
- Requires that the `convert-currency-supported-currencies` file be kept in the same directory for printing error and supported currency code messages.

Example 1:

```bash
,convert-currency ZAR
20.3534 ZAR in 1 EUR
```

Example 2:

```bash
,convert-currency ZAR GBP
23.1815 ZAR in 1.00 GBP
```

### Search With Duck Duck Go

Get results from the [Duck Duck Go](https://duckduckgo.com/) search engine for queries in your default browser using terms.

Search terms are provided as arguments.

Example:

```bash
,ddg sights cape town
```

### Get the Weather with wttr

Get the weather for your location or any cities using Igor Chubin's [wttr.in](https://github.com/chubin/wttr.in) service.

If no argument is supplied, your current location is used. Supplying city as an argument will return the weather for that city.

Example 1:

```bash
,wttr
```

Example 2:

```bash
,wttr helsinki
```
