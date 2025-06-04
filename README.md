# CryptoFam - Rule-Based Cryptocurrency Chatbot

# Step 1: Predefined crypto database
crypto_db = {
    "Bitcoin": {
        "price_trend": "rising",
        "market_cap": "high",
        "energy_use": "high",
        "sustainability_score": 3
    },
    "Ethereum": {
        "price_trend": "stable",
        "market_cap": "high",
        "energy_use": "medium",
        "sustainability_score": 6
    },
    "Cardano": {
        "price_trend": "rising",
        "market_cap": "medium",
        "energy_use": "low",
        "sustainability_score": 8
    }
}

# Step 2: Define chatbot logic
def crypto_fam():
    print("👋 Welcome to CryptoFam — your friendly crypto advisor!")
    print("Ask me questions like:")
    print("- Which crypto is trending up?")
    print("- What’s the most sustainable coin?")
    print("- Which one is most profitable?\n")

    user_query = input("💬 Your question: ").lower()

    if "sustainable" in user_query or "eco" in user_query:
        recommend = max(crypto_db, key=lambda x: crypto_db[x]["sustainability_score"])
        print(f"🌱 Invest in {recommend}! It’s the most eco-friendly option with strong sustainability potential.")

    elif "trending" in user_query or "rising" in user_query:
        rising_coins = [coin for coin in crypto_db if crypto_db[coin]["price_trend"] == "rising"]
        print(f"📈 These coins are trending up: {', '.join(rising_coins)}.")

    elif "profitable" in user_query or "profit" in user_query:
        for coin, data in crypto_db.items():
            if data["price_trend"] == "rising" and data["market_cap"] == "high":
                print(f"💰 {coin} looks profitable! It's rising and has a strong market cap.")
                break
        else:
            print("📊 No coin fits the best investment profile right now.")

    elif "energy" in user_query or "efficient" in user_query:
        low_energy = [coin for coin in crypto_db if crypto_db[coin]["energy_use"] == "low"]
        print(f"⚡ These coins use low energy: {', '.join(low_energy)}.")

    else:
        print("🤖 Sorry, I didn’t understand that. Try asking about trending coins, energy use, or profitability.")

# Step 3: Run the chatbot
crypto_fam()
python crypto_fam.py
