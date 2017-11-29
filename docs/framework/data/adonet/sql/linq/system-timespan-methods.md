---
title: "Métodos de System.TimeSpan"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a32b57488b49e9fd2f4e6342391690b27d7ad825
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="systemtimespan-methods"></a>Métodos de System.TimeSpan
Suporte de membro para <xref:System.TimeSpan?displayProperty=nameWithType> depende das versões do .NET Framework e do Microsoft SQL Server que você está usando.  
  
 Quando um método, um operador, ou uma propriedade são sem suporte; significa que LINQ to SQL não pode converter o membro para execução no SQL Server. Você pode ainda seja possível usar esses membros no seu código. No entanto, devem ser avaliado antes que a consulta seja convertida a Transact-SQL ou após os resultados foram recuperados de base de dados.  
  
## <a name="previous-limitations"></a>Limitações anteriores  
 Ao usar LINQ to SQL com versões do .NET Framework antes do .NET Framework 3.5 SP1, você não pode mapear campos de base de dados SQL Server a <xref:System.TimeSpan?displayProperty=nameWithType>. No entanto, as operações no <xref:System.TimeSpan> têm suporte porque os valores <xref:System.TimeSpan> podem ser retornados da subtração de <xref:System.DateTime> ou introduzidos em uma expressão como um literal ou uma variável associada.  
  
## <a name="supported-systemtimespan-method-support"></a>Suporte suporte de método System.TimeSpan  
 Seguinte LINQ para os métodos suportados SQL-, operadores, e propriedades estão disponíveis para que você as use nas consultas LINQ to SQL. Mapeado uma vez no modelo de objeto ou no arquivo de mapeamento externo, LINQ to SQL permite que você chame muitos dos membros de <xref:System.TimeSpan?displayProperty=nameWithType> em suas consultas LINQ to SQL.  
  
|Métodos suportados de <xref:System.TimeSpan>|Operadores de <xref:System.TimeSpan> suportados|Propriedades suportadas de <xref:System.TimeSpan>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<!--zz <xref:System.TimeSpan.MinValue%2A>-->|  
  
> [!NOTE]
>  A capacidade de mapear <xref:System.TimeSpan?displayProperty=nameWithType> para uma coluna do SQL `TIME` com LINQ to SQL requer o .NET Framework 3.5 SP1 e além. O tipo de dados SQL `TIME` só está disponível no Microsoft SQL Server 2008 e além.  
  
### <a name="addition-and-subtraction"></a>Adição e subtração  
 Embora o tipo de CLR <xref:System.TimeSpan?displayProperty=nameWithType> suporte a adição e subtração, o tipo do SQL `TIME` não. Devido a isso, as consultas LINQ to SQL gerarão erros se tentam a adição e subtração quando eles são mapeadas para o tipo do SQL `TIME` . Você pode encontrar outras considerações para trabalhar com tipos de data e hora do SQL em [mapeamento de tipo CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Criando o modelo de objeto](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Mapeamento de tipo CLR do SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Funções e tipos de dados](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
