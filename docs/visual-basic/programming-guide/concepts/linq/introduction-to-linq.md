---
title: Introdução ao LINQ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 2900cade8bc4166cccb62baf4381cb926cdff5f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614526"
---
# <a name="introduction-to-linq-visual-basic"></a>Introdução ao LINQ (Visual Basic)
O LINQ (consulta integrada à linguagem) é uma inovação introduzida no .NET Framework versão 3.5 que preenche a lacuna entre o mundo dos objetos e o mundo dos dados.  
  
 Tradicionalmente, consultas em dados são expressas como cadeias de caracteres simples sem verificação de tipo no tempo de compilação ou no suporte a IntelliSense. Além disso, você precisará aprender uma linguagem de consulta diferente para cada tipo de fonte de dados: Bancos de dados SQL, documentos XML, vários serviços Web e assim por diante. LINQ faz uma *consulta* uma construção de linguagem de primeira classe no Visual Basic. Você escreve consultas em coleções fortemente tipadas de objetos usando palavras-chave da linguagem e operadores familiares.  
  
 Você pode escrever consultas LINQ no Visual Basic para bancos de dados do SQL Server, documentos XML, conjuntos de dados ADO.NET e qualquer coleção de objetos que dá suporte a <xref:System.Collections.IEnumerable> ou o genérico <xref:System.Collections.Generic.IEnumerable%601> interface. O suporte ao LINQ também é fornecido por terceiros para muitos serviços Web e outras implementações de banco de dados.  
  
 É possível usar consultas do LINQ em novos projetos ou em conjunto com consultas que não são do LINQ em projetos existentes. O único requisito é que o projeto tenha como alvo o .NET Framework 3.5 ou posterior.  
  
 A ilustração a seguir do Visual Studio mostra uma consulta do LINQ parcialmente concluída em um banco de dados do SQL Server no C# e no Visual Basic, com verificação de tipo completa e suporte a IntelliSense.  
  
 ![Diagrama que shwos uma consulta LINQ com Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a>Próximas etapas  
 Para obter mais detalhes sobre o LINQ, comece se familiarizando com alguns conceitos básicos na seção de Introdução [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), e, em seguida, leia a documentação para a tecnologia LINQ na qual você está está interessado:  
  
- Bancos de dados do SQL Server: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
- Documentos XML: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
- Conjunto de dados do ADO.NET: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
- Coleções do .NET, arquivos, cadeias de caracteres e assim por diante: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Consulte também

- [LINQ (consulta integrada à linguagem) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
