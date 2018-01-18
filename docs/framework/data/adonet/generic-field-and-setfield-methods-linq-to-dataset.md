---
title: "Campo genérico e métodos de SetField (LINQ to DataSet)"
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
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6281f2fdd00f210f09c97861d2ea723d259af004
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Campo genérico e métodos de SetField (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]fornece métodos de extensão para o <xref:System.Data.DataRow> classe para acessar valores de coluna: o <xref:System.Data.DataRowExtensions.Field%2A> método e o <xref:System.Data.DataRowExtensions.SetField%2A> método. Esses métodos fornecem acesso fácil aos valores de coluna para desenvolvedores, especialmente em relação a valores nulos. O <xref:System.Data.DataSet> usa <xref:System.DBNull.Value> para representar valores nulos, enquanto [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] usa o suporte a tipo anulável introduzido no [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Usando o acessador de coluna já existentes no <xref:System.Data.DataRow> exige que você converter o objeto de retorno para o tipo apropriado. Se um determinado campo de um <xref:System.Data.DataRow> pode ser nulo, você precisa verificar explicitamente um valor nulo como retornando <xref:System.DBNull.Value> e implicitamente convertê-la em outro lança do tipo um <xref:System.InvalidCastException>. No exemplo a seguir, se o <xref:System.Data.DataRow.IsNull%2A> método não foi usado para verificar se há um valor nulo, uma exceção será lançada se o indexador retornado <xref:System.DBNull.Value> e tentou convertê-lo para um <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 O método <xref:System.Data.DataRowExtensions.Field%2A> fornece acesso aos valores de coluna de um <xref:System.Data.DataRow> e o <xref:System.Data.DataRowExtensions.SetField%2A> define valores de coluna em um <xref:System.Data.DataRow>. Os métodos <xref:System.Data.DataRowExtensions.Field%2A> e <xref:System.Data.DataRowExtensions.SetField%2A> lidam com tipos anuláveis, para você não precise verificar valores nulos explicitamente como no exemplo anterior. Ambos os métodos também são genéricos, de modo que você não tem que converter o tipo de retorno.  
  
 O exemplo a seguir usa o método <xref:System.Data.DataRowExtensions.Field%2A>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Observe que o tipo de dados especificado no parâmetro genérico `T` dos métodos <xref:System.Data.DataRowExtensions.Field%2A> e <xref:System.Data.DataRowExtensions.SetField%2A> deve corresponder ao tipo do valor subjacente. Caso contrário, uma exceção <xref:System.InvalidCastException> será gerada. O nome da coluna especificado também deve corresponder ao nome de uma coluna no <xref:System.Data.DataSet> ou <xref:System.ArgumentException> será gerado. Em ambos os casos, a exceção é gerada em tempo de execução durante a enumeração dos dados quando a consulta é executada.  
  
 O próprio método <xref:System.Data.DataRowExtensions.SetField%2A> não realiza nenhuma conversão de tipos. Isso não significa, entretanto, que uma conversão de tipos não ocorrerá. O <xref:System.Data.DataRowExtensions.SetField%2A> método expõe o [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] comportamento do <xref:System.Data.DataRow> classe. Uma conversão de tipo pode ser realizada o <xref:System.Data.DataRow> objeto e o valor convertido, em seguida, seriam salvas no <xref:System.Data.DataRow> objeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataRowExtensions>
