---
title: "Introdu&#231;&#227;o ao LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Introdu&#231;&#227;o ao LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Consulta integrada à linguagem \(LINQ\) é que uma inovação introduzido no .NET Framework versão 3.5 que as pontes a lacuna entre o mundo de objetos e o mundo dos dados.  
  
 Tradicionalmente, consultas em dados são expressos como cadeias de caracteres simples sem verificação de tipo em compilar tempo ou suporte a IntelliSense. Além disso, você terá de aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: SQL bancos de dados, documentos XML, vários serviços da Web e assim por diante. LINQ faz um *consulta* uma construção de linguagem de primeira classe no Visual Basic. Você escrever consultas em relação a coleções com rigidez de tipos de objetos usando palavras\-chave e operadores familiares.  
  
 Você pode escrever consultas LINQ no Visual Basic para bancos de dados do SQL Server, documentos XML, Datasets ADO.NET e qualquer coleção de objetos que oferece suporte a <xref:System.Collections.IEnumerable> ou genérica <xref:System.Collections.Generic.IEnumerable%601> interface. Suporte a LINQ também é fornecido por terceiros para muitos serviços da Web e outras implementações de banco de dados.  
  
 Você pode usar consultas LINQ em novos projetos ou junto com consultas LINQ não em projetos existentes. O único requisito é que o projeto de destino do .NET Framework 3.5 ou posterior.  
  
 A ilustração a seguir do Visual Studio mostra uma consulta LINQ parcialmente concluída com um banco de dados do SQL Server em c\# e Visual Basic com verificação de tipo completo e suporte a IntelliSense.  
  
 ![Consulta LINQ com Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query\_Intell")  
  
## Próximas etapas  
 Para obter mais detalhes sobre o LINQ, comece se familiarizar com alguns conceitos básicos na seção Introdução [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), e, em seguida, leia a documentação para a tecnologia LINQ no qual você está interessado:  
  
-   Bancos de dados do SQL Server: [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)  
  
-   Documentos XML: [LINQ to XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   Conjuntos de dados ADO.NET: [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
-   Coleções .NET, arquivos, cadeias de caracteres e assim por diante: [LINQ to Objects \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## Consulte também  
 [Consulta integrada à linguagem \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/index.md)