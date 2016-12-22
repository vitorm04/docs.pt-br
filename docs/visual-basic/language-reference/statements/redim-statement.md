---
title: "Instru&#231;&#227;o ReDim (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ReDim"
  - "vb.Preserve"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "matrizes [Visual Basic], e escalares"
  - "matrizes [Visual Basic], declarando"
  - "matrizes [Visual Basic], dimensões"
  - "matrizes [Visual Basic], realocando"
  - "matrizes [Visual Basic], reinicializando"
  - "palavra-chave As, instrução in ReDim"
  - "tipos de dados [Visual Basic], atribuindo"
  - "instruções de declaração"
  - "declarações, matrizes dinâmicas"
  - "matrizes dinâmicas, Instrução ReDim"
  - "cadeias de caracteres de comprimento fixo, declarando"
  - "palavra-chave Preserve, Instrução ReDim"
  - "Instrução ReDim"
  - "Instrução ReDim, sintaxe"
  - "variáveis escalares"
  - "escalares"
  - "escalares, e matrizes"
  - "storage, alocando"
  - "palavra-chave To, Instrução ReDim"
  - "variáveis [Visual Basic], escalar"
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o ReDim (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Realoca espaço de armazenamento para uma variável de matriz.  
  
## Sintaxe  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## Partes  
  
|Termo|Definição|  
|-----------|---------------|  
|`Preserve`|Opcional.  Modificador usado para preservar os dados na matriz existente quando você alterar o tamanho de somente a última dimensão.|  
|`name`|Obrigatório.  Nome da variável de matriz.  Consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Obrigatório.  Lista de limites de cada dimensão da matriz redefinida.|  
  
## Comentários  
 Você pode usar o `ReDim` instrução para alterar o tamanho de uma ou mais dimensões de um array que já foi declarado.  Se você tiver uma matriz grande e você não precisa mais alguns de seus elementos `ReDim` pode liberar memória, reduzindo o tamanho da matriz.  Por outro lado, se sua matriz precisar de mais elementos, `ReDim` pode adicioná\-los.  
  
 O `ReDim` instrução é destinada apenas para matrizes.  Não é válido em estruturas, coleções ou escalares \(variáveis que contêm apenas um único valor\).  Observe que, se você declarar uma variável para ser do tipo `Array`, o `ReDim` instrução não tem informações de tipo suficientes para criar a nova matriz.  
  
 Você pode usar `ReDim` apenas no nível de procedimento.  Portanto, o contexto da declaração da variável deve ser um procedimento. ele não pode ser um arquivo de origem, um namespace, uma interface, uma classe, uma estrutura, um módulo ou um bloco.  Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## Regras  
  
-   **Diversas variáveis.** Você pode redimensionar diversas variáveis de matriz na mesma instrução de declaração e especificar o `name` e `boundlist` partes para cada variável.  Diversas variáveis são separadas por vírgulas.  
  
-   **Limites de matriz.** Cada entrada na `boundlist` pode especificar os limites inferior e superior da dimensão.  O limite inferior é sempre 0 \(zero\).  O limite superior é o maior valor de índice possíveis para essa dimensão, não o comprimento da dimensão \(que é o limite superior mais um\).  O índice para cada dimensão pode variar de 0 a seu valor de limite superior.  
  
     O número de dimensões no `boundlist` deve corresponder ao número original de dimensões \(classificação\) da matriz.  
  
-   **Tipos de dados.** O `ReDim` instrução não é possível alterar o tipo de dados de uma variável de matriz ou seus elementos.  
  
-   **Inicialização.** O `ReDim` instrução não pode fornecer novos valores de inicialização para os elementos da matriz.  
  
-   **Classificação.** O `ReDim` instrução não pode mudar o grau \(número de dimensões\) da matriz.  
  
-   **Redimensionamento de preservar.** Se você usar `Preserve`, você pode redimensionar a última dimensão da matriz.  Para cada dimensão, você deve especificar o limite da matriz existente.  
  
     Por exemplo, se a matriz tem apenas uma dimensão, redimensionar dimensão e ainda manter todo o conteúdo da matriz, porque você está alterando a última vez e somente a dimensão.  No entanto, se a matriz tem dois ou mais dimensões, você pode alterar o tamanho da dimensão somente última de se você usar `Preserve`.  
  
-   **Propriedades.** Você pode usar `ReDim` em uma propriedade que contém uma matriz de valores.  
  
## Comportamento  
  
-   **Matriz substituição.** `ReDim` libera a matriz existente e cria uma nova matriz com a mesma classificação.  Nova matriz substitui a matriz lançada na variável de matriz.  
  
-   **Inicialização sem preservar.** Se você não especificar `Preserve`, `ReDim` inicializa os elementos da nova matriz usando o valor padrão para seu tipo de dados.  
  
-   **Inicialização com preservar.** Se você especificar `Preserve`, Visual Basic copia os elementos da matriz existente para a nova matriz.  
  
## Exemplo  
 O exemplo a seguir aumenta o tamanho da última dimensão de uma matriz dinâmica sem perder os dados existentes na matriz e, em seguida, diminui o tamanho com perda de dados parcial.  Por fim, ele diminui o tamanho de volta para seu valor original e reinicializa todos os elementos da matriz.  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 O `Dim` instrução cria uma nova matriz com três dimensões.  Cada dimensão é declarado com um limite de 10, para que o índice de matriz para cada dimensão pode variar de 0 a 10.  Na discussão a seguir, três dimensões são denominadas camada, linha e coluna.  
  
 A primeira `ReDim` cria uma nova matriz que substitui a matriz existente na variável `intArray`.  `ReDim` copia todos os elementos da matriz existente na nova matriz.  Também adiciona 10 mais colunas ao final de cada linha de cada camada e inicializa os elementos nas novas colunas como 0 \(o valor padrão de `Integer`, que é o tipo de elemento da matriz\).  
  
 A segunda `ReDim` cria outra nova matriz e copia todos os elementos que se encaixam.  No entanto, cinco colunas forem perdidas no final de cada linha de cada camada.  Isso não é um problema se você terminar de usar essas colunas.  Reduzindo o tamanho de uma matriz grande pode liberar memória que não é mais necessário.  
  
 A terceira `ReDim` cria outro novo array e remove outro cinco colunas do final de cada linha de cada camada.  Dessa vez não copia os elementos existentes.  Essa instrução reverte a matriz ao seu tamanho original.  Como a instrução não inclui o `Preserve` modificador, ele define todos os elementos da matriz para seus valores padrão originais.  
  
 Para obter exemplos adicionais, consulte [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## Consulte também  
 <xref:System.IndexOutOfRangeException>   
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Instrução Erase](../../../visual-basic/language-reference/statements/erase-statement.md)   
 [nada](../../../visual-basic/language-reference/nothing.md)   
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)