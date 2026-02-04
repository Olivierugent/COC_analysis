# Clash of Clans Clan Analyzer 🏰

A comprehensive Python tool for analyzing Clash of Clans clan data with an interactive Streamlit dashboard.

## Features

- **Clan Overview**: View clan info, level, war stats, and member count
- **Member Analysis**: Detailed breakdown of all clan members
- **Rush Detection**: Identifies rushed players by comparing levels to previous TH max
- **War Performance**: Historical attack tracking for regular wars and CWL
- **CWL Analysis**: Per-round breakdown with attack direction analysis
- **Interactive Dashboard**: Beautiful Streamlit web interface with charts and filters

## Screenshots

![Dashboard Preview](screenshots/dashboard.png)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/YOUR_USERNAME/coc-clan-analyzer.git
cd coc-clan-analyzer
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Get your API token from [Clash of Clans Developer Portal](https://developer.clashofclans.com/)

4. Update the API token in `clan_analyzer.py` and `streamlit_app.py`

## Usage

### Command Line Analysis
```bash
python clan_analyzer.py
```

### Streamlit Dashboard
```bash
streamlit run streamlit_app.py
```

The dashboard will open at `http://localhost:8501`

## Configuration

Edit the following variables in the scripts:
- `API_TOKEN`: Your Clash of Clans API token
- `CLAN_TAG`: Your clan's tag (e.g., "#2J28LL2VU")

⚠️ **Note**: API tokens are IP-restricted. Generate a new token if your IP changes.

## Project Structure

```
coc-clan-analyzer/
├── clan_analyzer.py      # Main analysis script (CLI)
├── streamlit_app.py      # Streamlit dashboard
├── requirements.txt      # Python dependencies
├── clan_history.json     # Historical data storage (auto-generated)
├── .gitignore           # Git ignore rules
└── README.md            # This file
```

## Rush Detection Algorithm

The rush detection system compares each player's current levels against the **maximum levels available at the previous Town Hall**:

- **Heroes**: 50% weight (most important)
- **Troops**: 35% weight
- **Spells**: 15% weight

### Status Classifications:
- ✅ **Maxed** (score < 3): Fully caught up
- 🟢 **Slightly Behind** (3-10): Minor gaps
- 🟡 **Moderately Rushed** (10-25): Noticeable deficits
- 🟠 **Rushed** (25-50): Significant gaps
- 🔴 **Severely Rushed** (25+ with 15+ hero levels missing)

## Data Persistence

The analyzer stores historical war attack data in `clan_history.json`, allowing you to track performance trends over time.

## API Rate Limits

The Clash of Clans API has rate limits. The script includes delays between requests to avoid hitting these limits.

## Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT](LICENSE)

## Disclaimer

This project is not affiliated with, endorsed, sponsored, or specifically approved by Supercell and Supercell is not responsible for it. For more information see Supercell's Fan Content Policy.
