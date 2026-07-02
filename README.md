# chollometro-cli

Small self-contained CLI for reading public Chollometro listing and deal pages.

It uses `uv` inline script dependencies and BeautifulSoup, so there is no project setup beyond having `uv` installed.

## Installation

Install `uv` first:

```bash
brew install uv
```

Or on Linux/macOS without Homebrew:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Install the CLI:

```bash
mkdir -p ~/.local/bin

curl -L https://raw.githubusercontent.com/YOUR_USER/chollometro-cli/main/chollometro \
  -o ~/.local/bin/chollometro

chmod +x ~/.local/bin/chollometro
```

Make sure `~/.local/bin` is in your `PATH`:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

Then run:

```bash
chollometro popular --limit 10
```

## Usage

```bash
./chollometro popular --limit 10
./chollometro most-voted --limit 10
./chollometro new --limit 10
./chollometro featured --limit 10
./chollometro home --limit 10
```

Direct URLs also work:

```bash
./chollometro "https://www.chollometro.com/populares" --limit 5
./chollometro "https://www.chollometro.com/ofertas/epic-games-regala-river-city-girls-2-jueves-2-1928068"
```

JSON output:

```bash
./chollometro popular --limit 10 --json
./chollometro deal "URL" --json
```

Shorten long deal descriptions:

```bash
./chollometro deal "URL" --max-description 700
```

## Parsed fields

Listing pages:

- title
- URL
- current price
- previous price
- discount percent
- temperature
- merchant
- comments count
- thread ID

Deal pages additionally parse:

- description
- link host
- visit URL
- updates metadata

Comment bodies are not embedded in the static HTML currently fetched by this CLI; only the comment count is available.

## Supported listing shortcuts

- `popular` → `https://www.chollometro.com/populares`
- `most-voted` → `https://www.chollometro.com/mas-votados`
- `new` → `https://www.chollometro.com/nuevos`
- `featured` / `home` → `https://www.chollometro.com/`

