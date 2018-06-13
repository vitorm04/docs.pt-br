---
title: LINQ e o ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: 1385b2d9b49a7615810025141e111b7d7bf71eac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766121"
---
# <a name="linq-and-adonet"></a>LINQ e o ADO.NET
Atualmente, muitos desenvolvedores de negócios devem usar linguagens de programação duas (ou mais): uma linguagem de alto nível para as camadas de apresentação e lógica de negócios (por exemplo, Visual c# ou Visual Basic) e uma linguagem de consulta para interagir com o banco de dados (como [!INCLUDE[tsql](../../../../includes/tsql-md.md)]). Isso exige que o desenvolvedor seja proficiente em várias linguagens para ser eficaz e também provoca incompatibilidades de linguagens no ambiente de desenvolvimento. Por exemplo, um aplicativo que usa uma API de acesso a dados para executar uma consulta em um banco de dados especifica a consulta como um literal de cadeia de caracteres usando aspas. Essa cadeia de caracteres de consulta é ilegível para o compilador e os erros não são verificados, como sintaxe inválida ou se as colunas ou linhas referenciadas realmente existem. Não há nenhuma verificação do tipo dos parâmetros da consulta e também nenhum suporte do `IntelliSense`.  
  
 O [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] permite que os desenvolvedores formem consultas baseadas em conjuntos no código de seus aplicativos, sem precisar usar uma linguagem de consulta separada. Você pode escrever consultas de [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] com várias fontes de dados enumeráveis (ou seja, uma fonte de dados que implemente a interface <xref:System.Collections.IEnumerable>), como estruturas de dados na memória, documentos XML, bancos de dados SQL e objetos <xref:System.Data.DataSet>. Embora essas fontes de dados enumeráveis sejam implementadas de várias maneiras, todas elas expõem as mesmas sintaxe e constructos de linguagem. Como as consultas podem ser formadas na própria linguagem de programação, você não precisa usar outra linguagem de consulta que seja inserida como literais de cadeia de caracteres que não podem ser compreendidos ou verificados pelo compilador. Integrar a linguagem de programação de consultas também permite que os programadores de Visual Studio ser mais produtivo, fornecendo o tipo de tempo de compilação e verificação de sintaxe, e `IntelliSense`. Esses recursos reduzem a necessidade de depuração da consulta e de correção de erros.  
  
 A transferência de dados de tabelas SQL para objetos na memória é geralmente tediosa e sujeita a erros. O provedor do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] implementado pelo [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] e pelo [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] converte os dados de origem em coleções de objetos baseados em <xref:System.Collections.IEnumerable>. O programador sempre exibe os dados como uma coleção de <xref:System.Collections.IEnumerable>, quando você consulta e quando você atualiza. Suporte completo do `IntelliSense` é fornecido para escrever consultas nessas coleções.  
  
 Há três tecnologias separadas do [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] do ADO.NET: [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] e [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fornece mais avançada, otimizado consulta sobre o <xref:System.Data.DataSet> e [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] permite consultar diretamente os esquemas de banco de dados do SQL Server, e [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] permite consultar um [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
 O diagrama a seguir fornece uma visão geral de como as tecnologias LINQ do ADO.NET estão relacionadas às linguagens de programação de alto nível e às fontes de dados habilitadas para LINQ.  
  
 ![LINQ para visão geral do ADO.NET](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Para obter informações gerais sobre os recursos de linguagem LINQ, consulte [Introdução ao LINQ](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e). Para obter informações sobre como usar o LINQ em seus aplicativos, consulte o [não está em compilação: guia de programação geral de LINQ](http://msdn.microsoft.com/library/609c7a6b-cbdd-429d-99f3-78d13d3bc049), que contém informações detalhadas sobre como usar tecnologias LINQ.  
  
 As seções a seguir fornecem mais informações sobre o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], o [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] e o [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 O <xref:System.Data.DataSet> é um elemento chave do modelo de programação desconectado no qual o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] é baseado e é amplamente utilizado. O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] permite que os desenvolvedores criem mais recursos sofisticados de consulta no <xref:System.Data.DataSet> usando o mesmo mecanismo de formulação de consulta que está disponível para muitas outras fontes de dados. Para obter mais informações, consulte [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 O [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] é uma ferramenta útil para os desenvolvedores que não requerem mapeamento para um modelo conceitual. Usando o [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], você pode usar o modelo de programação do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] diretamente sobre o esquema do banco de dados existente. O [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] permite que os desenvolvedores gerem classes do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] que representam dados. Em vez do mapeamento para um modelo de dados conceitual, essas classes geradas mapeiam diretamente para tabelas do banco de dados, modos de exibição, procedimentos armazenados e funções definidas pelo usuário.  
  
 Com o [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], os desenvolvedores podem escrever código diretamente no esquema de armazenamento usando o mesmo padrão de programação do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] como coleções na memória e o <xref:System.Data.DataSet>, além de outras fontes de dados, como XML. Para obter mais informações, consulte [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Atualmente, maioria dos aplicativos são escritos sobre bancos de dados relacionais. Em algum ponto, esses aplicativos precisarão interagir com os dados representados em um formulário relacional. Os esquemas de banco de dados não são sempre ideais para criar aplicativos, e os modelos conceituais do aplicativo não são os mesmos que os modelos lógicos de bancos de dados. O [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] é um modelo de dados conceitual, que pode ser usado para modelar os dados de um domínio específico de modo que os aplicativos possam interagir com dados como objetos. Consulte [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) para obter mais informações.  
  
 Por meio do [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], os dados relacionais são expostos como objetos no ambiente .NET. Isso torna a camada do objeto um destino ideal para o suporte do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] permitindo que os desenvolvedores formulem consultas no banco de dados na linguagem usada para criar a lógica de negócios. Esse recurso é conhecido como [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. Consulte [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md) para obter mais informações.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
