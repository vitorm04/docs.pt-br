---
title: "Associação de dados"
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
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 99aa438c64fdb8f2d14207e6afb06afa8e5f014a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding"></a>Associação de dados
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dá suporte à associação para controles comuns, como controles de grade. Especificamente, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] define os padrões básicos para associação a uma grade de dados e tratamento de associação de detalhes mestre, em relação ao exibir e atualizar.  
  
## <a name="underlying-principle"></a>Princípio subjacente  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]converte [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] consultas SQL para execução em um banco de dados. Os resultados são `IEnumerable` fortemente tipados. Como esses objetos são comuns objetos common language runtime (CLR), associação de dados de objeto comum pode ser usada para exibir os resultados. Por outro lado, as operações de alteração (inserções, atualizações e exclusões) exigem etapas adicionais.  
  
## <a name="operation"></a>Operação  
 Implicitamente, a associação aos controles do Windows Forms é realizada por meio da implementação de <xref:System.ComponentModel.IListSource>. Fontes de dados genéricos <xref:System.Data.Linq.Table%601> (`Table<T>` em c# ou `Table(Of T)` na [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) e genérica `DataQuery` foram atualizadas para implementar <xref:System.ComponentModel.IListSource>. Usuário (IU) da interface associação de dados mecanismos (Windows Forms e Windows Presentation Foundation) ambos os testar se suas fontes de dados implementa <xref:System.ComponentModel.IListSource>. Por isso, escrever uma affectation direta de uma consulta para uma fonte de dados de um controle implicitamente chamadas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] geração de coleção, como no exemplo a seguir:  
  
 [!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
 [!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]  
  
 O mesmo ocorre com o Windows Presentation Foundation:  
  
 [!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
 [!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]  
  
 As gerações de coleção são implementadas por <xref:System.Data.Linq.Table%601> genérico e por `DataQuery` genérico em <xref:System.ComponentModel.IListSource.GetList%2A>.  
  
## <a name="ilistsource-implementation"></a>Implementação de IListSource  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]implementa <xref:System.ComponentModel.IListSource> em dois locais:  
  
-   A fonte de dados é um <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] procura a tabela para preencher um `DataBindingList` coleção que mantém uma referência na tabela.  
  
-   A fonte de dados é um <xref:System.Linq.IQueryable%601>. Há dois cenários:  
  
    -   Se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] localiza subjacente <xref:System.Data.Linq.Table%601> do <xref:System.Linq.IQueryable%601>, permite que a fonte para edição e a situação é o mesmo que o primeiro ponto de marcador.  
  
    -   Se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não é possível localizar subjacente <xref:System.Data.Linq.Table%601>, a origem não permite a edição (por exemplo, `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]procura a consulta para preencher um genérico `SortableBindingList`, que é um simples <xref:System.ComponentModel.BindingList%601> que implementa o recurso de classificação para entidades de T para uma determinada propriedade.  
  
## <a name="specialized-collections"></a>Coleções especializadas  
 Para muitos recursos descritos anteriormente neste documento, <xref:System.ComponentModel.BindingList%601> foi especializado para algumas classes diferentes. Essas classes são `SortableBindingList` genérica e `DataBindingList`genérica. As duas são declaradas como internas.  
  
### <a name="generic-sortablebindinglist"></a>SortableBindingList genérica  
 Essa classe herda de <xref:System.ComponentModel.BindingList%601> e é uma versão classificável de <xref:System.ComponentModel.BindingList%601>. A classificação é uma solução na memória e nunca entra em contato com o próprio banco de dados. <xref:System.ComponentModel.BindingList%601> implementa <xref:System.ComponentModel.IBindingList>, mas, por padrão, não dá suporte à classificação. No entanto, <xref:System.ComponentModel.BindingList%601> implementa <xref:System.ComponentModel.IBindingList> com virtual *core* métodos. Você pode substituir esses métodos facilmente. `SortableBindingList` genérica substitui <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A> e <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore` é chamada por <xref:System.ComponentModel.IBindingList.ApplySort%2A> e classifica a lista de itens de T para uma determinada propriedade.  
  
 Uma exceção será gerada se a propriedade não pertencer a T.  
  
 Para obter a classificação, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria um genérico `SortableBindingList.PropertyComparer` classe que herda de genérica <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> e implementa o comparador padrão para um determinado tipo T, um `PropertyDescriptor`e uma direção. Essa classe cria dinamicamente um `Comparer` de T onde T é `PropertyType` de `PropertyDescriptor`. Em seguida, o comparador padrão é recuperado do `Comparer` estático genérico. Uma instância padrão é obtida usando reflexão.  
  
 A `SortableBindingList` genérica também é a classe base para `DataBindingList`. A `SortableBindingList` genérica oferece dois métodos virtuais para suspender ou retomar o controle de itens adicionar/remover. Esses dois métodos podem ser usados para recursos base como classificação, mas serão realmente implementados por classes superiores, como `DataBindingList`genérica.  
  
### <a name="generic-databindinglist"></a>DataBindingList genérica  
 Esta classe herda de `SortableBindingLIst`genérica. A `DataBindingList` genérica mantém uma referência na `Table` genérica subjacente da `IQueryable` genérica usada para o preenchimento inicial da coleção. A `DatabindingList` genérica adiciona o controle para adicionar/remover itens à coleção substituindo `InsertItem`() e `RemoveItem`(). Também implementa o recurso abstrato suspender/retomar para tornar o controle condicional. Esse recurso faz a `DataBindingList` genérica tirar proveito de todo o uso polimorfo do recurso de rastreamento das classes pai.  
  
## <a name="binding-to-entitysets"></a>Associando a EntitySets  
 A associação a `EntitySet` é um caso especial porque `EntitySet` já é uma coleção que implementa <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Adiciona a classificação e Cancelando (<xref:System.ComponentModel.ICancelAddNew>) oferecem suporte. Uma classe `EntitySet` usa uma lista interna para armazenar entidades. Essa lista é uma coleção de baixo nível baseada em uma matriz genérica, a classe genérica `ItemList`.  
  
### <a name="adding-a-sorting-feature"></a>Adicionando um recurso de classificação  
 Matrizes oferecem um método de classificação (`Array.Sort()`) que pode ser usado com um `Comparer` de T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usa genérica `SortableBindingList.PropertyComparer` classe descrito anteriormente neste tópico para obter esse `Comparer` para a propriedade e a direção para ser classificada. Um método `ApplySort` é adicionado ao `ItemList` genérico para chamar esse recurso.  
  
 No lado de `EntitySet`, você agora precisa declarar suporte à classificação:  
  
-   <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> retorna `true`.  
  
-   <xref:System.ComponentModel.IBindingList.ApplySort%2A> chama `entities.ApplySort()` e, em seguida, `OnListChanged()`.  
  
-   As propriedades <xref:System.ComponentModel.IBindingList.SortDirection%2A> e <xref:System.ComponentModel.IBindingList.SortProperty%2A> expõem a definição de classificação atual, que é armazenada em membros locais.  
  
 Quando você usar um BindingSource e associar um EntitySet\<TEntity > para System.Windows.Forms.BindingSource.DataSource, você deve chamar EntitySet\<Tentity >. GetNewBindingList atualizar BindingSource.List.  
  
 Se você usar um BindingSource e defina a propriedade BindingSource.DataMember e definir BindingSource.DataSource para uma classe que tem uma propriedade denominada no BindingSource.DataMember que expõe o EntitySet\<TEntity >, você não é necessário chamar EntitySet\<Tentity >. GetNewBindingList para atualizar o BindingSource.List, mas você perder a capacidade de classificação.  
  
## <a name="caching"></a>Cache  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]consultas implementam <xref:System.ComponentModel.IListSource.GetList%2A>. Quando a classe BindingSource do Windows Forms encontra essa interface, ela chama GetList() três vezes para uma única conexão. Para solucionar essa situação, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementa um cache por instância para armazenar e sempre retornará o mesmo gerado coleção.  
  
## <a name="cancellation"></a>Cancelamento  
 O <xref:System.ComponentModel.IBindingList> define um método <xref:System.ComponentModel.IBindingList.AddNew%2A> que é usado pelos controles para criar um novo item de uma coleção associada. O controle `DataGridView` mostra esse recurso muito bem quando a última linha visível contém uma estrela em seu cabeçalho. A estrela mostra que você pode adicionar um novo item.  
  
 Além desse recurso, uma coleção também pode implementar <xref:System.ComponentModel.ICancelAddNew>. Esse recurso permite que os controles cancelem ou validem se o novo item editado foi validado ou não.  
  
 <xref:System.ComponentModel.ICancelAddNew>é implementado em todos os [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] coleções de ligação de dados (genérico `SortableBindingList` e genérica `EntitySet`). Em ambas as implementações o código executa:  
  
-   Permite que itens sejam inseridos e removidos da coleção.  
  
-   Não controla as alterações desde que a interface do usuário não confirme a edição.  
  
-   Não controla as alterações desde que a edição seja cancelada (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).  
  
-   Permite controlar quando a edição é confirmada (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).  
  
-   Permite que a coleção se comporte normalmente se o novo item não for proveniente de <xref:System.ComponentModel.IBindingList.AddNew%2A>.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Esta seção chama vários itens que podem ajudar a resolver problemas de seus aplicativos de vinculação de dados do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
-   Você deve usar propriedades; usar somente campos não é suficiente. O Windows Forms requer esse uso.  
  
-   Por padrão, `image`, `varbinary`, e `timestamp` tipos de banco de dados são mapeados para a matriz de bytes. Como `ToString()` não é suportado nesse cenário, esses objetos não podem ser exibidos.  
  
-   Um membro de classe mapeado para uma chave primária tem um setter, mas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não oferece suporte à alteração de identidade de objeto. Portanto, a chave primária/exclusiva que é usada no mapeamento não pode ser atualizada no banco de dados. Uma alteração na grade faz com que uma exceção ao chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Se uma entidade estiver associada em duas grades separadas (por exemplo, uma mestra e outra de detalhes), `Delete` na grade mestra não será propagado para a grade de detalhes.  
  
## <a name="see-also"></a>Consulte também  
 [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
