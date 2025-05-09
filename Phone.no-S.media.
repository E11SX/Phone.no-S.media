import subprocess
import json
import os
import sys

# Dynamically add 'checkers' directory to the system path
current_dir = os.getcwd()
checkers_dir = os.path.join(current_dir, "checkers")
sys.path.append(checkers_dir)

# Import the local whatsapp checker module if it exists
try:
    import whatsapp
except ModuleNotFoundError:
    whatsapp = None

# Retrieve phone number from environment variable or fallback to a default
PHONE_NUMBER = os.getenv("PHONE_NUMBER", "+1234567890")

results = []

# WhatsApp check using Python
if whatsapp:
    try:
        wa_result = whatsapp.check_whatsapp(PHONE_NUMBER)
        results.append(wa_result)
    except Exception as e:
        results.append({"platform": "WhatsApp", "status": f"Error: {str(e)}"})
else:
    results.append({"platform": "WhatsApp", "status": "Error: whatsapp module not found"})

# Telegram check using Go script
try:
    go_result = subprocess.run(["go", "run", os.path.join("checkers", "telegram.go"), PHONE_NUMBER], capture_output=True, text=True)
    results.append(json.loads(go_result.stdout))
except Exception as e:
    results.append({"platform": "Telegram", "status": f"Error: {str(e)}"})

# Facebook check using Node.js
try:
    node_result = subprocess.run(["node", os.path.join("checkers", "facebook.js"), PHONE_NUMBER], capture_output=True, text=True)
    results.append(json.loads(node_result.stdout))
except Exception as e:
    results.append({"platform": "Facebook", "status": f"Error: {str(e)}"})

# Ensure output directory exists
os.makedirs("output", exist_ok=True)

# Save result to file
with open("output/results.json", "w") as f:
    json.dump(results, f, indent=4)

print("\nScan Results:")
print(json.dumps(results, indent=4))
