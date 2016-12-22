---
title: "Operador IsTrue (Visual Basic) | Microsoft Docs"
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
  - "vb.istrue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador IsTrue"
  - "Operador OrElse [Visual Basic]"
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador IsTrue (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Determina se uma expressão é `True`.  
  
 Você não pode chamar `IsTrue` explicitamente no código, mas o compilador Visual Basic pode usá\-lo para gerar código de cláusulas `OrElse`.  Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo em uma cláusula `OrElse`, você deve definir `IsTrue` na classe ou estrutura.  
  
 O compilador considera os operadores `IsTrue` e `IsFalse` como um  *par correspondente* .  Isso significa que se você definir um deles, você deverá também definir o outro.  
  
## Uso do compilador de IsTrue  
 Quando você tiver definido uma classe ou estrutura, você pode usar uma variável desse tipo em um `For`, `If`, `Else``If`, ou `While` instrução, ou em um `When` cláusula.  Se você fizer isso, o compilador requer um operador que converte seu tipo em um `Boolean` para que ele possa testar uma condição de valor.  Ele procura por um operador adequado na seguinte ordem:  
  
1.  Um operador de conversão de expansão de sua classe ou estrutura para `Boolean`.  
  
2.  Um operador de conversão de expansão de sua classe ou estrutura para `Boolean?`.  
  
3.  O `IsTrue` operador em sua classe ou estrutura.  
  
4.  Uma conversão de restrição para `Boolean?` que não envolve uma conversão de `Boolean` para `Boolean?`.  
  
5.  Um operador de conversão de restrição de sua classe ou estrutura para `Boolean`.  
  
 Se você não tiver definido a conversão em `Boolean` ou um `IsTrue` operador, o compilador sinaliza um erro.  
  
> [!NOTE]
>  O operador `IsTrue`pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefenir seu comportamento quando seu operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo de código a seguir define o contorno de uma estrutura que inclui as definições para operadores `IsFalse` e `IsTrue`.  
  
 [!CODE [VbVbalrOperators#28](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#28)]  
  
## Consulte também  
 [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)