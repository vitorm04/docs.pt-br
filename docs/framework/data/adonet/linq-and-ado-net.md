---
title: LINQ e o ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: e24473f68fe5ccd993c5d205660ea8f397b6f797
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980087"
---
# <a name="linq-and-adonet"></a>LINQ e o ADO.NET
Today, many business developers must use two (or more) programming languages: a high-level language for the business logic and presentation layers (such as Visual C# or Visual Basic), and a query language to interact with the database (such as Transact-SQL). Isso exige que o desenvolvedor seja proficiente em várias linguagens para ser eficaz e também provoca incompatibilidades de linguagens no ambiente de desenvolvimento. Por exemplo, um aplicativo que usa uma API de acesso a dados para executar uma consulta em um banco de dados especifica a consulta como um literal de cadeia de caracteres usando aspas. Essa cadeia de caracteres de consulta é ilegível para o compilador e os erros não são verificados, como sintaxe inválida ou se as colunas ou linhas referenciadas realmente existem. Não há nenhuma verificação do tipo dos parâmetros da consulta e também nenhum suporte do `IntelliSense`.  
  
 Language-Integrated Query (LINQ) enables developers to form set-based queries in their application code, without having to use a separate query language. You can write LINQ queries against various enumerable data sources (that is, a data source that implements the <xref:System.Collections.IEnumerable> interface), such as in-memory data structures, XML documents, SQL databases, and <xref:System.Data.DataSet> objects. Embora essas fontes de dados enumeráveis sejam implementadas de várias maneiras, todas elas expõem as mesmas sintaxe e constructos de linguagem. Como as consultas podem ser formadas na própria linguagem de programação, você não precisa usar outra linguagem de consulta que seja inserida como literais de cadeia de caracteres que não podem ser compreendidos ou verificados pelo compilador. Integrating queries into the programming language also enables Visual Studio programmers to be more productive by providing compile-time type and syntax checking, and `IntelliSense`. Esses recursos reduzem a necessidade de depuração da consulta e de correção de erros.  
  
 A transferência de dados de tabelas SQL para objetos na memória é geralmente tediosa e sujeita a erros. The LINQ provider implemented by LINQ to DataSet and [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] converts the source data into <xref:System.Collections.IEnumerable>-based object collections. O programador sempre exibe os dados como uma coleção de <xref:System.Collections.IEnumerable>, quando você consulta e quando você atualiza. Suporte completo do `IntelliSense` é fornecido para escrever consultas nessas coleções.  
  
 There are three separate ADO.NET Language-Integrated Query (LINQ) technologies: LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], and LINQ to Entities. LINQ to DataSet provides richer, optimized querying over the <xref:System.Data.DataSet> and [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] enables you to directly query SQL Server database schemas, and LINQ to Entities allows you to query an Entity Data Model.  
  
 O diagrama a seguir fornece uma visão geral de como as tecnologias LINQ do ADO.NET estão relacionadas às linguagens de programação de alto nível e às fontes de dados habilitadas para LINQ.  
  
 ![LINQ to ADO.NET overview](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Para obter mais informações sobre LINQ, consulte [linguagem de consulta integrada (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 As seções a seguir fornecem mais informações sobre LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]e LINQ to Entities.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 O <xref:System.Data.DataSet> é um elemento-chave do modelo de programação desconectado no qual o ADO.NET é criado e é amplamente usado. O LINQ to DataSet permite que os desenvolvedores criem recursos de consulta mais avançados em <xref:System.Data.DataSet> usando o mesmo mecanismo de formulação de consulta que está disponível para muitas outras fontes de dados. Para obter mais informações, consulte [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 O [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] é uma ferramenta útil para os desenvolvedores que não requerem mapeamento para um modelo conceitual. Usando [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], você pode usar o modelo de programação LINQ diretamente sobre o esquema de banco de dados existente. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] permite que os desenvolvedores gerem .NET Framework classes que representam dados. Em vez do mapeamento para um modelo de dados conceitual, essas classes geradas mapeiam diretamente para tabelas do banco de dados, modos de exibição, procedimentos armazenados e funções definidas pelo usuário.  
  
 Com o [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], os desenvolvedores podem escrever código diretamente no esquema de armazenamento usando o mesmo padrão de programação LINQ que as coleções na memória e o <xref:System.Data.DataSet>, além de outras fontes de dados, como XML. Para obter mais informações, consulte [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Atualmente, maioria dos aplicativos são escritos sobre bancos de dados relacionais. Em algum ponto, esses aplicativos precisarão interagir com os dados representados em um formulário relacional. Os esquemas de banco de dados não são sempre ideais para criar aplicativos, e os modelos conceituais do aplicativo não são os mesmos que os modelos lógicos de bancos de dados. O Modelo de Dados de Entidade é um modelo de dados conceitual que pode ser usado para modelar os dados de um determinado domínio para que os aplicativos possam interagir com os dados como objetos. Consulte [ADO.NET Entity Framework](./ef/index.md) para obter mais informações.  
  
 Por meio do Modelo de Dados de Entidade, os dados relacionais são expostos como objetos no ambiente .NET. Isso torna a camada de objeto um destino ideal para o suporte a LINQ, permitindo que os desenvolvedores formulem consultas no banco de dados a partir da linguagem usada para criar a lógica de negócios. Essa funcionalidade é conhecida como LINQ to Entities. Consulte [LINQ to Entities](./ef/language-reference/linq-to-entities.md) para obter mais informações.  
  
## <a name="see-also"></a>Veja também

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [LINQ (Consulta Integrada à Linguagem)](../../../csharp/programming-guide/concepts/linq/index.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
