---
title: "Introdu&#231;&#227;o ao LINQ (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Introdu&#231;&#227;o ao LINQ (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Consulta integrada à linguagem \(LINQ\) é que uma inovação introduzido no .NET Framework versão 3.5 que as pontes a lacuna entre o mundo de objetos e o mundo dos dados.  
  
 Tradicionalmente, consultas em dados são expressos como cadeias de caracteres simples sem verificação de tipo em compilar tempo ou suporte a IntelliSense. Além disso, você terá de aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: SQL bancos de dados, documentos XML, vários serviços da Web e assim por diante. LINQ faz um *consulta* uma construção de linguagem de primeira classe em c\#. Você escrever consultas em relação a coleções com rigidez de tipos de objetos usando palavras\-chave e operadores familiares.  
  
 Você pode escrever consultas LINQ em c\# para bancos de dados do SQL Server, documentos XML, Datasets ADO.NET e qualquer coleção de objetos que oferece suporte a <xref:System.Collections.IEnumerable> ou genérica <xref:System.Collections.Generic.IEnumerable%601> interface. Suporte a LINQ também é fornecido por terceiros para muitos serviços da Web e outras implementações de banco de dados.  
  
 Você pode usar consultas LINQ em novos projetos ou junto com consultas LINQ não em projetos existentes. O único requisito é que o projeto de destino do .NET Framework 3.5 ou posterior.  
  
 A ilustração a seguir do Visual Studio mostra uma consulta LINQ parcialmente concluída com um banco de dados do SQL Server em c\# e Visual Basic com verificação de tipo completo e suporte a IntelliSense.  
  
 ![Consulta LINQ com Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query\_Intell")  
  
## Próximas etapas  
 Para obter mais detalhes sobre o LINQ, comece se familiarizar com alguns conceitos básicos na seção Introdução [Introdução a LINQ em C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), e, em seguida, leia a documentação para a tecnologia LINQ no qual você está interessado:  
  
-   Bancos de dados do SQL Server: [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)  
  
-   Documentos XML: [LINQ to XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   Conjuntos de dados ADO.NET: [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
-   Coleções .NET, arquivos, cadeias de caracteres e assim por diante: [LINQ to Objects \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## Consulte também  
 [Consulta integrada à linguagem \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/index.md)