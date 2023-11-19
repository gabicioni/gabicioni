- 👋 Hi, I’m @gabicioni
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
import numpy as np

def calculate_goals(data):
  """
  Calcule le nombre de buts possibles dans un match en fonction des données historiques.

  Args:
    data: Un tableau contenant les données historiques pour les deux équipes.

  Returns:
    Une liste de listes, où chaque liste représente un possible résultat du match.
  """

  # Calcule les probabilités de chaque résultat possible.
  probabilities = calculate_probabilities(data)

  # Crée une liste de listes, où chaque liste représente un possible résultat du match.
  results = []
  for i in range(0, len(probabilities)):
    results.append([probabilities[i][0], probabilities[i][1]])

  return results

def calculate_probabilities(data):
  """
  Calcule les probabilités de chaque résultat possible dans un match.

  Args:
    data: Un tableau contenant les données historiques pour les deux équipes.

  Returns:
    Une liste de listes, où chaque liste représente la probabilité de chaque résultat possible.
  """

  # Calcule les statistiques de chaque équipe.
  wins = data["wins"]
  losses = data["losses"]
  draws = data["draws"]

  # Calcule les probabilités de chaque résultat possible.
  probabilities = []
  for score1 in range(0, 11):
    for score2 in range(0, 11):
      probability = (wins[score1] * wins[score2] + losses[score1] * losses[score2] + draws[score1] * draws[score2]) / (wins[score1] + losses[score1] + draws[score1])
      probabilities.append([probability, score1, score2])

  return probabilities

# Charge les données historiques.
data = np.loadtxt("data.csv", skiprows=1, delimiter=",")

# Calcule les résultats possibles du match.
results = calculate_goals(data)

# Imprime les résultats possibles du match.
for result in results:
  print(result)
<!---
gabicioni/gabicioni is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
