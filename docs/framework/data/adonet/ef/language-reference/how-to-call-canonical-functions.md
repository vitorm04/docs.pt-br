---
title: "Como: Funções canônicas de chamada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 02cbcee218db310fdddc7f42d9b6f01a16a8314d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-canonical-functions"></a>Como: Funções canônicas de chamada
A classe de <xref:System.Data.Objects.EntityFunctions> contém os métodos que expõe funções canônicas para usar em consultas LINQ to Entities. Para obter informações sobre funções canônicas, consulte [Funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
>  Os métodos de <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> e de <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> na classe de <xref:System.Data.Objects.EntityFunctions> não têm equivalentes canônicos de função.  
  
 As funções canônicas que executar um cálculo em um conjunto de valores e retornar um valor único (também conhecido como funções agregadas canônicas) podem ser chamadas diretamente. Outras funções canônicas só podem ser chamados como parte de uma consulta LINQ to Entities. Para chamar diretamente uma função agregada, você deve passar <xref:System.Data.Objects.ObjectQuery%601> à função. Para obter mais informações, consulte o segundo exemplo abaixo.  
  
 Você pode chamar algumas funções canônicas usando métodos do Common Language Runtime (CLR) em consultas LINQ to Entities. Para obter uma lista dos métodos CLR que são mapeados para funções canônicas, consulte [método CLR ao mapeamento canônico de função](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). O exemplo executa uma consulta LINQ to entidades que usa o método de <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> para retornar todos os produtos para que a diferença entre `SellEndDate` e `SellStartDate` é menor que 365 dias:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). O exemplo chama o método agregado de <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> diretamente para retornar o desvio padrão de subtotais de `SalesOrderHeader` . Observe que <xref:System.Data.Objects.ObjectQuery%601> é passado para a função, que permite que é chamado sem ser parte de uma consulta LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Chamando funções em consultas LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Consultas no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
