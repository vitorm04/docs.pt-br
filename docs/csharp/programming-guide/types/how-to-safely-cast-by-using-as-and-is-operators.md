---
title: "Como executar convers&#227;o cast com seguran&#231;a usando operadores as e is (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador as [C#]"
  - "operadores cast [C#], operadores as e is"
  - "Operador is [C#]"
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como executar convers&#227;o cast com seguran&#231;a usando operadores as e is (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Como os objetos são polimórficos, é possível que uma variável de um tipo de classe base para armazenar um tipo derivado.  Para acessar o método do tipo derivado, é necessário converter o valor de volta para o tipo derivado.  No entanto, para tentar uma simples cast nesses casos cria o risco de gerar um <xref:System.InvalidCastException>.  Isto é porque C\# fornece a  [é](../../../csharp/language-reference/keywords/is.md) e  [como](../../../csharp/language-reference/keywords/as.md) operadores.  Você pode usar esses operadores para testar se um elenco será bem\-sucedida sem causar uma exceção seja lançada.  Em geral, o `as` operador é mais eficiente porque, na verdade, retorna o valor de conversão se a conversão pode ser feita com êxito.  O `is` o operador retorna apenas um valor booleano.  Portanto, pode ser usado quando você apenas deseja determinar o tipo de um objeto, mas não precisa realmente lançá\-lo.  
  
## Exemplo  
 Os exemplos a seguir mostram como usar o `is` e `as` digite de operadores de conversão de uma referência para outro, sem o risco de gerar uma exceção.  O exemplo também mostra como usar o `as` operador com tipos de valor anulável.  
  
 [!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## Consulte também  
 [Tipos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Conversões cast e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md)