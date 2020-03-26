---
title: Campo genérico e métodos de SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: d7ddee775e91c6be6166a091997afd58113cfe6b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249097"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Campo genérico e métodos de SetField (LINQ to DataSet)
LINQ to DataSet fornece métodos de extensão <xref:System.Data.DataRow> à <xref:System.Data.DataRowExtensions.Field%2A> classe <xref:System.Data.DataRowExtensions.SetField%2A> para acessar valores de coluna: o método e o método. Esses métodos proporcionam acesso mais fácil aos valores das colunas para desenvolvedores, especialmente em relação a valores nulos. Os <xref:System.Data.DataSet> <xref:System.DBNull.Value?displayProperty=nameWithType> usos representam valores nulos, <xref:System.Nullable> <xref:System.Nullable%601> enquanto linq usa os e tipos. O uso do acessório de <xref:System.Data.DataRow> coluna pré-existente requer que você lance o objeto de retorno para o tipo apropriado. Se um campo <xref:System.Data.DataRow> específico em um pode ser nulo, você <xref:System.DBNull.Value?displayProperty=nameWithType> deve verificar explicitamente se há <xref:System.InvalidCastException>um valor nulo porque retornar e implicitamente lançá-lo para outro tipo lança um . No exemplo a seguir, se o <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> método não fosse usado para verificar um valor <xref:System.DBNull.Value?displayProperty=nameWithType> nulo, uma exceção seria lançada se o indexador retornasse e tentasse lançá-lo para um <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 O método <xref:System.Data.DataRowExtensions.Field%2A> fornece acesso aos valores de coluna de um <xref:System.Data.DataRow> e o <xref:System.Data.DataRowExtensions.SetField%2A> define valores de coluna em um <xref:System.Data.DataRow>. Tanto <xref:System.Data.DataRowExtensions.Field%2A> o <xref:System.Data.DataRowExtensions.SetField%2A> método quanto o método lidam com tipos de valor anulados, para que você não precise verificar explicitamente se há valores nulos como no exemplo anterior. Ambos os métodos também são genéricos, de modo que você não tem que converter o tipo de retorno.  
  
 O exemplo a seguir usa o método <xref:System.Data.DataRowExtensions.Field%2A>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Observe que o tipo de dados especificado no parâmetro genérico `T` dos métodos <xref:System.Data.DataRowExtensions.Field%2A> e <xref:System.Data.DataRowExtensions.SetField%2A> deve corresponder ao tipo do valor subjacente. Caso contrário, uma exceção <xref:System.InvalidCastException> será gerada. O nome da coluna especificado também deve corresponder ao nome de uma coluna no <xref:System.Data.DataSet> ou <xref:System.ArgumentException> será gerado. Em ambos os casos, a exceção é gerada em tempo de execução durante a enumeração dos dados quando a consulta é executada.  
  
 O próprio método <xref:System.Data.DataRowExtensions.SetField%2A> não realiza nenhuma conversão de tipos. Isso não significa, entretanto, que uma conversão de tipos não ocorrerá. O <xref:System.Data.DataRowExtensions.SetField%2A> método expõe o comportamento <xref:System.Data.DataRow> ADO.NET da classe. Uma conversão de tipo <xref:System.Data.DataRow> poderia ser realizada pelo objeto e <xref:System.Data.DataRow> o valor convertido seria então salvo no objeto.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataRowExtensions>
