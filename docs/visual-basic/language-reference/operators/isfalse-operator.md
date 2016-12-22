---
title: "Operador IsFalse (Visual Basic) | Microsoft Docs"
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
  - "vb.isfalse"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador AndAlso"
  - "Operador IsFalse"
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador IsFalse (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Determina se uma expressão é `False`.  
  
 Você não pode chamar `IsFalse` explicitamente no código, mas o compilador Visual Basic pode usá\-lo para gerar código de cláusulas `AndAlso`.  Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo em uma cláusula `AndAlso`, você deve definir `IsFalse` na classe ou estrutura.  
  
 O compilador considera os operadores `IsFalse` e `IsTrue` como um  *par correspondente* .  Isso significa que se você definir um deles, você deverá também definir o outro.  
  
> [!NOTE]
>  O operador `IsFalse`pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefenir seu comportamento quando seu operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo de código a seguir define o contorno de uma estrutura que inclui as definições para operadores `IsFalse` e `IsTrue`.  
  
 [!CODE [VbVbalrOperators#28](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#28)]  
  
## Consulte também  
 [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)