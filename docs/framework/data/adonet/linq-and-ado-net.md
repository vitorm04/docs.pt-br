---
title: LINQ e o ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: f6b956aa4d19a5bf558681975da3125b45b36c5f
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634840"
---
# <a name="linq-and-adonet"></a>LINQ e o ADO.NET
Hoje, muitos desenvolvedores de negócios devem usar duas (ou mais) linguagens de programação: uma linguagem de alto nível para a lógica de negócios e camadas de C# apresentação (como Visual ou Visual Basic) e uma linguagem de consulta para interagir com o banco de dados (como TRANSACT-SQL). Isso exige que o desenvolvedor seja proficiente em várias linguagens para ser eficaz e também provoca incompatibilidades de linguagens no ambiente de desenvolvimento. Por exemplo, um aplicativo que usa uma API de acesso a dados para executar uma consulta em um banco de dados especifica a consulta como um literal de cadeia de caracteres usando aspas. Essa cadeia de caracteres de consulta é ilegível para o compilador e os erros não são verificados, como sintaxe inválida ou se as colunas ou linhas referenciadas realmente existem. Não há nenhuma verificação do tipo dos parâmetros da consulta e também nenhum suporte do `IntelliSense`.  
  
 O LINQ (consulta integrada à linguagem) permite que os desenvolvedores formem consultas baseadas em conjunto no código do aplicativo, sem precisar usar uma linguagem de consulta separada. Você pode escrever consultas LINQ em várias fontes de dados enumeráveis (ou seja, uma fonte de dados que implementa a interface <xref:System.Collections.IEnumerable>), como estruturas de dados na memória, documentos XML, bancos de dados SQL e objetos <xref:System.Data.DataSet>. Embora essas fontes de dados enumeráveis sejam implementadas de várias maneiras, todas elas expõem as mesmas sintaxe e constructos de linguagem. Como as consultas podem ser formadas na própria linguagem de programação, você não precisa usar outra linguagem de consulta que seja inserida como literais de cadeia de caracteres que não podem ser compreendidos ou verificados pelo compilador. A integração de consultas à linguagem de programação também permite que os programadores do Visual Studio sejam mais produtivos fornecendo o tipo de tempo de compilação e a verificação de sintaxe e `IntelliSense`. Esses recursos reduzem a necessidade de depuração da consulta e de correção de erros.  
  
 A transferência de dados de tabelas SQL para objetos na memória é geralmente tediosa e sujeita a erros. O provedor LINQ implementado por LINQ to DataSet e [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] converte os dados de origem em coleções de objetos baseados em <xref:System.Collections.IEnumerable>. O programador sempre exibe os dados como uma coleção de <xref:System.Collections.IEnumerable>, quando você consulta e quando você atualiza. Suporte completo do `IntelliSense` é fornecido para escrever consultas nessas coleções.  
  
 Há três tecnologias de LINQ (consulta integrada à linguagem ADO.NET) separadas: LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]e LINQ to Entities. O LINQ to DataSet fornece consultas mais ricas e otimizadas sobre o <xref:System.Data.DataSet> e [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] permite que você consulte diretamente os esquemas de banco de dados SQL Server e LINQ to Entities permite consultar um Modelo de Dados de Entidade.  
  
 O diagrama a seguir fornece uma visão geral de como as tecnologias LINQ do ADO.NET estão relacionadas às linguagens de programação de alto nível e às fontes de dados habilitadas para LINQ.  
  
 ![Visão geral de LINQ to ADO.NET](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
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
