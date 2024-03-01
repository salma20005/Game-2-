# File: CS112-A1-T2-3-20230172
# Purpose : 2 players want to get the number 15 by adding 3 numbers and who gets it first is the winner
# Author : Salma Yasser Saied
# ID: 20230172
# function to check sum of indexes of first player
def checkp1(used_numbers1):
 if len(used_numbers1) >= 3:
   for i in range(len(used_numbers1)):
       for j in range(len(used_numbers1)):
           for  k in range(len(used_numbers1)):
              if used_numbers1[i] != used_numbers1[j] and used_numbers1[j] != used_numbers1[k] and used_numbers1[k] != used_numbers1[i]:
                  if used_numbers1[i] + used_numbers1[j] +used_numbers1[k] == 15:
                      return True
   return False
 return False
# function to check sum of indexes of second player
def checkp2(used_numbers2):
    if len(used_numbers2) >= 3:
        for i in range(len(used_numbers2)):
            for j in range(len(used_numbers2)):
                for k in range(len(used_numbers2)):
                    if used_numbers2[i] != used_numbers2[j] and used_numbers2[j] != used_numbers2[k] and used_numbers2[i] != used_numbers2[k]:
                        if used_numbers2[i] + used_numbers2[j] + used_numbers2[k] == 15:
                            return True
        return False
    return False

def main():
    #set the value of the required number
    required_num = 15
    #welcome message and display status
    print("Welcome to Number Scrabble ")
    print("The required number = 15")
    print("list = [1,2,3,4,5,6,7,8,9]")
    #creating a list to keep track of numbers players used
    used_numbers1 = []
    used_numbers2 = []

    # playing the game
    list = [1,2,3,4,5,6,7,8,9]
    result1 = 0
    result2 = 0
    player1_turn = True
    while True :
      if (len(list) == len(used_numbers1) + len(used_numbers2)):
            print("Draw")
            print(("The list of player 1 :"), used_numbers1)
            print(("The list of player 2 :"), used_numbers2)
            break
      if player1_turn:
        # player1 enters the number
        num = input("Player1 : Please enter number from the list :  ")
        # check if the number is in the list
        try:
          num = int(num)
          if num < 1 or num > 9:
            print("Please enter a number from list ")
            continue
          # check if the number is in list of used of numbers
          if num in used_numbers2 or num in used_numbers1:
              print("Number already used . Enter a different number")
              continue

        except ValueError:
          print("Please enter a valid input")
          continue
        result1 += num

        # Add the number to list of the used numbers
        used_numbers1.append(num)
        print(("The list of player 1 : "), used_numbers1)

            # check if player 1 wins
        if result1 == 15 and len(used_numbers1) == 3:
            print("player 1 is winner")
            return
            # calling the function of checking for player 1
        elif checkp1(used_numbers1) == True:
            print("player 1 is winner")
            return
            # switch to player2
        player1_turn = False
      else :
          # player 2 enters number
          num = input("Player2 : Please enter number from the list :  ")
          # check if the number is in the list
          try :
            num = int(num)
            if num < 1 or num > 9:
             print("Please enter a number from list ")
             continue
             # check if the number is in list of used numbers
            if num in used_numbers1 or num in used_numbers2 :
             print("Number already used . Enter a different number ")
             continue

          except ValueError :
            print("Please enter a valid number")
            continue
          result2 += num
               # Add the number to list of the used numbers
          used_numbers2.append(num)
          print(("The list of player 2 :"), used_numbers2)
               # check if player 2 wins
          if result2 == 15 and len(used_numbers2) == 3:
            print("player 2 is winner")
            return
              # calling the function of checking for player 2
          elif checkp2(used_numbers2) == True :
            print("player 2 is winner")
            return
                # switch to player1
          player1_turn = True

main()
