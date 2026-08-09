# **"FWMsPrinter ::: Imagem maior que 1Mb sem path absoluto..."**

Quem trabalha com **FWMsPrinter** provavelmente já encontrou essa mensagem:

> *"Imagem maior que 1Mb sem path absoluto, verifique o caminho da imagem informado no 3º parâmetro do método SayBitmap..."*

Na prática, imagens maiores que **1 MB** acabam exigindo que o arquivo esteja disponível localmente antes da impressão.

Até aí, beleza.

O problema surgiu quando percebi que, dependendo da quantidade de imagens, **o gargalo deixava de ser a impressão e passava a ser a transferência dos arquivos**.

E aí lembrei de uma premissa muito divulgada dentro da TOTVS:

> **Somos Inconformados.**

Pois bem...

🥷 **Eu fui me inconformar justamente com a transferência.** 😂

Em vez de aceitar o tradicional:

**"é assim mesmo..."**

resolvi fazer aquilo que costuma estragar esse argumento:

📊 **benchmark.**

Testei as alternativas, medi os tempos e coloquei todo mundo para correr na mesma pista.

### 📊 Resultado do benchmark

| Estratégia                      | Tempo total | Comparação com a vencedora |
| ------------------------------- | ----------: | -------------------------: |
| 🥷 **GetDataFromServerWithZip** | **58,12 s** |                  **1,00x** |
| ⚡ DNATech FILECOPY              |       1m38s |       **1,69x mais lento** |
| 📦 TOTVS CPYS2TZip              |       4m37s |       **4,77x mais lento** |
| 🐢 TOTVS CPYS2T                 |       6m00s |       **6,20x mais lento** |

Os tempos acumulados medidos foram aproximadamente **58,12 s**, **98,19 s**, **277,08 s** e **360,10 s**, respectivamente. 

Mas aqui apareceu a parte mais interessante do problema.

`FILECOPY`, `CPYS2T` e `CPYS2TZip` estavam trabalhando essencialmente com a lógica de **transferir os arquivos individualmente**.

Então veio a pergunta inconveniente:

> **"E se, em vez de tentar fazer cada transferência ficar menos lenta, eu simplesmente parar de fazer dezenas de transferências?"**

💡 Bingo.

A estratégia com **GetDataFromServerWithZip** passou a baixar **todo o conjunto de arquivos de uma única vez**.

No teste, foram aproximadamente **65,5 MB em 58 segundos**. 

### E os números ficaram interessantes:

🚀 **40,8% mais rápido** que minha própria solução baseada em FILECOPY.

🚀 **79,0% mais rápido** que CPYS2TZip.

🚀 **83,9% mais rápido** que CPYS2T.

Ou olhando de outro jeito:

**CPYS2T levou aproximadamente 6,2 vezes o tempo da solução em lote.**

E aí está uma das coisas que mais gosto em desenvolvimento:

Às vezes você não precisa otimizar o algoritmo existente.

Você precisa olhar para ele e perguntar:

> **"Por que estou fazendo isso desse jeito?"**

É a velha diferença entre:

🐢 *"Como faço esse loop rodar mais rápido?"*

e

🥷 *"Preciso mesmo desse loop?"*

😂

E o objetivo continua sendo o mesmo:

✅ reduzir o tempo de espera;

✅ diminuir o impacto antes da geração da impressão;

✅ esconder a complexidade técnica;

✅ e facilitar a vida de quem realmente importa nessa história: **o usuário.**

Porque o cliente não quer saber se usei `CPYS2T`, ZIP, stream, compactação, transferência em lote ou magia negra do AppServer.

Ele clicou em:

**IMPRIMIR.**

E espera, veja só que absurdo...

**que imprima.** 😂

No final, minha maior conclusão desse benchmark não foi que eu tinha uma função mais rápida.

Foi perceber que havia uma **estratégia melhor**.

E talvez seja exatamente isso que significa ser inconformado:

Não aceitar o gargalo.

Não apenas contorná-lo.

Mas perguntar se ele realmente precisa existir.

🥷 Sendo assim, solicito formalmente minha promoção para:

**#InconformadoMor**

---

#TOTVS #Protheus #AdvPL #TLPP #FWMsPrinter #Performance #Benchmark #Otimização #SoftwareEngineering #EngenhariaDeSoftware #ProblemSolving #DeveloperLife #PerformanceTuning #Automação #Produtividade #DNATech #InconformadoMor

---
