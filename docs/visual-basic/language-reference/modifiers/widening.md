---
title: "Widening (Visual Basic) | Microsoft Docs"
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
  - "vb.widening"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversões de tipo"
  - "conversão de tipo"
  - "conversões de tipo de dados"
  - "palavra-chave Widening"
  - "conversão de tipo de dados"
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Widening (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indica que um operador de conversão \(`CType`\) converte uma classe ou estrutura para um tipo que pode conter todos os possíveis valores da classe ou estrutura original.  
  
## Convertendo com a palavra\-chave Widening  
 O procedimento de conversão deve especificar `Public Shared` além `Widening`.  
  
 Conversões de ampliação sempre são bem\-sucedidas em tempo de execução e nunca provocam perda de dados. Os exemplos são `Single` para `Double`, `Char` para `String`, e um tipo derivado para seu tipo base. Essa última conversão está ampliando porque o tipo derivado contém todos os membros do tipo base e, portanto, é uma instância do tipo base.  
  
 O código consumidor não precisa usar `CType` para ampliação conversões, mesmo se `Option Strict` é `On`.  
  
 O `Widening` palavra\-chave pode ser usada neste contexto:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Por exemplo, definições de widening e narrowing operadores de conversão, consulte [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## Consulte também  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)