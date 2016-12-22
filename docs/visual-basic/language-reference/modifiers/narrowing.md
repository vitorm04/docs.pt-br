---
title: "Narrowing (Visual Basic) | Microsoft Docs"
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
  - "vb.narrowing"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversões,   (tipo de dados)"
  - "conversões, Tipo "
  - "conversão de tipo de dados"
  - "palavra-chave Narrowing"
  - "conversão de tipo"
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Narrowing (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indica que um operador de conversão \(`CType`\) converte uma classe ou estrutura em um tipo que pode não conseguir armazenar alguns dos possíveis valores da classe original ou estrutura.  
  
## Convertendo com a Palavra\-Chave Narrowing  
 O procedimento de conversão deve especificar `Public Shared`, bem como `Narrowing`.  
  
 Conversões de restrição não são sempre bem\-sucedidas em tempo de execução e podem falhar ou provoca perda de dados.  Exemplos são `Long` para `Integer`, `String` para `Date` e um tipo base para um tipo derivado.  Esta último conversão é restritiva porque o tipo base pode não conter todos os membros do tipo derivado e,  portanto, não é uma instância do tipo derivado.  
  
 Se `Option Strict` estiver `On`, o código consumidor deve usar `CType` para todas as conversões redutoras.  
  
 A palavra\-chave `Narrowing` pode ser usada nos seguintes contextos:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## Consulte também  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)