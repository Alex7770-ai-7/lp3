import random


class Weather:

    def init(self, humidity=50):
        self.humidity = humidity

    def change_humidity(self):
        self.humidity += random.randint(-10, 10)
        self.humidity = max(0, min(100, self.humidity))

    def get_humidity(self):
        return self.humidity


class HumiditySensor:

    def init(self, weather):
        self.weather = weather

    def read_humidity(self):
        return  "{self.weather.get_humidity()}%"

    def update_weather(self):
        self.weather.change_humidity()


weather = Weather()
sensor = HumiditySensor(weather)

for _ in range(5):
    sensor.update_weather()
    print(sensor.read_humidity())
