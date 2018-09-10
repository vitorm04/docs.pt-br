---
title: Introdução ao LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: 990a47d6ecfe38d9efa7d505eb3c23a28c05f58c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43740241"
---
# <a name="introduction-to-linq-c"></a>Introdução ao LINQ (C#)
O LINQ (consulta integrada à linguagem) é uma inovação introduzida no .NET Framework versão 3.5 que preenche a lacuna entre o mundo dos objetos e o mundo dos dados.  
  
 Tradicionalmente, consultas feitas em dados são expressas como cadeias de caracteres simples sem verificação de tipo no tempo de compilação ou suporte a IntelliSense. Além disso, você precisará aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: bancos de dados SQL, documentos XML, vários serviços Web etc. O LINQ faz da *consulta* um constructo de linguagem de primeira classe no C#. Você escreve consultas em coleções fortemente tipadas de objetos usando palavras-chave da linguagem e operadores familiares.  
  
 É possível escrever consultas do LINQ em C# para bancos de dados do SQL Server, documentos XML, conjuntos de dados ADO.NET e qualquer coleção de objetos que dá suporte a <xref:System.Collections.IEnumerable> ou à interface genérica <xref:System.Collections.Generic.IEnumerable%601>. O suporte ao LINQ também é fornecido por terceiros para muitos serviços Web e outras implementações de banco de dados.  
  
 É possível usar consultas do LINQ em novos projetos ou em conjunto com consultas que não são do LINQ em projetos existentes. O único requisito é que o projeto tenha como alvo o .NET Framework 3.5 ou posterior.  
  
 A ilustração a seguir do Visual Studio mostra uma consulta do LINQ parcialmente concluída em um banco de dados do SQL Server no C# e no Visual Basic, com verificação de tipo completa e suporte a IntelliSense.  
  
 ![Consulta de LINQ com Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>Próximas etapas  
 Para obter mais detalhes sobre o LINQ, comece se familiarizando com alguns conceitos básicos na seção de introdução [Introdução a LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) e, em seguida, leia a documentação da tecnologia do LINQ na qual você está interessado:  
  
-   Bancos de dados do SQL Server: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
-   Documentos XML: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   Conjuntos de dados ADO.NET: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
-   Coleções do .NET, arquivos, cadeias de caracteres etc.: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Consulte também

- [LINQ (Consulta Integrada à Linguagem) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
