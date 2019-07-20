---
title: Arquitetura do componente BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 54a23ba899ceb05701fe3580aefbb723c6b3f0fd
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364407"
---
# <a name="bindingsource-component-architecture"></a>Arquitetura do componente BindingSource
Com o <xref:System.Windows.Forms.BindingSource> componente, você pode associar universalmente todos os controles de Windows Forms a fontes de dados.  
  
 O <xref:System.Windows.Forms.BindingSource> componente simplifica o processo de vinculação de controles a uma fonte de dados e fornece as seguintes vantagens em relação à ligação de dados tradicional:  
  
- Habilita a associação a objetos comerciais em tempo de design.  
  
- <xref:System.Windows.Forms.CurrencyManager> Encapsula a <xref:System.Windows.Forms.CurrencyManager> funcionalidade e expõe eventos em tempo de design.  
  
- Simplifica a criação de uma lista que dá <xref:System.ComponentModel.IBindingList> suporte à interface, fornecendo notificação de alteração de lista para fontes de dados que não dão suporte nativo à notificação de alteração de lista.  
  
- Fornece um ponto de extensibilidade para <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> o método.  
  
- Fornece um nível de indireção entre a fonte de dados e o controle. A indireção é importante quando a fonte de dados pode se alterar em tempo de execução.  
  
- Interopera com outros controles de Windows Forms relacionados a dados, especificamente os <xref:System.Windows.Forms.BindingNavigator> <xref:System.Windows.Forms.DataGridView> controles e.  
  
 Por esses motivos, o <xref:System.Windows.Forms.BindingSource> componente é a maneira preferida de associar os controles de Windows Forms a fontes de dados.  
  
## <a name="bindingsource-features"></a>Recursos do BindingSource  
 O <xref:System.Windows.Forms.BindingSource> componente fornece vários recursos para ligar controles a dados. Com esses recursos, você pode implementar a maioria dos cenários de associação de dados com quase nenhuma codificação de sua parte.  
  
 O <xref:System.Windows.Forms.BindingSource> componente realiza isso fornecendo uma interface consistente para acessar vários tipos diferentes de fontes de dados. Isso significa que você usa o mesmo procedimento para associar a qualquer tipo. Por exemplo, você pode anexar a <xref:System.Windows.Forms.BindingSource.DataSource%2A> Propriedade a um <xref:System.Data.DataSet> ou a um objeto comercial e, em ambos os casos, você usa o mesmo conjunto de propriedades, métodos e eventos para manipular a fonte de dados.  
  
 A interface consistente fornecida pelo <xref:System.Windows.Forms.BindingSource> componente simplifica muito o processo de vinculação de dados a controles. Para tipos de fonte de dados que fornecem notificação de alteração <xref:System.Windows.Forms.BindingSource> , o componente comunica automaticamente as alterações entre o controle e a fonte de dados. Para tipos de fonte de dados que não fornecem notificação de alteração, são fornecidos eventos que permitem gerar notificações de alteração. A lista a seguir mostra os recursos com suporte <xref:System.Windows.Forms.BindingSource> pelo componente:  
  
- Indireção.  
  
- Gerenciamento de moeda.  
  
- Fonte de dados como uma lista.  
  
- <xref:System.Windows.Forms.BindingSource>como um <xref:System.ComponentModel.IBindingList>.  
  
- Criação de item personalizado.  
  
- Criação de item transacional.  
  
- <xref:System.Collections.IEnumerable>support.  
  
- Suporte a tempo de design.  
  
- Métodos <xref:System.Windows.Forms.ListBindingHelper> estáticos.  
  
- Classificação e filtragem com a <xref:System.ComponentModel.IBindingListView> interface.  
  
- Integração com <xref:System.Windows.Forms.BindingNavigator>o.  
  
### <a name="indirection"></a>Indireção  
 O <xref:System.Windows.Forms.BindingSource> componente fornece um nível de indireção entre um controle e uma fonte de dados. Em vez de ligar um controle diretamente a uma fonte de dados, você associa o controle <xref:System.Windows.Forms.BindingSource>a um e anexa a fonte de dados <xref:System.Windows.Forms.BindingSource> à propriedade do <xref:System.Windows.Forms.BindingSource.DataSource%2A> componente.  
  
 Com esse nível de indireção, você pode alterar a fonte de dados sem redefinir a associação de controle. Isso oferece as seguintes funcionalidades:  
  
- Você pode anexar o <xref:System.Windows.Forms.BindingSource> a diferentes fontes de dados enquanto retém as associações de controle atuais.  
  
- Você pode alterar os itens na fonte de dados e notificar os controles associados. Para obter mais informações, confira [Como: Reflita atualizações de fontes de dados em um controle de Windows Forms](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)com a BindingSource.  
  
- Você pode associar a um <xref:System.Type> em vez de a um objeto na memória. Para obter mais informações, confira [Como: Associar um controle de Windows Forms a um](how-to-bind-a-windows-forms-control-to-a-type.md)tipo. Em seguida, você pode associar a um objeto em tempo de execução.  
  
### <a name="currency-management"></a>Gerenciamento de moedas  
 O <xref:System.Windows.Forms.BindingSource> componente implementa a <xref:System.Windows.Forms.ICurrencyManagerProvider> interface para lidar com o gerenciamento de moedas para você. Com a <xref:System.Windows.Forms.ICurrencyManagerProvider> interface, você também pode acessar o Gerenciador de moedas para um <xref:System.Windows.Forms.BindingSource>, além do Gerenciador de moedas para outro <xref:System.Windows.Forms.BindingSource> associado ao mesmo <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 O <xref:System.Windows.Forms.BindingSource> componente <xref:System.Windows.Forms.CurrencyManager> encapsula a funcionalidade e expõe as propriedades e os eventos mais comuns. <xref:System.Windows.Forms.CurrencyManager> A tabela a seguir descreve alguns dos membros relacionados ao gerenciamento de moeda.  
  
 Propriedade <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>  
 Obtém o Gerenciador de moedas associado <xref:System.Windows.Forms.BindingSource>ao.  
  
 Método <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A>  
 Se houver outro <xref:System.Windows.Forms.BindingSource> associado ao membro de dados especificado, o obterá seu Gerenciador de moedas.  
  
 Propriedade <xref:System.Windows.Forms.BindingSource.Current%2A>  
 Obtém o item atual da fonte de dados.  
  
 Propriedade <xref:System.Windows.Forms.BindingSource.Position%2A>  
 Obtém ou define a posição atual na lista subjacente.  
  
 Método <xref:System.Windows.Forms.BindingSource.EndEdit%2A>  
 Aplica as alterações pendentes à fonte de dados subjacente.  
  
 Método <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>  
 Cancela a operação de edição atual.  
  
### <a name="data-source-as-a-list"></a>Fonte de dados como uma lista  
 O <xref:System.Windows.Forms.BindingSource> componente implementa as <xref:System.ComponentModel.IBindingListView> interfaces <xref:System.ComponentModel.ITypedList> e. Com essa implementação, você pode usar o <xref:System.Windows.Forms.BindingSource> próprio componente como uma fonte de dados, sem nenhum armazenamento externo.  
  
 Quando o <xref:System.Windows.Forms.BindingSource> componente é anexado a uma fonte de dados, ele expõe a fonte de dados como uma lista.  
  
 A <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade pode ser definida para várias fontes de dados. Isso inclui tipos, objetos e listas de tipos. A fonte de dados resultante será exposta como uma lista. A tabela a seguir mostra algumas das fontes de dados comuns e a avaliação de lista resultante.  
  
|Propriedade DataSource|Listar resultados|  
|-------------------------|------------------|  
|Uma referência nula (`Nothing` no Visual Basic)|Um vazio <xref:System.ComponentModel.IBindingList> de objetos. Adicionar um item define a lista como o tipo do item adicionado.|  
|Uma referência nula (`Nothing` em Visual Basic) com <xref:System.Windows.Forms.BindingSource.DataMember%2A> Set|Sem suporte; gera <xref:System.ArgumentException>.|  
|Tipo fora da lista ou objeto do tipo "T"|Um vazio <xref:System.ComponentModel.IBindingList> do tipo "T".|  
|Instância de matriz|Um <xref:System.ComponentModel.IBindingList> que contém os elementos da matriz.|  
|<xref:System.Collections.IEnumerable>cópia|Um <xref:System.ComponentModel.IBindingList> que contém <xref:System.Collections.IEnumerable> os itens|  
|Instância de lista que contém o tipo "T"|Uma <xref:System.ComponentModel.IBindingList> instância que contém o tipo "T".|  
  
 Além disso <xref:System.Windows.Forms.BindingSource.DataSource%2A> , o pode ser definido para outros tipos de lista <xref:System.ComponentModel.IListSource> , <xref:System.ComponentModel.ITypedList>como e, <xref:System.Windows.Forms.BindingSource> e o irá tratá-los adequadamente. Nesse caso, o tipo contido na lista deve ter um construtor sem parâmetros.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource como uma IBindingList  
 O <xref:System.Windows.Forms.BindingSource> componente fornece membros para acessar e manipular os dados subjacentes como um <xref:System.ComponentModel.IBindingList>. A tabela a seguir descreve alguns desses membros.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.List%2A>|Obtém a lista que resulta da avaliação das <xref:System.Windows.Forms.BindingSource.DataSource%2A> Propriedades ou. <xref:System.Windows.Forms.BindingSource.DataMember%2A>|  
|Método <xref:System.Windows.Forms.BindingSource.AddNew%2A>|Adiciona um novo item à lista subjacente. Aplica-se a fontes de dados <xref:System.ComponentModel.IBindingList> que implementam a interface e permitem adicionar itens ( <xref:System.Windows.Forms.BindingSource.AllowNew%2A> ou seja, a `true`propriedade é definida como).|  
  
### <a name="custom-item-creation"></a>Criação de item personalizado  
 Você pode manipular o <xref:System.Windows.Forms.BindingSource.AddingNew> evento para fornecer sua própria lógica de criação de itens. O <xref:System.Windows.Forms.BindingSource.AddingNew> evento ocorre antes que um novo objeto seja adicionado <xref:System.Windows.Forms.BindingSource>ao. Esse evento é gerado depois que <xref:System.Windows.Forms.BindingSource.AddNew%2A> o método é chamado, mas antes que o novo item seja adicionado à lista subjacente. Ao manipular esse evento, você pode fornecer comportamento de criação de item personalizado sem derivar <xref:System.Windows.Forms.BindingSource> da classe. Para obter mais informações, confira [Como: Personalize a adição de itens com o](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)Windows Forms BindingSource.  
  
### <a name="transactional-item-creation"></a>Criação de item transacional  
 O <xref:System.Windows.Forms.BindingSource> componente implementa a <xref:System.ComponentModel.ICancelAddNew> interface, que habilita a criação de itens transacionais. Depois que um novo item é criado Provisionando usando uma chamada para <xref:System.Windows.Forms.BindingSource.AddNew%2A>, a adição pode ser confirmada ou revertida das seguintes maneiras:  
  
- O <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> método confirmará explicitamente a adição pendente.  
  
- A realização de outra operação de coleção, como uma inserção, remoção ou mover, confirmará implicitamente a adição pendente.  
  
- O <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> método reverterá a adição pendente se o método ainda não tiver sido confirmado.  
  
### <a name="ienumerable-support"></a>Suporte a IEnumerable  
 O <xref:System.Windows.Forms.BindingSource> componente permite ligar controles a <xref:System.Collections.IEnumerable> fontes de dados. Com esse componente, você pode associar a uma fonte de dados, como <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>um.  
  
 Quando uma <xref:System.Collections.IEnumerable> fonte de dados é atribuída <xref:System.Windows.Forms.BindingSource> ao componente, o <xref:System.Windows.Forms.BindingSource> <xref:System.Collections.IEnumerable> cria um <xref:System.ComponentModel.IBindingList> e adiciona o conteúdo da fonte de dados à lista.  
  
### <a name="design-time-support"></a>Suporte a tempo de design  
 Alguns tipos de objeto não podem ser criados em tempo de design, como objetos criados de uma classe de fábrica ou objetos retornados por um serviço Web. Às vezes é necessário associar os controles a esses tipos em tempo de design, mesmo que não haja nenhum objeto na memória aos quais os controles podem ser associados. Por exemplo, você pode precisar rotular os cabeçalhos de coluna de um <xref:System.Windows.Forms.DataGridView> controle com os nomes das propriedades públicas do seu tipo personalizado.  
  
 Para dar suporte a esse cenário <xref:System.Windows.Forms.BindingSource> , o componente dá suporte <xref:System.Type>à associação a um. Quando você atribui um <xref:System.Type> <xref:System.Windows.Forms.BindingSource.DataSource%2A> à propriedade, o <xref:System.Windows.Forms.BindingSource> componente cria um vazio <xref:System.ComponentModel.BindingList%601> de <xref:System.Type> itens. Todos os controles que você associar posteriormente <xref:System.Windows.Forms.BindingSource> ao componente serão alertados sobre a presença das propriedades ou do esquema do seu tipo no tempo de design ou em tempo de execução. Para obter mais informações, confira [Como: Associar um controle de Windows Forms a um](how-to-bind-a-windows-forms-control-to-a-type.md)tipo.  
  
### <a name="static-listbindinghelper-methods"></a>Métodos estáticos ListBindingHelper  
 Os <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>tipos <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>, `DataSource` e <xref:System.Windows.Forms.BindingSource> compartilham a lógica comum para gerar uma lista de um / `DataMember` par. Além disso, essa lógica comum é publicamente exposta para ser usada por autores de controle e terceiros nos seguintes métodos `static`:  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Classificação e filtragem com a interface IBindingListView  
 O <xref:System.Windows.Forms.BindingSource> componente implementa a <xref:System.ComponentModel.IBindingListView> interface, que estende a <xref:System.ComponentModel.IBindingList> interface. O <xref:System.ComponentModel.IBindingList> oferece classificação de coluna única <xref:System.ComponentModel.IBindingListView> e oferece classificação e filtragem avançadas. Com <xref:System.ComponentModel.IBindingListView>o, você pode classificar e filtrar itens na fonte de dados, se a fonte de dados também implementar uma dessas interfaces. O <xref:System.Windows.Forms.BindingSource> componente não fornece uma implementação de referência desses membros. Em vez disso, as chamadas são encaminhadas para a lista subjacente.  
  
 A tabela a seguir descreve as propriedades que você pode usar para classificação e filtragem.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Filter%2A>|Se a fonte de dados for <xref:System.ComponentModel.IBindingListView>um, Obtém ou define a expressão usada para filtrar quais linhas são exibidas.|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Sort%2A>|Se a fonte de dados for <xref:System.ComponentModel.IBindingList>um, Obtém ou define um nome de coluna usado para classificar e classificar informações de ordem.<br /><br /> - ou -<br /><br /> Se a fonte de dados for <xref:System.ComponentModel.IBindingListView> um e oferecer suporte à classificação avançada, o obterá vários nomes de coluna usados para classificação e ordem de classificação|  
  
### <a name="integration-with-bindingnavigator"></a>Integração com o BindingNavigator  
 Você pode usar o <xref:System.Windows.Forms.BindingSource> componente para associar qualquer Windows Forms controle a uma fonte de dados, mas <xref:System.Windows.Forms.BindingNavigator> o controle foi projetado especificamente para trabalhar com <xref:System.Windows.Forms.BindingSource> o componente. O <xref:System.Windows.Forms.BindingNavigator> controle fornece uma interface do usuário para controlar <xref:System.Windows.Forms.BindingSource> o item atual do componente. Por padrão, o <xref:System.Windows.Forms.BindingNavigator> controle fornece botões que correspondem aos métodos de navegação <xref:System.Windows.Forms.BindingSource> no componente. Para obter mais informações, confira [Como: Navegue dados com o controle](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)BindingNavigator Windows Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Visão geral do componente BindingSource](bindingsource-component-overview.md)
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Associação de dados do Windows Forms](../windows-forms-data-binding.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
- [Como: Associar um controle de Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Como: Refletir as atualizações da fonte de dados em um controle de Windows Forms com o BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
