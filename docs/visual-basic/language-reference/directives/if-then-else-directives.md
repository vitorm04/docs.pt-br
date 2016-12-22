---
title: "Diretivas #If...Then...#Else | Microsoft Docs"
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
  - "vb.#EndIf"
  - "#End If"
  - "#Then"
  - "#ElseIf"
  - "vb.#ElseIf"
  - "vb.#Else"
  - "vb.#If"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Diretiva #Else [Visual Basic]"
  - "Diretiva if #End [Visual Basic]"
  - "Diretiva #If [Visual Basic]"
  - "compilação condicional, Diretivas ()"
  - "diretiva else (#else)"
  - "compilação seletiva"
  - "código do Visual Basic, compilando"
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diretivas #If...Then...#Else
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Condicionalmente compila blocos de código Visual Basic selecionados.  
  
## Sintaxe  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## Partes  
 `expression`  
 Necessário para instruções `#If` e `#ElseIf`, opcionais em outro lugar.  Qualquer expressão, consistindo exclusivamente de uma ou mais constantes, literais e operadores de compilação condicional, que seja avaliada como `True` ou `False`.  
  
 `statements`  
 Obrigatório para bloco de declaração `#If`, opcional em outro lugar.  Visual Basic programa linhas ou diretivas de compilador que são compiladas se a expressão associada for avaliada como `True`.  
  
 `#End If`  
 Finaliza o bloco de declaração `#If`.  
  
## Comentários  
 Na superfície, o comportamento das diretivas `#If...Then...#Else` aparenta ser igual ao das instruções `If...Then...Else`.  No entanto, as diretivas `#If...Then...#Else` avaliam o que é compilado pelo compilador, enquanto as instruções `If...Then...Else` avaliam condições em tempo de execução.  
  
 Compilação condicional é normalmente usada para compilar o mesmo programa para diferentes plataformas.  Ela também é usado para evitar que o código depurado seja exibido em um arquivo executável.  Código excluído durante compilação condicional é completamente omitido do arquivo executável final, para que ele não tenha efeito sobre o tamanho ou desempenho.  
  
 Independentemente do resultado de qualquer avaliação, todas as expressões são avaliadas usando `Option Compare Binary`.  A instrução `Option Compare` não afeta as expressões nas instruções `#If` e `#ElseIf`.  
  
> [!NOTE]
>  Não exite formato de linha única das diretivas `#If`, `#Else`, `#ElseIf` e `#End If`.  Nenhum outro código pode aparecer na mesma linha que qualquer um das diretivas.  
  
## Exemplo  
 Este exemplo usa a construção `#If...Then...#Else` para determinar se determinadas instruções serão compiladas.  
  
 [!CODE [VbVbalrConditionalComp#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrConditionalComp#1)]  
  
## Consulte também  
 [Diretiva \#Const](../../../visual-basic/language-reference/directives/const-directive.md)   
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)