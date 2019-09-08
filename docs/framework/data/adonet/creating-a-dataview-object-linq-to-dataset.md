---
title: Criando um objeto de DataView (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: 054898a3520cbc2b607fc26b94b72b9896ad9c71
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786691"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>Criando um objeto de DataView (LINQ to DataSet)
Há duas maneiras de criar um <xref:System.Data.DataView> no contexto de LINQ to DataSet. Você pode criar um <xref:System.Data.DataView> de uma consulta de LINQ to DataSet em <xref:System.Data.DataTable>um ou pode criá-lo de um tipo ou não tipado <xref:System.Data.DataTable>. Em ambos os casos, você cria <xref:System.Data.DataView> o usando um <xref:System.Data.DataTableExtensions.AsDataView%2A> dos métodos de extensão; <xref:System.Data.DataView> não é diretamente constructible no contexto LINQ to DataSet.  
  
 Após <xref:System.Data.DataView> foi criado, você pode associá-lo a um controle de interface do usuário em um aplicativo de formulários do Windows ou um aplicativo ASP.NET, ou alterar as configurações de filtro e classificação.  
  
 <xref:System.Data.DataView> constrói um índice, que aumenta significativamente o desempenho das operações que podem usar o índice, como filtragem e classificação. O índice de um <xref:System.Data.DataView> é compilado quando <xref:System.Data.DataView> é criado e quando qualquer informação de classificação ou de filtragem é modificada. Criar <xref:System.Data.DataView> e então defina a classificação ou informações de filtragem causam posteriormente o índice a ser compilado pelo menos duas vezes: uma vez que quando <xref:System.Data.DataView> é criado, e novamente quando algumas de tipo ou propriedades de filtragem são alteradas.  
  
 Para obter mais informações sobre filtragem e classificação <xref:System.Data.DataView>com o, consulte [filtrando com DataView](filtering-with-dataview-linq-to-dataset.md) e [classificando com DataView](sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>Criando um DataView de uma consulta LINQ to DataSet  
 Um <xref:System.Data.DataView> objeto pode ser criado com base nos resultados de uma consulta LINQ to DataSet, em que os resultados são uma <xref:System.Data.DataRow> projeção de objetos. <xref:System.Data.DataView> recém-criado herda informações de filtro e classificação de consulta que é criada de.  
  
> [!NOTE]
> Na maioria dos casos, as expressões usadas filtrar e classificar não devem ter efeitos colaterais e devem ser determinísticas. Além disso, as expressões não devem conter qualquer lógica que dependam um número definido de executa, como as operações de classificação e filtragem podem ser executadas qualquer número de vezes.  
  
 Criando <xref:System.Data.DataView> de uma consulta que retorna os tipos anônimos ou consultas que executam join a operações não são suportados.  
  
 Somente os seguintes operadores de consulta são suportados em uma consulta utilizada para criar <xref:System.Data.DataView>:  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Observe que, quando <xref:System.Data.DataView> um é criado a partir de uma <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> consulta LINQ to DataSet, o método deve ser o método final chamado na consulta. Isso é mostrado no exemplo a seguir, que cria um <xref:System.Data.DataView> dos pedidos online classificados pelo total devido:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Você também pode usar as propriedades e <xref:System.Data.DataView.RowFilter%2A> <xref:System.Data.DataView.Sort%2A> baseadas em cadeia de caracteres para filtrar e <xref:System.Data.DataView> classificar um após ter sido criado a partir de uma consulta. Observe que isso desmarcará classificação e informações de filtragem herdadas de consulta. O exemplo a seguir cria <xref:System.Data.DataView> um de uma consulta LINQ to DataSet que filtra por sobrenomes que começam com ' '. A propriedade cadeia de caracteres- base de <xref:System.Data.DataView.Sort%2A> é definida para classificar em sobrenomes na ordem crescente e em nomes em ordem decrescente:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>Criando um DataView de um DataTable  
 Além de serem criados a partir de uma consulta LINQ to DataSet, <xref:System.Data.DataView> um objeto pode ser criado a <xref:System.Data.DataTable> partir de um <xref:System.Data.DataTableExtensions.AsDataView%2A> usando o método.  
  
 O exemplo a seguir cria <xref:System.Data.DataView> da tabela de SalesOrderDetail e defina-o como a fonte de dados de um objeto de <xref:System.Windows.Forms.BindingSource> . Este objeto atua como um proxy para um controle de <xref:System.Windows.Forms.DataGridView> .  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 A filtragem e a classificação podem ser definidas em <xref:System.Data.DataView> depois que foi criado de <xref:System.Data.DataTable>. O exemplo a seguir cria <xref:System.Data.DataView> da tabela de contatos e defina a propriedade de <xref:System.Data.DataView.Sort%2A> para classificar em sobrenomes na ordem crescente e em nomes em ordem decrescente:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 No entanto, há uma perda de desempenho proveniente com definir a propriedade de <xref:System.Data.DataView.RowFilter%2A> ou de <xref:System.Data.DataView.Sort%2A> após <xref:System.Data.DataView> foi criado de uma consulta, como <xref:System.Data.DataView> constrói um índice para oferecer suporte a operações de filtro e classificação. Definindo a propriedade de <xref:System.Data.DataView.RowFilter%2A> ou de <xref:System.Data.DataView.Sort%2A> reconstrói o índice para os dados, adicionando a sobrecarga ao seu aplicativo e a diminuir o desempenho. Quando possível, é melhor especificar informações de filtro e classificação quando você primeiro cria <xref:System.Data.DataView> e impede o alterar mais tarde.  
  
## <a name="see-also"></a>Consulte também

- [Associação de dados e LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [Filtrando com DataView](filtering-with-dataview-linq-to-dataset.md)
- [Classificando com DataView](sorting-with-dataview-linq-to-dataset.md)
