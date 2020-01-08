---
title: Campo genérico e métodos de SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 310eb3ccecc3159234ed362ed044be7ad704dde4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634827"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Campo genérico e métodos de SetField (LINQ to DataSet)
LINQ to DataSet fornece métodos de extensão para a classe <xref:System.Data.DataRow> para acessar valores de coluna: o método <xref:System.Data.DataRowExtensions.Field%2A> e o método <xref:System.Data.DataRowExtensions.SetField%2A>. Esses métodos fornecem acesso mais fácil a valores de coluna para desenvolvedores, especialmente em relação a valores nulos. O <xref:System.Data.DataSet> usa <xref:System.DBNull.Value?displayProperty=nameWithType> para representar valores nulos, enquanto o LINQ usa os tipos <xref:System.Nullable> e <xref:System.Nullable%601>. Usar o acessador de coluna pré-existente no <xref:System.Data.DataRow> exige que você converta o objeto de retorno para o tipo apropriado. Se um determinado campo em um <xref:System.Data.DataRow> puder ser nulo, você deverá verificar explicitamente se há um valor nulo porque retornar <xref:System.DBNull.Value?displayProperty=nameWithType> e convertê-lo implicitamente em outro tipo gera uma <xref:System.InvalidCastException>. No exemplo a seguir, se o método <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> não foi usado para verificar um valor nulo, uma exceção seria gerada se o indexador retornou <xref:System.DBNull.Value?displayProperty=nameWithType> e tentou convertê-lo em um <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 O método <xref:System.Data.DataRowExtensions.Field%2A> fornece acesso aos valores de coluna de um <xref:System.Data.DataRow> e o <xref:System.Data.DataRowExtensions.SetField%2A> define valores de coluna em um <xref:System.Data.DataRow>. Os métodos <xref:System.Data.DataRowExtensions.Field%2A> e <xref:System.Data.DataRowExtensions.SetField%2A> lidam com tipos anuláveis, para você não precise verificar valores nulos explicitamente como no exemplo anterior. Ambos os métodos também são genéricos, de modo que você não tem que converter o tipo de retorno.  
  
 O exemplo a seguir usa o método <xref:System.Data.DataRowExtensions.Field%2A>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Observe que o tipo de dados especificado no parâmetro genérico `T` dos métodos <xref:System.Data.DataRowExtensions.Field%2A> e <xref:System.Data.DataRowExtensions.SetField%2A> deve corresponder ao tipo do valor subjacente. Caso contrário, uma exceção <xref:System.InvalidCastException> será gerada. O nome da coluna especificado também deve corresponder ao nome de uma coluna no <xref:System.Data.DataSet> ou <xref:System.ArgumentException> será gerado. Em ambos os casos, a exceção é gerada em tempo de execução durante a enumeração dos dados quando a consulta é executada.  
  
 O próprio método <xref:System.Data.DataRowExtensions.SetField%2A> não realiza nenhuma conversão de tipos. Isso não significa, entretanto, que uma conversão de tipos não ocorrerá. O método <xref:System.Data.DataRowExtensions.SetField%2A> expõe o comportamento ADO.NET da classe <xref:System.Data.DataRow>. Uma conversão de tipo pode ser executada pelo objeto <xref:System.Data.DataRow> e o valor convertido seria então salvo no objeto <xref:System.Data.DataRow>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Data.DataRowExtensions>
