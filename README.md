<img src="doc/openwid-logo.png" alt="drawing" width="400"/>

**openwid** (OpenWeather in Dash) is a Python package for creating daily weather forecast components in Plotly Dash framework. You can easily add a fully responsive weather forecast card to your Dash applications. Before starting, you need to get a unique API key from <a href="https://home.openweathermap.org/api_keys">OpenWeather</a> website.

## Install
openwid can be installed using
```
pip install openwid
```

## Example full-code for Dash
```
import dash
import dash_bootstrap_components as dbc
import dash_html_components as html

from openwid import Openwid   # Importing openwid

owid_mon = Openwid(
    api_key="YOUR_API_KEY",   # <-- Edit Here
    latitude="45.501690",
    longitude="-73.567253"
)

app = dash.Dash(
    __name__, meta_tags=[{"name": "viewport", "content": "width=device-width"}],
    external_stylesheets = [dbc.themes.PULSE]
)

app.layout = html.Div(
    [
        html.Div(
            [
                dbc.Row(
                    dbc.Col(
                        owid_mon.get_card(city_name="Montréal", days=7),
                        lg=6,
                        md=6,
                        sm=12
                    ),
                )
            ], style={"margin": "2rem"}
        )
    ]
)

if __name__ == '__main__':
    app.run_server(debug=True)
```

## Screenshots
<img src="doc/screenshot-1.png" alt="drawing"/>
