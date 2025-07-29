# first_made
new
import requests
import sys
import json
def main():
   print(f"${bitcoin(sys.argv)}")





def bitcoin(s):
   try:
      if len(s) == 1:
         sys.exit("Missing command-line argument")
      elif len(s) == 2:
         if s[1].isdigit() == True or is_float(s[1]) == True:
            response = requests.get("https://rest.coincap.io/v3/assets/bitcoin?apiKey=33c14528cd04aa21aefb5034c0b72016e372f751d42c9ede3352334c59a36109")
            o = response.json()
            p = o.get("data")
            price = float(p.get("priceUsd"))
            return f"{float(s[1])*price:,.4f}"


         else:
           sys.exit("Command-line argument is not a number")


   except requests.RequestException:
      sys.exit()

def is_float(v):
   try:
      float(v)
      return True
   except ValueError:
      return False



if __name__ == "__main__":
   main()
