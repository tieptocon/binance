# binance
API Binance
from flask import Flask, jsonify
import ccxt

app = Flask(__name__)

binance = ccxt.binance({
    'apiKey': 'IBIKHnxqOxUGVkwJhigGyIv1P64rKOV3f3wXc5hI5YxGlKVPxQzLkEp5XBWVuYuL',
    'secret': 'OJvR45HVQ5hFEoM7s88ArlQQmHL8PfvUUxJycxcmlrD0LhwcwJvi9oV0vSpGeTpL',
})

@app.route('/ticker', methods=['GET'])
def get_ticker():
    ticker = binance.fetch_ticker('BTC/USDT')
    return jsonify({'last_price': ticker['last']})

if __name__ == '__main__':
    app.run(port=5000)
