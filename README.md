# Relatório da NOME DA ATIVIDADE

**Disciplina:** 
**Aluno(s):** kelvin raphael de souza pereira 
**Turma:**
**Professor:**
**Data:**

---

# 1. Descrição do Problema

O problema consiste em somar todos os valores contidos em um arquivo de números inteiros (numero2.txt), que possui 10 milhões de linhas. O objetivo é avaliar o desempenho da soma usando execução serial e paralela com diferentes números de threads, medindo tempo, speedup e eficiência.

Algoritmo utilizado: soma sequencial por linha, paralelizada dividindo o arquivo em blocos e somando cada bloco em threads.

Tamanho da entrada: 10.000.000 números.

Objetivo da paralelização: reduzir o tempo de execução da soma utilizando múltiplas threads.

Complexidade aproximada: O algoritmo tem complexidade O(n), onde n é o número de linhas do arquivo.
---

# 2. Ambiente Experimental

Descreva o ambiente em que os experimentos foram realizados.

## Orientações

Informar as características do hardware e software utilizados na execução dos testes.

| Item                        | Descrição |
| --------------------------- | --------- |
| Processador                 |12th Gen Intel(R) Core(TM) i5-12500            |
| Número de núcleos           |6 nucleos           |
| Memória RAM                 |16,0 GB            |
| Sistema Operacional         |Windows 11           |
| Linguagem utilizada         |Python 3   |
| Biblioteca de paralelização |           |
| Compilador / Versão         |Python 3.10|

---

# 3. Metodologia de Testes

Medição de tempo: Utilizou-se time.time() antes e depois da execução da soma.

Número de execuções: 1 execução por configuração (arquivo grande).

Entrada utilizada: arquivo numero2.txt com 10 milhões de números.

Configurações testadas:

1 thread (serial)

2 threads

4 threads

6 threads

12 threads

Procedimento experimental:

O arquivo foi lido em blocos de 1 milhão de linhas.

Cada bloco foi distribuído entre as threads, que somaram os valores de forma paralela.

O tempo de execução foi registrado em segundos.

# 4. Resultados Experimentais

Preencha a tabela com os **tempos médios de execução** obtidos.

## Orientações

* O tempo deve ser informado em **segundos**
* Utilizar a **média das execuções**

| Nº Threads/Processos | Tempo de Execução (s) |
| -------------------- | --------------------- |
| 1                    |      1,324963         |
| 2                    |      1.280188         |
| 4                    |      1.240317         |
| 8                    |      1.208345         |
| 12                   |      1.289748         |

---

# 5. Cálculo de Speedup e Eficiência

Fórmulas utilizadas:

Speedup(p) = T(1) / T(p)

Eficiência(p) = Speedup(p) / p

---

# 6. Tabela de Resultados

Preencha a tabela abaixo utilizando os tempos medidos.

| Threads/Processos | Tempo (s) | Speedup | Eficiência |
| ----------------- | --------- | ------- | ---------- |
| 1                 |1.356551    1.0     | 1.0        |
| 2                 |1.280188   | 1.06   | 0,53       |
| 4                 |1.240317   | 1.09   | 0,27       |
| 8                 |1.208345   | 1.12   | 0,14       |
| 12                |1.289748   | 1,05   | 0,9        |

---

# 7. Gráfico de Tempo de Execução

Orientações:

Eixo X: número de threads/processos

Eixo Y: tempo de execução (s)

Observação: Gráfico mostra que o tempo não diminui significativamente com o aumento de threads.
file:///C:/Users/aluno/Downloads/execucao.png

---

# 8. Gráfico de Speedup

Observação: O speedup obtido é menor que 1, indicando que o paralelismo via threads não acelerou a soma devido ao GIL no Python.
Inserir o gráfico abaixo:



---

# 9. Gráfico de Eficiência

Observação: A eficiência cai rapidamente à medida que o número de threads aumenta, mostrando overhead da paralelização.
Inserir o gráfico abaixo:

file:///C:/Users/aluno/Pictures/Screenshots/eficiencia.png

---

# 10. Análise dos Resultados

O speedup obtido não foi próximo do ideal.

A aplicação não apresentou escalabilidade com threads devido ao GIL.

A eficiência começou a cair já a partir de 2 threads.

O número de threads testado ultrapassa o número de núcleos físicos, agravando o overhead.

Houve overhead de paralelização e contenção de memória, já que as threads compartilham o mesmo processo e não executam em paralelo de verdade para operações CPU-bound.

Possíveis causas:

Perda de desempenho causada pelo overhead de criação e gerenciamento de threads.

Sincronização mínima, mas ainda necessária para coletar resultados.

Comunicação entre threads e contenção de memória/cache.

---

# 11. Conclusão

O paralelismo via threads não trouxe ganho significativo de desempenho para a soma de números inteiros em Python.

O melhor desempenho foi obtido com 1 thread (serial).

O programa não escala bem com o aumento do número de threads.

Para melhoria: usar multiprocessing ou bibliotecas vetorizadas como NumPy, que contornam o GIL e permitem verdadeiro paralelismo em CPU-bound.

