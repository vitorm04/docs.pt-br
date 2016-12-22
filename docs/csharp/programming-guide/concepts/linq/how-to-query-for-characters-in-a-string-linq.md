---
title: "Como: consultar caracteres em uma cadeia de caracteres (LINQ) (c#) | Microsoft Docs"
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
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: consultar caracteres em uma cadeia de caracteres (LINQ) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Porque o <xref:System.String> classe implementa a <xref:System.Collections.Generic.IEnumerable%601> interface, qualquer cadeia de caracteres pode ser consultada como uma seqüência de caracteres. No entanto, isso não é um uso comum do LINQ. Para operações de correspondência de padrões complexos, use o <xref:System.Text.RegularExpressions.Regex> classe.  
  
## Exemplo  
 O exemplo a seguir consulta uma cadeia de caracteres para determinar o número de dígitos numéricos que ele contém. Observe que a consulta é "reutilizada" depois que ele é executado na primeira vez. Isso é possível porque a consulta em si não armazena os resultados reais.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou posterior, com uma referência a System.Core.dll e `using` diretivas para os namespaces System. LINQ e System.IO.  
  
## Consulte também  
 [LINQ e cadeias de caracteres \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)   
 [Como: combinar consultas LINQ com expressões regulares \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)