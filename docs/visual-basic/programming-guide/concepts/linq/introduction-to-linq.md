---
title: "Introdução ao LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de34f27bc520c4e814738e0ba22620ed80f7f23e
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="introduction-to-linq-visual-basic"></a>Introdução ao LINQ (Visual Basic)
O LINQ (consulta integrada à linguagem) é uma inovação introduzida no .NET Framework versão 3.5 que preenche a lacuna entre o mundo dos objetos e o mundo dos dados.  
  
 Tradicionalmente, consultas feitas em dados são expressas como cadeias de caracteres simples sem verificação de tipo no tempo de compilação ou suporte a IntelliSense. Além disso, você terá de aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: bancos de dados SQL, documentos XML, vários serviços Web e etc. LINQ faz um *consulta* uma construção de linguagem de primeira classe no Visual Basic. Você escreve consultas em coleções fortemente tipadas de objetos usando palavras-chave da linguagem e operadores familiares.  
  
 Você pode escrever consultas LINQ no Visual Basic para bancos de dados do SQL Server, documentos XML, conjuntos de dados ADO.NET e qualquer coleção de objetos que oferece suporte a <xref:System.Collections.IEnumerable> ou genérica <xref:System.Collections.Generic.IEnumerable%601> interface. O suporte ao LINQ também é fornecido por terceiros para muitos serviços Web e outras implementações de banco de dados.  
  
 É possível usar consultas do LINQ em novos projetos ou em conjunto com consultas que não são do LINQ em projetos existentes. O único requisito é que o projeto tenha como alvo o .NET Framework 3.5 ou posterior.  
  
 A ilustração a seguir do Visual Studio mostra uma consulta do LINQ parcialmente concluída em um banco de dados do SQL Server no C# e no Visual Basic, com verificação de tipo completa e suporte a IntelliSense.  
  
 ![Consulta de LINQ com Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>Próximas etapas  
 Para obter mais detalhes sobre o LINQ, iniciar, familiarize-se com alguns conceitos básicos da seção Introdução [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), e, em seguida, leia a documentação para a tecnologia LINQ no qual você está interessado:  
  
-   Bancos de dados do SQL Server: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
-   Documentos XML: [LINQ para XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   Conjuntos de dados ADO.NET: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
-   Coleções do .NET, arquivos, cadeias de caracteres e assim por diante: [LINQ para objetos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Consulte também  
 [LINQ (consulta integrada à linguagem) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
