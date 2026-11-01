# ORBIT WORLD v3 - FULL 195 UN COUNTRIES - Real TLE 2026-10-31
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.label import Label
from kivy.uix.button import Button
from kivy.uix.textinput import TextInput
from kivy.uix.spinner import Spinner
import math

TLE_DATA = {
    "ISS (ZARYA)": ["ISS (ZARYA)","1 25544U 98067A   26304.75703383  .00006360  00000+0  12291-3 0  9993","2 25544  51.6332 344.2755 0007028 332.5119  27.5497 15.49131714592920"],
    "CSS (TIANHE)": ["CSS (TIANHE)","1 48274U 21035A   26304.81366593  .00007043  00000+0  84508-4 0  9994","2 48274  41.4686 211.9204 0004008 241.3716 118.6720 15.61260946314509"],
    "TIANZHOU-10": ["TIANZHOU-10","1 69049U 26102A   26304.23795895  .00007415  00000+0  88781-4 0  9994","2 69049  41.4686 215.4265 0003959 238.3286 121.7167 15.61253455311436"],
    "PROGRESS-MS 34": ["PROGRESS-MS 34","1 68837U 26093A   26304.17644456  .00006183  00000+0  11976-3 0  9998","2 68837  51.6332 347.1486 0007016 330.4977  29.5614 15.49124187587564"],
}

# FULL 195 COUNTRIES
COUNTRIES = {
    "Afghanistan - Kabul": (34.55,69.20), "Albania - Tirana": (41.32,19.81), "Algeria - Algiers": (36.75,3.06),
    "Andorra - Andorra la Vella": (42.50,1.52), "Angola - Luanda": (-8.83,13.23), "Antigua and Barbuda - St Johns": (17.12,-61.85),
    "Argentina - Buenos Aires": (-34.60,-58.38), "Armenia - Yerevan": (40.17,44.49), "Australia - Canberra": (-35.28,149.12),
    "Austria - Vienna": (48.20,16.37), "Azerbaijan - Baku": (40.40,49.86), "Bahamas - Nassau": (25.06,-77.34),
    "Bahrain - Manama": (26.22,50.58), "Bangladesh - Dhaka": (23.81,90.41), "Barbados - Bridgetown": (13.09,-59.61),
    "Belarus - Minsk": (53.90,27.56), "Belgium - Brussels": (50.85,4.35), "Belize - Belmopan": (17.25,-88.76),
    "Benin - Porto-Novo": (6.49,2.62), "Bhutan - Thimphu": (27.47,89.63), "Bolivia - Sucre": (-19.03,-65.25),
    "Bosnia and Herzegovina - Sarajevo": (43.85,18.37), "Botswana - Gaborone": (-24.62,25.91), "Brazil - Brasilia": (-15.79,-47.88),
    "Brunei - Bandar Seri Begawan": (4.89,114.94), "Bulgaria - Sofia": (42.69,23.32), "Burkina Faso - Ouagadougou": (12.36,-1.53),
    "Burundi - Gitega": (-3.42,29.92), "Cabo Verde - Praia": (14.91,-23.50), "Cambodia - Phnom Penh": (11.55,104.91),
    "Cameroon - Yaounde": (3.84,11.50), "Canada - Ottawa": (45.42,-75.69), "Central African Republic - Bangui": (4.39,18.55),
    "Chad - NDjamena": (12.13,15.05), "Chile - Santiago": (-33.44,-70.66), "China - Beijing": (39.90,116.40),
    "Colombia - Bogota": (4.71,-74.07), "Comoros - Moroni": (-11.70,43.24), "Congo - Brazzaville": (-4.26,15.28),
    "Congo DR - Kinshasa": (-4.32,15.30), "Costa Rica - San Jose": (9.92,-84.09), "Croatia - Zagreb": (45.81,15.98),
    "Cuba - Havana": (23.11,-82.36), "Cyprus - Nicosia": (35.18,33.36), "Czech Republic - Prague": (50.07,14.43),
    "Denmark - Copenhagen": (55.68,12.56), "Djibouti - Djibouti": (11.57,43.14), "Dominica - Roseau": (15.30,-61.38),
    "Dominican Republic - Santo Domingo": (18.47,-69.89), "Ecuador - Quito": (-0.22,-78.51), "Egypt - Cairo": (30.04,31.23),
    "El Salvador - San Salvador": (13.69,-89.21), "Equatorial Guinea - Malabo": (3.75,8.78), "Eritrea - Asmara": (15.33,38.93),
    "Estonia - Tallinn": (59.43,24.75), "Eswatini - Mbabane": (-26.30,31.13), "Ethiopia - Addis Ababa": (9.03,38.74),
    "Fiji - Suva": (-18.14,178.44), "Finland - Helsinki": (60.16,24.93), "France - Paris": (48.85,2.35),
    "Gabon - Libreville": (0.41,9.46), "Gambia - Banjul": (13.45,-16.57), "Georgia - Tbilisi": (41.72,44.82),
    "Germany - Berlin": (52.52,13.40), "Ghana - Accra": (5.60,-0.21), "Greece - Athens": (37.98,23.72),
    "Grenada - St Georges": (12.05,-61.74), "Guatemala - Guatemala City": (14.63,-90.50), "Guinea - Conakry": (9.51,-13.57),
    "Guinea-Bissau - Bissau": (11.86,-15.58), "Guyana - Georgetown": (6.80,-58.15), "Haiti - Port-au-Prince": (18.59,-72.33),
    "Honduras - Tegucigalpa": (14.07,-87.19), "Hungary - Budapest": (47.49,19.04), "Iceland - Reykjavik": (64.14,-21.94),
    "India - New Delhi": (28.61,77.20), "Indonesia - Jakarta": (-6.20,106.84), "Iran - Tehran": (35.68,51.38),
    "Iraq - Baghdad": (33.32,44.36), "Ireland - Dublin": (53.34,-6.26), "Israel - Jerusalem": (31.76,35.21),
    "Italy - Rome": (41.90,12.49), "Jamaica - Kingston": (17.97,-76.79), "Japan - Tokyo": (35.68,139.69),
    "Jordan - Amman": (31.95,35.92), "Kazakhstan - Astana": (51.18,71.44), "Kenya - Nairobi": (-1.28,36.82),
    "Kiribati - Tarawa": (1.32,173.12), "Korea North - Pyongyang": (39.03,125.76), "Korea South - Seoul": (37.56,126.97),
    "Kosovo - Pristina": (42.66,21.16), "Kuwait - Kuwait City": (29.37,47.97), "Kyrgyzstan - Bishkek": (42.87,74.59),
    "Laos - Vientiane": (17.97,102.60), "Latvia - Riga": (56.94,24.10), "Lebanon - Beirut": (33.89,35.50),
    "Lesotho - Maseru": (-29.31,27.48), "Liberia - Monrovia": (6.30,-10.80), "Libya - Tripoli": (32.88,13.19),
    "Liechtenstein - Vaduz": (47.14,9.52), "Lithuania - Vilnius": (54.68,25.27), "Luxembourg - Luxembourg": (49.61,6.12),
    "Madagascar - Antananarivo": (-18.87,47.50), "Malawi - Lilongwe": (-13.96,33.77), "Malaysia - Kuala Lumpur": (3.13,101.68),
    "Maldives - Male": (4.17,73.50), "Mali - Bamako": (12.63,-8.00), "Malta - Valletta": (35.89,14.51),
    "Marshall Islands - Majuro": (7.08,171.38), "Mauritania - Nouakchott": (18.07,-15.96), "Mauritius - Port Louis": (-20.16,57.50),
    "Mexico - Mexico City": (19.43,-99.13), "Micronesia - Palikir": (6.92,158.16), "Moldova - Chisinau": (47.01,28.86),
    "Monaco - Monaco": (43.73,7.42), "Mongolia - Ulaanbaatar": (47.91,106.90), "Montenegro - Podgorica": (42.43,19.26),
    "Morocco - Rabat": (34.02,-6.84), "Mozambique - Maputo": (-25.96,32.58), "Myanmar - Naypyidaw": (19.76,96.07),
    "Namibia - Windhoek": (-22.56,17.08), "Nauru - Yaren": (-0.54,166.93), "Nepal - Kathmandu": (27.71,85.32),
    "Netherlands - Amsterdam": (52.37,4.89), "New Zealand - Wellington": (-41.29,174.77), "Nicaragua - Managua": (12.11,-86.23),
    "Niger - Niamey": (13.51,2.11), "Nigeria - Abuja": (9.07,7.49), "North Macedonia - Skopje": (41.99,21.43),
    "Norway - Oslo": (59.91,10.75), "Oman - Muscat": (23.61,58.54), "Pakistan - Islamabad": (33.68,73.04),
    "Palau - Ngerulmud": (7.50,134.62), "Palestine - Ramallah": (31.90,35.20), "Panama - Panama City": (8.98,-79.51),
    "Papua New Guinea - Port Moresby": (-9.47,147.18), "Paraguay - Asuncion": (-25.30,-57.63), "Peru - Lima": (-12.04,-77.04),
    "Philippines - Manila": (14.59,120.98), "Poland - Warsaw": (52.22,21.01), "Portugal - Lisbon": (38.72,-9.13),
    "Qatar - Doha": (25.28,51.53), "Romania - Bucharest": (44.43,26.10), "Russia - Moscow": (55.75,37.61),
    "Rwanda - Kigali": (-1.94,30.06), "Saint Kitts and Nevis - Basseterre": (17.30,-62.72), "Saint Lucia - Castries": (14.01,-60.98),
    "Saint Vincent - Kingstown": (13.16,-61.22), "Samoa - Apia": (-13.85,-171.75), "San Marino - San Marino": (43.94,12.44),
    "Sao Tome - Sao Tome": (0.33,6.73), "Saudi Arabia - Riyadh": (24.71,46.67), "Senegal - Dakar": (14.69,-17.44),
    "Serbia - Belgrade": (44.80,20.46), "Seychelles - Victoria": (-4.61,55.45), "Sierra Leone - Freetown": (8.46,-13.23),
    "Singapore - Singapore": (1.35,103.81), "Slovakia - Bratislava": (48.14,17.10), "Slovenia - Ljubljana": (46.05,14.50),
    "Solomon Islands - Honiara": (-9.43,159.96), "Somalia - Mogadishu": (2.04,45.34), "South Africa - Pretoria": (-25.74,28.18),
    "South Sudan - Juba": (4.85,31.58), "Spain - Madrid": (40.41,-3.70), "Sri Lanka - Colombo": (6.92,79.86),
    "Sudan - Khartoum": (15.50,32.55), "Suriname - Paramaribo": (5.85,-55.16), "Sweden - Stockholm": (59.32,18.06),
    "Switzerland - Bern": (46.94,7.44), "Syria - Damascus": (33.51,36.27), "Taiwan - Taipei": (25.03,121.56),
    "Tajikistan - Dushanbe": (38.55,68.77), "Tanzania - Dodoma": (-6.16,35.74), "Thailand - Bangkok": (13.75,100.50),
    "Timor-Leste - Dili": (-8.55,125.56), "Togo - Lome": (6.13,1.22), "Tonga - Nuku'alofa": (-21.13,-175.20),
    "Trinidad and Tobago - Port of Spain": (10.65,-61.51), "Tunisia - Tunis": (36.80,10.18), "Turkey - Ankara": (39.93,32.85),
    "Turkmenistan - Ashgabat": (37.95,58.38), "Tuvalu - Funafuti": (-7.10,177.64), "Uganda - Kampala": (0.34,32.58),
    "Ukraine - Kyiv": (50.45,30.52), "UAE - Abu Dhabi": (24.45,54.37), "UK - London": (51.50,-0.12),
    "USA - Washington DC": (38.89,-77.03), "Uruguay - Montevideo": (-34.88,-56.18), "Uzbekistan - Tashkent": (41.29,69.24),
    "Vanuatu - Port Vila": (-17.73,168.31), "Vatican City - Vatican City": (41.90,12.45), "Venezuela - Caracas": (10.48,-66.90),
    "Vietnam - Hanoi": (21.02,105.83), "Yemen - Sanaa": (15.36,44.20), "Zambia - Lusaka": (-15.40,28.32),
    "Zimbabwe - Harare": (-17.82,31.03)
}

def solve_kepler(M, e):
    E = M if e < 0.8 else math.pi
    for _ in range(30):
        d = (E - e*math.sin(E) - M)/(1 - e*math.cos(E))
        E -= d
        if abs(d) < 1e-7: break
    return E

def propagate(tle2, dt_min):
    inc = math.radians(float(tle2[8:16])); raan = math.radians(float(tle2[17:25]))
    e = float("0."+tle2[26:33].strip()); argp = math.radians(float(tle2[34:42]))
    M0 = math.radians(float(tle2[43:51])); n = float(tle2[52:63])
    M = M0 + n * 2*math.pi/1440 * dt_min; E = solve_kepler(M % (2*math.pi), e)
    a = (398600.4418 / ((n*2*math.pi/86400)**2))**(1/3); r = a * (1 - e*math.cos(E))
    lat = math.degrees(math.asin(math.sin(inc)*math.sin(argp + E)))
    lon = (raan + math.atan2(math.cos(inc)*math.sin(argp+E), math.cos(argp+E)) - math.radians((dt_min*0.25)%360))
    lon = ((math.degrees(lon)+180)%360)-180; alt = r - 6371
    return lat, lon, alt, n

class OrbitWorld(BoxLayout):
    def __init__(self, **kwargs):
        super().__init__(orientation='vertical', **kwargs)
        self.current = "ISS (ZARYA)"; self.dt = 0; self.country = "Zimbabwe - Harare"
        self.h_lat, self.h_lon = COUNTRIES[self.country]
        self.add_widget(Label(text="[ ORBIT WORLD - 195 COUNTRIES ]", color=(0,1,0.6,1), size_hint_y=0.07))
        self.spinner = Spinner(text=self.country, values=sorted(COUNTRIES.keys()), size_hint_y=0.1, background_color=(0,0.3,0.15,1), color=(0,1,0.6,1))
        self.spinner.bind(text=self.on_country); self.add_widget(self.spinner)
        self.data_label = Label(text="Loading...", color=(0.7,1,0.8,1), size_hint_y=0.45, font_size='13sp'); self.add_widget(self.data_label)
        self.tle_input = TextInput(hint_text="paste new tle data", size_hint_y=0.1, background_color=(0,0.1,0.05,1), foreground_color=(0,1,0.6,1)); self.add_widget(self.tle_input)
        row = BoxLayout(size_hint_y=0.09)
        for name in TLE_DATA.keys():
            b = Button(text=name.split()[0][:5], background_color=(0,0.3,0.15,1), font_size='8sp')
            b.bind(on_press=lambda x, n=name: setattr(self,'current',n)); row.add_widget(b)
        self.add_widget(row)
        row2 = BoxLayout(size_hint_y=0.09)
        b_load = Button(text="LOAD TLE DATA", background_color=(0,0.8,0.4,1), color=(0,0,0,1)); b_load.bind(on_press=self.load_tle)
        b_fwd = Button(text="+10 MIN", background_color=(0,0.4,0.2,1)); b_fwd.bind(on_press=lambda x: setattr(self,'dt',self.dt+10))
        row2.add_widget(b_load); row2.add_widget(b_fwd); self.add_widget(row2)
        from kivy.clock import Clock; Clock.schedule_interval(self.update, 0.5); self.update(None)
    def on_country(self, spinner, text):
        self.country = text; self.h_lat, self.h_lon = COUNTRIES[text]; self.dt = 0
    def load_tle(self, _):
        txt = self.tle_input.text.strip().split("\n")
        if len(txt)>=2: TLE_DATA["CUSTOM"] = txt[-3:] if len(txt)>=3 else ["CUSTOM"]+txt[-2:]; self.current = "CUSTOM"
    def update(self, _):
        info = TLE_DATA[self.current]; tle2 = info[2] if len(info)==3 else info[1]
        lat, lon, alt, n = propagate(tle2, self.dt); self.dt += 0.15
        dlon_r = math.radians(lon - self.h_lon); y = math.sin(dlon_r)
        x = math.cos(math.radians(self.h_lat))*math.tan(math.radians(lat)) - math.sin(math.radians(self.h_lat))*math.cos(dlon_r)
        az = (math.degrees(math.atan2(y,x))+360)%360; dist = math.sqrt((lat-self.h_lat)**2 + (lon-self.h_lon)**2)
        visible = dist < 25
        self.data_label.text = f"[{self.current}]\nCountry: {self.country}\nLAT {lat:+07.2f} LON {lon:+08.2f} ALT {alt:.0f}km\nFROM {self.country.split(' - ')[-1]}: AZ {az:.0f}° DIST {dist:.1f}°\n{'>>> VISIBLE NOW! <<<' if visible else 'Not visible from here'}\nT+{self.dt:.0f}min | OFFLINE WORLD MODE"

class OrbitApp(App):
    def build(self):
        self.title = "ORBIT WORLD FULL"; return OrbitWorld()

OrbitApp().run()