---
title: "Como corresponder uma cadeia de caracteres a um padr&#227;o (Visual Basic) | Microsoft Docs"
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
  - "operadores de comparação, comparando cadeias de caracteres"
  - "Operador Like [Visual Basic], correspondência padrão"
  - "operadores [Visual Basic], comparação"
  - "correspondência padrão"
  - "correspondência padrão, cadeias de caracteres vazias"
  - "correspondência padrão, comparação de cadeias de caracteres"
  - "comparação de cadeias de caracteres [Visual Basic]"
  - "comparação de cadeias de caracteres [Visual Basic], operadores"
  - "cadeias de caracteres {Visual Basic], comparando"
  - "código do Visual Basic, operadores"
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como corresponder uma cadeia de caracteres a um padr&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Se você quiser saber se uma expressão de [Tipo de dados da cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfaz um padrão, então você pode usar o [Operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like` leva dois operandos.  O operando esquerdo é uma expressão de seqüência de caracteres e o operando da direita é uma seqüência de caracteres que contém o padrão a ser usado para correspondência.  `Like`Retorna um `Boolean` valor que indica se a expressão de seqüência satisfaz o padrão.  
  
 Você pode fazer a correspondência entre cada caractere na expressão de sequência de caracteres e um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres.  As posições das especificações na sequência de caracteres de padrão correspondem às posições dos caracteres a ser verificados por correspondência na expressão em sequência de caracteres.  
  
### Para corresponder um caractere na expressão em sequência de caracteres com um caractere específico  
  
-   Coloque o caractere específico diretamente na sequência de caracteres do padrão.  Certos caracteres especiais devem ser colocados entre colchetes \(`[ ]`\).  Para obter mais informações, consulte [Operador Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     O exemplo a seguir testa se `myString` consiste exatamente do único caractere `H`.  
  
     [!CODE [VbVbalrOperators#70](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#70)]  
  
### Para corresponder um caractere na expressão em sequência de caracteres com um caractere curinga  
  
-   Coloque um ponto de interrogação \(`?`\) na sequência de caracteres do padrão.  Qualquer caractere válido nessa posição é uma correspondência com êxito.  
  
     O exemplo a seguir testa se `myString` consiste do único caractere `W` seguido por exatamente dois caracteres de quaisquer valores.  
  
     [!CODE [VbVbalrOperators#71](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#71)]  
  
### Para corresponder um caractere na expressão em sequência de caracteres com uma lista de caracteres  
  
-   Coloque colchetes \(`[ ]`\) na sequência de caracteres do padrão, e dentro dos colchetes coloque a lista de caracteres.  Não separe os caracteres com vírgulas ou qualquer outro separador.  Qualquer caractere único na lista é uma correspondência com êxito.  
  
     O exemplo a seguir testa se `myString` consiste de qualquer caractere válido seguido por exatamente um dos caracteres `A`, `C`, ou `E`.  
  
     [!CODE [VbVbalrOperators#72](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#72)]  
  
     Observe que essa correspondência diferencia maiúsculas de minúsculas.  
  
### Para corresponder um caractere na expressão em sequência de caracteres com um intervalo de caracteres  
  
-   Colocar colchetes \(`[ ]`\) na seqüência de caracteres padrão e dentro dos colchetes colocados os caracteres mais baixos e mais altos no intervalo, separados por um hífen \(`–`\).  Qualquer caractere único dentro do intervalo é uma correspondência com êxito.  
  
     O exemplo a seguir testa se `myString` consiste dos caracteres `num` seguidos por exatamente um dos caracteres `i`, `j`, `k`, `l`, `m`, ou `n`.  
  
     [!CODE [VbVbalrOperators#73](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#73)]  
  
     Observe que essa correspondência diferencia maiúsculas de minúsculas.  
  
## Correspondência de sequências de caracteres vazias  
 `Like` trata a sequência `[]` como uma sequência de caracteres de comprimento nulo \(`""`\).  Você pode usar `[]` para testar se a expressão de sequência de caracteres inteira está vazia, mas você não pode usá\-los para testar se uma determinada posição na expressão de sequência de caracteres está vazia.  Se uma posição vazia é uma das opções necessárias para testar, você pode usar `Like` mais de uma vez.  
  
#### Para corresponder um caractere na expressão em sequência de caracteres com uma lista de caracteres ou nenhum caractere  
  
1.  Chame o operador `Like` duas vezes na mesma expressão em sequência, e conecte as duas chamadas com o [Operador Or](../../../../visual-basic/language-reference/operators/or-operator.md) ou o [Operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2.  Na sequência de caracteres do padrão para a primeira cláusula `Like`, inclua a lista de caracteres entre colchetes \(`[ ]`\).  
  
3.  Na sequência de caracteres do padrão para a segunda cláusula `Like`, não coloque nenhum caractere na posição em questão.  
  
     O exemplo a seguir testa o número de telefone de sete dígitos `phoneNum` para exatamente três dígitos numéricos, seguido por um espaço, um hífen \(`–`\), um período \(`.`\), ou nenhum caractere, seguido de exatamente quatro dígitos numéricos.  
  
     [!CODE [VbVbalrOperators#74](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#74)]  
  
## Consulte também  
 [Operadores de comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operadores e expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Operador Like](../../../../visual-basic/language-reference/operators/like-operator.md)   
 [Tipo de dados da cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md)