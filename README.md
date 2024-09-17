# Popularidade-das-linguagem-de-programa-o-2019
import pandas as pd
import matplotlib.pyplot as plt
from io import StringIO

# Criando os dados a partir da tabela fornecida
data = """
Week,Python,Java,C++
4/21/2019,55,55,18
4/28/2019,52,50,16
5/5/2019,56,56,17
5/12/2019,56,61,18
5/19/2019,57,56,17
5/26/2019,55,57,17
6/2/2019,54,58,15
6/9/2019,58,55,16
6/16/2019,58,56,16
6/23/2019,60,57,16
6/30/2019,57,54,16
7/7/2019,60,58,17
7/14/2019,60,57,17
7/21/2019,56,55,15
7/28/2019,59,53,16
8/4/2019,57,54,16
8/11/2019,54,51,16
8/18/2019,61,58,19
8/25/2019,59,60,19
"""

# Lendo os dados para um DataFrame
df = pd.read_csv(StringIO(data), parse_dates=["Week"])

# Configurando a data como índice
df.set_index("Week", inplace=True)

# Criando o gráfico da popularidade das linguagens ao longo do tempo
plt.figure(figsize=(10,6))
plt.plot(df.index, df['Python'], label='Python', marker='o')
plt.plot(df.index, df['Java'], label='Java', marker='o')
plt.plot(df.index, df['C++'], label='C++', marker='o')

# Definindo título e legendas
plt.title('Popularidade das Linguagens de Programação (Abril 2019 - Agosto 2019)')
plt.xlabel('Semana')
plt.ylabel('Popularidade')
plt.xticks(rotation=45)
plt.legend()

# Exibindo o gráfico
plt.tight_layout()
plt.show()
