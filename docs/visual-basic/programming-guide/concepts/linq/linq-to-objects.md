---
title: "LINQ to Objects (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# LINQ to Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O termo "LINQ to Objects" refere\-se ao uso do LINQ consulta com qualquer <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601> coleção diretamente, sem o uso de um provedor LINQ intermediário ou API como [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) ou [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Você pode usar o LINQ para consultar qualquer coleção enumerável como <xref:System.Collections.Generic.List%601>, <xref:System.Array>, ou <xref:System.Collections.Generic.Dictionary%602>. A coleção pode ser definido pelo usuário ou pode ser retornada por uma API do .NET Framework.  
  
 Basicamente, o LINQ to Objects representa uma nova abordagem para coleções. Na forma antiga, você precisava escrever complexas `For Each` loops que especificou como recuperar dados de uma coleção. A abordagem do LINQ, você escreve código declarativo que descreve o que você deseja recuperar.  
  
 Além disso, consultas LINQ oferecem três principais vantagens tradicionais `For Each` loops:  
  
1.  Eles são mais concisas e legíveis, especialmente quando várias condições de filtragem.  
  
2.  Eles fornecem poderosa filtragem, classificação e agrupamento de recursos com um mínimo de código do aplicativo.  
  
3.  Elas podem ser movidas para outras fontes de dados com pouca ou nenhuma modificação.  
  
 Em geral, quanto mais complexa a operação que você deseja executar nos dados, o maior benefício você perceberá usando LINQ em vez de técnicas tradicionais de iteração.  
  
 O objetivo desta seção é demonstrar a abordagem do LINQ com alguns exemplos selecionados. Ele não se destina a ser completa.  
  
## Nesta seção  
 [LINQ e cadeias de caracteres \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 Explica como o LINQ pode ser usado para consultar e transformar coleções de cadeias de caracteres e cadeias de caracteres. Também inclui links para tópicos que demonstram esses princípios.  
  
 [LINQ e reflexão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Links para um exemplo que demonstra como LINQ usa reflexão.  
  
 [LINQ e diretórios de arquivos \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Explica como o LINQ pode ser usado para interagir com sistemas de arquivos. Também inclui links para tópicos que demonstram esses conceitos.  
  
 [Como: consultar um ArrayList com LINQ \(Visual Basic\)](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ%20\(Visual%20Basic\).md)  
 Demonstra como consultar um ArrayList no c\#.  
  
 [Como: adicionar métodos personalizados para consultas LINQ \(Visual Basic\)](../Topic/How%20to:%20Add%20Custom%20Methods%20for%20LINQ%20Queries%20\(Visual%20Basic\).md)  
 Explica como estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando métodos de extensão para o <xref:System.Collections.Generic.IEnumerable%601> interface.  
  
 [Consulta integrada à linguagem \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Fornece links para tópicos que explicam o LINQ e fornecem exemplos de código que executam consultas.