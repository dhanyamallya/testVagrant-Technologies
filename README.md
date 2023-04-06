# testVagrant-Technologies
# M Dhanya Mallya
# My Subscription code
class Newspaper:
  def __init__(self, name, prices):
    self.name = name
    self.prices = prices
  def __str__(self):
    return self.name
def possible_combinations(newspapers, budget):
  combinations = []
  for i, newspaper in enumerate(newspapers):
        if budget >= min(newspaper.prices):
            if budget in newspaper.prices:
                combinations.append([newspaper])
            else:
                for comb in possible_combinations(newspapers[i:], budget - min(newspaper.prices)):
                    if comb[0] is newspaper or budget >= min(comb[0].prices) + min(newspaper.prices):
                        combinations.append([newspaper] + comb)
    return combinations


if __name__ == "__main__":
    toi = Newspaper("TOI", [3, 3, 3, 3, 3, 5, 6])
    hindu = Newspaper("Hindu", [2.5, 2.5, 2.5, 2.5, 2.5, 4, 4])
    et = Newspaper("ET", [4, 4, 4, 4, 4, 4, 10])
    bm = Newspaper("BM", [1.5, 1.5, 1.5, 1.5, 1.5, 1.5, 1.5])
    ht = Newspaper("HT", [2, 2, 2, 2, 4, 4, 4])

    newspapers = [toi, hindu, et, bm, ht]

    budget = int(input("Enter your weekly budget: "))

    combinations = possible_combinations(newspapers, budget)

    print(f"All possible combinations of newspaper subscriptions for the weekly budget of {budget}:")

    for comb in combinations:
        print(", ".join(str(newspaper) for newspaper in comb))
     
