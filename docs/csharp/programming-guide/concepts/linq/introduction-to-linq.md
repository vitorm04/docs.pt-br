---
title: Introdução ao LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: b8a577c7f1cb89df5534ae0eca893f4db434301e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596570"
---
# <a name="introduction-to-linq-c"></a>Introdução ao LINQ (C#)
O LINQ (consulta integrada à linguagem) é uma inovação introduzida no .NET Framework versão 3.5 que preenche a lacuna entre o mundo dos objetos e o mundo dos dados.  
  
 Tradicionalmente, consultas em dados são expressas como cadeias de caracteres simples sem verificação de tipo no tempo de compilação ou no suporte a IntelliSense. Além disso, você precisará aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: Bancos de dados SQL, documentos XML, vários serviços Web e assim por diante. O LINQ faz da *consulta* um constructo de linguagem de primeira classe no C#. Você escreve consultas em coleções fortemente tipadas de objetos usando palavras-chave da linguagem e operadores familiares.  
  
 É possível escrever consultas do LINQ em C# para bancos de dados do SQL Server, documentos XML, conjuntos de dados ADO.NET e qualquer coleção de objetos que dá suporte a <xref:System.Collections.IEnumerable> ou à interface genérica <xref:System.Collections.Generic.IEnumerable%601>. O suporte ao LINQ também é fornecido por terceiros para muitos serviços Web e outras implementações de banco de dados.  
  
 É possível usar consultas do LINQ em novos projetos ou em conjunto com consultas que não são do LINQ em projetos existentes. O único requisito é que o projeto tenha como alvo o .NET Framework 3.5 ou posterior.  
  
 A seguinte ilustração do Visual Studio mostra uma consulta LINQ parcialmente concluída em um banco de dados do SQL Server no C# e no Visual Basic, com verificação de tipo completa e suporte ao IntelliSense:  
  
 ![Diagrama que mostra uma consulta LINQ com o IntelliSense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a>Próximas etapas  
 Para obter mais detalhes sobre o LINQ, comece se familiarizando com alguns conceitos básicos na seção de introdução [Introdução a LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) e, em seguida, leia a documentação da tecnologia do LINQ na qual você está interessado:  
  
- Bancos de dados do SQL Server: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
- Documentos XML: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
- Conjunto de dados do ADO.NET: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
- Coleções do .NET, arquivos, cadeias de caracteres e assim por diante: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Consulte também

- [LINQ (consulta integrada à linguagem) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
