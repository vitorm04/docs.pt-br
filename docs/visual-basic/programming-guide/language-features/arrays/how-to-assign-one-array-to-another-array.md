---
title: "Como atribuir uma matriz a outra matriz (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "matrizes [Visual Basic], atribuindo"
  - "matrizes [Visual Basic], covariância"
  - "covariância, matrizes"
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como atribuir uma matriz a outra matriz (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Como matrizes são objetos, você pode usá\-las em instruções de atribuição como outros tipos de objeto.  Uma variável de matriz contém um ponteiro para os dados que constituem os elementos da matriz e as informações de posição e comprimento, e uma atribuição copia somente esse ponteiro.  
  
### Para atribuir uma matriz a outra matriz  
  
1.  Garanta que as duas matrizes têm a mesma ordem \(número de dimensões\) e tipos de dados de elemento compatíveis.  
  
2.  Use uma instrução de atribuição padrão para atribuir a matriz de origem para a matriz de destino.  Não coloque parênteses após o nome da matriz.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Quando você atribui uma matriz à outra, as seguintes regras se aplicam:  
  
-   **Ordens iguais.** A ordem \(número de dimensões\) da matriz de destino deve ser a mesmo da matriz de origem.  
  
     Contanto que as ordens das duas matrizes sejam iguais, as dimensões não precisam ser iguais.  O número de elementos em uma determinada dimensão pode mudar durante a atribuição.  
  
-   **Tipos de elemento.** Tanto as duas matrizes devem ter  *tipo de referência* elementos ou as duas matrizes devem ter  *tipo de valor* elementos.  Para obter mais informações, consulte [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Se as duas matrizes têm elementos de tipo de valor, os tipos de dados dos elementos devem ser exatamente os mesmos.  A única exceção a isso é que você pode atribuir uma matriz de elementos `Enum` a uma matriz de tipo base de `Enum`.  
  
    -   Se as duas matrizes têm elementos de tipo de referência, o tipo de elemento de origem deve derivar do tipo de elemento de destino.  Quando esse for o caso, as duas matrizes têm a mesma relação de herança que seus elementos.  Isso é chamado *covariância de matrizes*.  
  
 O compilador relata um erro se as regras acima são violadas, por exemplo se os tipos de dados não forem compatíveis ou as ordens forem desiguais.  Você pode adicionar manipulação de erro a seu código para verificar se as matrizes são compatíveis antes de tentar uma atribuição.  Você também pode usar a palavra\-chave [Operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) se você quiser evitar lançar uma exceção.  
  
## Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Solucionando problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)