# Análise de Acidentes de Trânsito no Brasil (2024)

Este projeto apresenta uma análise estatística e probabilística de acidentes de trânsito no Brasil, utilizando dados oficiais do **DATATRAN 2024**. O estudo foi desenvolvido em **R** no ambiente **Google Colab**, com foco em responder questões sobre distribuição de acidentes por estado, condições climáticas, fase do dia e causas predominantes.

---

## 🎯 Objetivos
- Identificar o estado com maior número de acidentes.
- Calcular a probabilidade de acidentes em clima claro.
- Avaliar como a fase do dia influencia os acidentes.
- Determinar os tipos e causas predominantes.

---

## 🛠️ Metodologia
- **Linguagem:** R  
- **Bibliotecas:** `dplyr`, `ggplot2`  
- **Etapas:**  
  1. Carregamento e inspeção dos dados (`datatran2024.csv`).  
  2. Manipulação e sumarização com `dplyr`.  
  3. Cálculos probabilísticos.  
  4. Visualização com gráficos de barras (`ggplot2`).  


## 📊 Resultados
**Estado com mais acidentes:** Minas Gerais (MG).

Codigo R : 
estado_acidentes <- dados %>%
  group_by(uf) %>%
  summarise(total = n()) %>%
  arrange(desc(total))

   Insight: Minas Gerais concentra o maior número de acidentes, evidenciando que regiões com maior extensão rodoviária e fluxo intenso de veículos tendem a registrar mais ocorrências
   
  <img width="200" height="762" alt="image" src="https://github.com/user-attachments/assets/c1796be3-8027-4ba2-8da6-a30710c7a173" />


**Probabilidade em clima claro:** ~65% dos acidentes.

  Codigo R : 
claro <- nrow(filter(dados, condicao_metereologica == "Claro"))
prob_claro <- claro / nrow(dados)

  Insight: Aproximadamente 65% dos acidentes ocorreram em condições de céu claro, mostrando que o clima adverso não é o principal fator. Isso reforça que falhas humanas e comportamentais são mais determinantes do que o ambiente climático.


<img width="200" height="566" alt="image" src="https://github.com/user-attachments/assets/a14a0662-20a4-4b0a-b405-c05e8b6dfcc0" />



 **Fase do dia:** maior incidência durante manhã e tarde.
 
 Codigo R : 
 fase_dia_acidentes <- dados %>%
  group_by(fase_dia) %>%
  summarise(total = n())


  Insight: A maior parte dos acidentes acontece durante o dia, especialmente pela manhã e tarde, períodos de maior tráfego. A madrugada concentra menos acidentes, mas costuma estar associada a causas específicas como cansaço ou ingestão de álcool

<img width="200" height="678" alt="image" src="https://github.com/user-attachments/assets/a46be047-36bc-4ea4-be28-5451393b29dd" />


    
**Causas predominantes:** falta de atenção, reação tardia e velocidade incompatível.

Código R: 
causa_acidentes <- dados %>%
  group_by(causa_acidente) %>%
  summarise(total = n())

Insight: Colisões são os acidentes mais comuns e as principais causas estão ligadas à falta de atenção, reação tardia e velocidade incompatível. Isso evidencia que o fator humano é predominante, superando falhas mecânicas ou condições externas.

<img width="200" height="538" alt="image" src="https://github.com/user-attachments/assets/1453d7c1-87a2-45a9-b20c-15f2133d24db" />



---

## 📚 Referências
- Ministério dos Transportes; Polícia Rodoviária Federal. **Registro Nacional de Sinistros e Estatísticas de Trânsito (DATATRAN)**. Brasília, 2024.  
- SITRAN. **Registro Nacional de Acidentes e Estatísticas de Trânsito**. Chapecó, SC, 2024.  
- Observatório Nacional de Segurança Viária. **Relatório Anual 2024**. São Paulo: ONSV, 2024.  

