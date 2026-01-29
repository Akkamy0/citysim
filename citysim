import random as rd
import os 



class CitySimulator:
    def __init__(self, name, population, food, gold):
        self.name = name
        self.population = population
        self.food = food
        self.gold = gold

    def food_produced(self):
        
        # Random event affecting food production
        random_food_event = rd.choice([1.5, 0.8, 1, 1, 1, 1, 1, 1])
        
        # Food production based on population
        food_production = int(self.population * 1.5 * random_food_event)
        self.food += food_production
        
        if random_food_event == 1.5:
            print(f"""
                  
                  Great harvest this year! Food production increased by 50%!
                  
                  {self.name} produced {food_production} food this year.

                  """)
            print(input("Enter any key to continue..." ))
            os.system("cls")

        elif random_food_event == 0.8:
            print(f"""
                  
                  Poor harvest this year! Food production decreased by 20%!
                  
                  {self.name} produced {food_production} food this year.

                  """)
            print(input("Enter any key to continue..." ))  
            os.system("cls")

        else:
            print(f""" 

                  {self.name} produced {food_production} food this year.

                  """)
            print(input("Enter any key to continue..." ))
            os.system("cls")

    def gold_produced(self):
        
        # Random event affecting gold production
        random_gold_event = rd.choice([2, 0.5, 1, 1, 1, 1])

        # Gold production based on population
        gold_production = int(((self.population // 10 ) * 3 ) * random_gold_event)
        self.gold += gold_production
        
        if random_gold_event == 2:
            print(f"""
                  
                  Gold rush this year! Gold production doubled!
                  
                  {self.name} produced {gold_production} gold this year.

                  """)
            print(input("Enter any key to continue..." ))
            os.system("cls")
        
        elif random_gold_event == 0.5:
            print(f"""
                  
                  Economic downturn this year! Gold production halved!
                  
                  {self.name} produced {gold_production} gold this year.

                  """)
            print(input("Enter any key to continue..." ))
            os.system("cls")

        else:
            print(f""" 

                  {self.name} produced {gold_production} gold this year.

                  """)
            print(input("Enter any key to continue..." ))
            os.system("cls")

    def population_growth(self):
        # Population growth based on food
        if self.food >= self.population * 2:
            growth = self.population // 10
            growth = int(growth * 1.25)
            self.population += growth
            print(f"""    

            You have enough food to support your population! 
            
            Your people are thriving and you gain 25% more population!
                  
            {self.name} population increased by {growth} this year.
        
            """)
            print(input("Enter any key to continue..." ))
            os.system("cls")

        elif self.food >= self.population:
            growth = self.population // 10
            self.population += growth
            print(f"""  

            You don't have enough food to fully support your population!
                  
            Your people are in a stable condition and your population grows normally.
                  
            {self.name} population increased by {growth} this year.

            """)
            print(input("Enter any key to continue..." ))
            os.system("cls")
        
        else:
            growth = self.population // 10
            growth = int(growth * 0.75)
            self.population += growth
            print(f""" 

            You don't have nearly enough food to support your population!
                  
            Your people are struggling and you gain 25% less population!
                  
            {self.name} population increased by {growth} this year.

            """)
            print(input("Enter any key to continue..." ))
            os.system("cls")


    def simulate_year(self):

        print(f"Simulating year for {self.name}...")

        # Food production
        self.food_produced()
        # Gold production
        self.gold_produced()


        
        
        # Player has not enough food and option to trade gold for food
        if self.food < self.population * 2:
            low_food_choice = input(f"""{self.name} does not have enough food! You need {abs(self.food)} more food to feed your population.
                                    
                  Do you want to trade gold for food?
                                    
                            1. Yes
                            2. No

                            (Note: 1 food = 3 gold)
                                    
                  """).lower()
            
            while low_food_choice != "yes" and low_food_choice != "no" and low_food_choice != "1" and low_food_choice != "2":
                low_food_choice = input("Please enter \"yes\" or \"no\" (or \"1\" or \"2\"): ").lower()

            if low_food_choice == "yes" or low_food_choice == "1":
                food_needed = (self.population * 2) - self.food
                gold_needed = food_needed * 3 
                
                if self.gold >= gold_needed:
                    self.gold -= gold_needed
                    self.food += food_needed
                    print(f"Traded {gold_needed} gold for {food_needed} food!")
                
                else:
                    print(f"Not enough gold to trade for food!")
                    population_loss = max(1, )
                    self.population -= population_loss
                    self.food = 0
                    print("")
                    print(f"{self.name} lost {population_loss} population due to starvation!")

            elif low_food_choice == "no" or low_food_choice == "2":
                population_loss = max(1, abs(self.food) // 2)
                self.population -= population_loss
                self.food = 0
                print(f"{self.name} lost {population_loss} population due to starvation!")


        # Player has excess food and option to trade or save half
        elif self.food > self.population:
            excess_food_choice = input(f"""{self.name} has plenty of food! You have {self.food} excess food.
                                    
                  Do you want to trade the excess food for gold or a boost in population or save half of the food for the following year?
                            
                            1. Trade
                            2. Save half
                    
                            (Note:  1 food = 2 gold 
                                    or 3 food = +1 population)
                                       
                  """).lower()

            while excess_food_choice != "trade"  and excess_food_choice != "1" and excess_food_choice != "save half" and excess_food_choice != "2":
                excess_food_choice = input(" Please choose one of the options: ").lower()

            if excess_food_choice == "trade" or excess_food_choice == "1":
                trade_choice = input(f""" What do you want to trade the excess food for?
                                     
                            1. Gold
                            2. Population

                            (Note:  1 food = 2 gold 
                                    or 3 food = +1 population)        
                                     
                          """).lower()
                
                while trade_choice != "gold" and trade_choice != "1" and trade_choice != "population" and trade_choice != "2":
                    trade_choice = input(" Please choose one of the options: ").lower()
                
                if trade_choice == "gold" or trade_choice == "1":
                    food_to_trade = self.food
                    gold_earned = food_to_trade * 2
                    self.gold += gold_earned
                    self.food = 0
                    print(f"Traded {food_to_trade} food for {gold_earned} gold!")
                
                elif trade_choice == "population" or trade_choice == "2":
                    food_to_trade = self.food
                    if food_to_trade % 3 == 0: 
                        population_increase = food_to_trade // 3
                        self.population += population_increase 
                        self.food = 0
                        print(f"Traded {food_to_trade} food for {population_increase} population!")
                    else:
                        population_increase = food_to_trade // 3
                        food_traded = population_increase * 3
                        self.population += population_increase
                        self.food -= food_traded
                        print(f"Traded {food_traded} food for {population_increase} population! Saved {(self.food // 2)} food for next year.")
                        self.food = self.food // 2
            
            elif excess_food_choice == "save half" or excess_food_choice == "2":
                food_saved = self.food // 2
                self.food = food_saved
                print(f"Saved {food_saved} food for next year.")
        
        
        # Player has just the right amount of food
        else:
            print(f"{self.name} has just the right amount of food for its population.")

        
        # Population growth
        self.population_growth()


        



        




# Function to generate city stats with alteast 1 very good stat and 1 slightly bad stat
def city_generator():
    pop_rd = rd.randint(50, 400)
    if pop_rd > 250:
        food_rd = rd.randint(200, 500)
        gold_rd = rd.randint(50, 150)
    elif pop_rd < 100:
        food_rd = rd.randint(50, 200)
        gold_rd = rd.randint(200, 500)
    else:
        food_rd = rd.randint(100, 400)
        gold_rd = rd.randint(100, 400)
    return pop_rd, food_rd, gold_rd

def main():
    print("\n" * 50)
    city_player_choice = input("""
                               
                               
Enter the name of your city: 
                               




          """)
    pop_rd, food_rd, gold_rd = city_generator()
    city = CitySimulator(city_player_choice, pop_rd, food_rd, gold_rd)
    os.system("cls")
    print(f"""
      
      Your city {city.name} has been created with the following stats:
          
          Population: {city.population}
          Food: {city.food}
          Gold: {city.gold}
      
      """)

    print(input("Enter any key to continue..." ))
    os.system("cls")
    while city.population > 0:
        city.simulate_year()
        continue_choice = input("Do you wish to simulate the next year? (Y/N)   ").lower()
        if continue_choice == "y" or continue_choice == "yes":
            continue
        elif continue_choice == "n" or continue_choice == "no":
            misinput_choice = input("Oh No! That was a misinput for sure! Here i will make it easier for you: do you wish to simulate the next year? (Y/Y)   ").lower()
            if misinput_choice == "y" or misinput_choice == "yes":
                continue
            elif misinput_choice == "n" or misinput_choice == "no":
                print("You outsmarted me! But i am the almighty code! so i will simulate the next year for you anyway!")
                continue
            else:
                print("Invalid input! Simulating next year anyway!")
                continue
        else:
            print("Invalid input! Simulating next year anyway!")
            continue
    
main()
    
