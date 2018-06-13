---
title: Arquitetura do componente BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: b0334bd7a0bc5ff46c43fd7ee549422d98c35efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529254"
---
# <a name="bindingsource-component-architecture"></a>Arquitetura do componente BindingSource
Com o <xref:System.Windows.Forms.BindingSource> componente, você pode associar universalmente todos os controles de formulários do Windows para fontes de dados.  
  
 O <xref:System.Windows.Forms.BindingSource> componente simplifica o processo de associar controles a uma fonte de dados e fornece as seguintes vantagens sobre associação de dados tradicional:  
  
-   Habilita a associação a objetos comerciais em tempo de design.  
  
-   Encapsula <xref:System.Windows.Forms.CurrencyManager> funcionalidade e expõe <xref:System.Windows.Forms.CurrencyManager> eventos em tempo de design.  
  
-   Simplifica a criação de uma lista que oferece suporte a <xref:System.ComponentModel.IBindingList> interface, fornecendo a notificação de alteração da lista de fontes de dados que não dão suporte nativamente a lista de notificação de alteração.  
  
-   Fornece um ponto de extensibilidade para o <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> método.  
  
-   Fornece um nível de indireção entre a fonte de dados e o controle. A indireção é importante quando a fonte de dados pode se alterar em tempo de execução.  
  
-   Interage com outros controles de Windows Forms relacionados a dados, especificamente o <xref:System.Windows.Forms.BindingNavigator> e <xref:System.Windows.Forms.DataGridView> controles.  
  
 Por esses motivos, o <xref:System.Windows.Forms.BindingSource> componente é a melhor maneira de associar os controles de formulários do Windows para fontes de dados.  
  
## <a name="bindingsource-features"></a>Recursos do BindingSource  
 O <xref:System.Windows.Forms.BindingSource> componente fornece vários recursos para vincular controles a dados. Com esses recursos, você pode implementar a maioria dos cenários de associação de dados com quase nenhuma codificação de sua parte.  
  
 O <xref:System.Windows.Forms.BindingSource> componente faz isso fornecendo uma interface consistente para acessar vários tipos diferentes de fontes de dados. Isso significa que você usa o mesmo procedimento para associar a qualquer tipo. Por exemplo, você pode anexar o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade para um <xref:System.Data.DataSet> ou a um objeto comercial e em ambos os casos você usar o mesmo conjunto de propriedades, métodos e eventos para manipular a fonte de dados.  
  
 A interface consistente fornecida pelo <xref:System.Windows.Forms.BindingSource> componente simplifica o processo de associação de dados a controles. Para notificação de alteração de tipos de fonte de dados que fornecem o <xref:System.Windows.Forms.BindingSource> componente automaticamente se comunica alterações entre o controle e a fonte de dados. Para tipos de fonte de dados que não fornecem notificação de alteração, são fornecidos eventos que permitem gerar notificações de alteração. A lista a seguir mostra os recursos com suporte a <xref:System.Windows.Forms.BindingSource> componente:  
  
-   Indireção.  
  
-   Gerenciamento de moeda.  
  
-   Fonte de dados como uma lista.  
  
-   <xref:System.Windows.Forms.BindingSource> como um <xref:System.ComponentModel.IBindingList>.  
  
-   Criação de item personalizado.  
  
-   Criação de item transacional.  
  
-   <xref:System.Collections.IEnumerable> suporte.  
  
-   Suporte a tempo de design.  
  
-   Estático <xref:System.Windows.Forms.ListBindingHelper> métodos.  
  
-   Classificação e filtragem com o <xref:System.ComponentModel.IBindingListView> interface.  
  
-   Integração com <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Indireção  
 O <xref:System.Windows.Forms.BindingSource> componente fornece um nível de indireção entre um controle e uma fonte de dados. Em vez de vincular um controle diretamente a uma fonte de dados, você vincula o controle para um <xref:System.Windows.Forms.BindingSource>, e anexar a fonte de dados para o <xref:System.Windows.Forms.BindingSource> do componente <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade.  
  
 Com esse nível de indireção, você pode alterar a fonte de dados sem redefinir a associação de controle. Isso oferece as seguintes funcionalidades:  
  
-   Você pode anexar o <xref:System.Windows.Forms.BindingSource> para diferentes fontes de dados, mantendo as associações de controle atual.  
  
-   Você pode alterar os itens na fonte de dados e notificar os controles associados. Para obter mais informações, consulte [Como refletir atualizações feitas na fonte de dados em um controle dos Windows Forms com o BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
-   Você pode vincular a um <xref:System.Type> em vez de um objeto na memória. Para obter mais informações, consulte [Como associar um controle dos Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md). Em seguida, você pode associar a um objeto em tempo de execução.  
  
### <a name="currency-management"></a>Gerenciamento de moedas  
 O <xref:System.Windows.Forms.BindingSource> componente implementa o <xref:System.Windows.Forms.ICurrencyManagerProvider> interface para lidar com gerenciamento de moeda para você. Com o <xref:System.Windows.Forms.ICurrencyManagerProvider> interface, você também pode acessar para o Gerenciador de moeda para um <xref:System.Windows.Forms.BindingSource>, além do Gerenciador de moeda para outro <xref:System.Windows.Forms.BindingSource> associado ao mesmo <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 O <xref:System.Windows.Forms.BindingSource> encapsula o componente <xref:System.Windows.Forms.CurrencyManager> expõe as mais comuns e funcionalidade <xref:System.Windows.Forms.CurrencyManager> propriedades e eventos. A tabela a seguir descreve alguns dos membros relacionados ao gerenciamento de moeda.  
  
 Propriedade <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>  
 Obtém o Gerenciador de moeda associado a <xref:System.Windows.Forms.BindingSource>.  
  
 Método <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A>  
 Se não houver outro <xref:System.Windows.Forms.BindingSource> associado para o membro de dados especificado, obtém seu Gerenciador de moeda.  
  
 Propriedade <xref:System.Windows.Forms.BindingSource.Current%2A>  
 Obtém o item atual da fonte de dados.  
  
 Propriedade <xref:System.Windows.Forms.BindingSource.Position%2A>  
 Obtém ou define a posição atual na lista subjacente.  
  
 Método <xref:System.Windows.Forms.BindingSource.EndEdit%2A>  
 Aplica as alterações pendentes à fonte de dados subjacente.  
  
 Método <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>  
 Cancela a operação de edição atual.  
  
### <a name="data-source-as-a-list"></a>Fonte de dados como uma lista  
 O <xref:System.Windows.Forms.BindingSource> componente implementa o <xref:System.ComponentModel.IBindingListView> e <xref:System.ComponentModel.ITypedList> interfaces. Com essa implementação, você pode usar o <xref:System.Windows.Forms.BindingSource> componente como uma fonte de dados, sem qualquer armazenamento externo.  
  
 Quando o <xref:System.Windows.Forms.BindingSource> componente está anexado a uma fonte de dados, ele expõe a fonte de dados como uma lista.  
  
 O <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade pode ser definida para várias fontes de dados. Isso inclui tipos, objetos e listas de tipos. A fonte de dados resultante será exposta como uma lista. A tabela a seguir mostra algumas das fontes de dados comuns e a avaliação de lista resultante.  
  
|Propriedade DataSource|Listar resultados|  
|-------------------------|------------------|  
|Uma referência nula (`Nothing` no Visual Basic)|Vazio <xref:System.ComponentModel.IBindingList> de objetos. Adicionar um item define a lista como o tipo do item adicionado.|  
|Uma referência nula (`Nothing` no Visual Basic) com <xref:System.Windows.Forms.BindingSource.DataMember%2A> definido|Não há suporte para; gera <xref:System.ArgumentException>.|  
|Tipo fora da lista ou objeto do tipo "T"|Vazio <xref:System.ComponentModel.IBindingList> do tipo "T".|  
|Instância de matriz|Um <xref:System.ComponentModel.IBindingList> que contém os elementos da matriz.|  
|<xref:System.Collections.IEnumerable> Instância|Um <xref:System.ComponentModel.IBindingList> que contém o <xref:System.Collections.IEnumerable> itens|  
|Instância de lista que contém o tipo "T"|Um <xref:System.ComponentModel.IBindingList> instância que contém o tipo "T".|  
  
 Além disso, <xref:System.Windows.Forms.BindingSource.DataSource%2A> pode ser definido como outros tipos de lista, como <xref:System.ComponentModel.IListSource> e <xref:System.ComponentModel.ITypedList>e o <xref:System.Windows.Forms.BindingSource> manipulará corretamente. Nesse caso, o tipo que está contido na lista deve ter um construtor padrão.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource como uma IBindingList  
 O <xref:System.Windows.Forms.BindingSource> componente fornece membros para acessar e manipular os dados subjacentes, como um <xref:System.ComponentModel.IBindingList>. A tabela a seguir descreve alguns desses membros.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.List%2A>|Obtém a lista resultante da avaliação da <xref:System.Windows.Forms.BindingSource.DataSource%2A> ou <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedades.|  
|Método <xref:System.Windows.Forms.BindingSource.AddNew%2A>|Adiciona um novo item à lista subjacente. Aplica-se a fontes de dados que implementam o <xref:System.ComponentModel.IBindingList> de interface e permitir a adição de itens (ou seja, o <xref:System.Windows.Forms.BindingSource.AllowNew%2A> está definida como `true`).|  
  
### <a name="custom-item-creation"></a>Criação de item personalizado  
 Você pode manipular o <xref:System.Windows.Forms.BindingSource.AddingNew> evento para fornecer sua própria lógica de criação do item. O <xref:System.Windows.Forms.BindingSource.AddingNew> evento ocorre antes de um novo objeto é adicionado para o <xref:System.Windows.Forms.BindingSource>. Esse evento é gerado após o <xref:System.Windows.Forms.BindingSource.AddNew%2A> método é chamado, mas antes do novo item é adicionado à lista subjacente. Manipulando esse evento, você pode fornecer o comportamento de criação de item personalizado sem derivando de <xref:System.Windows.Forms.BindingSource> classe. Para obter mais informações, veja [Como personalizar a adição de item com o BindingSource dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md).  
  
### <a name="transactional-item-creation"></a>Criação de item transacional  
 O <xref:System.Windows.Forms.BindingSource> componente implementa o <xref:System.ComponentModel.ICancelAddNew> interface, que permite a criação de item transacional. Depois que um novo item provisoriamente é criado usando uma chamada para <xref:System.Windows.Forms.BindingSource.AddNew%2A>, a adição pode ser confirmada ou revertida das seguintes maneiras:  
  
-   O <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> método explicitamente confirmará a adição pendente.  
  
-   A realização de outra operação de coleção, como uma inserção, remoção ou mover, confirmará implicitamente a adição pendente.  
  
-   O <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> método reverterá a adição pendente se o método ainda não tenha sido confirmado.  
  
### <a name="ienumerable-support"></a>Suporte a IEnumerable  
 O <xref:System.Windows.Forms.BindingSource> componente permite que os controles de associação <xref:System.Collections.IEnumerable> fontes de dados. Com esse componente, você pode vincular a uma fonte de dados, como um <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 Quando um <xref:System.Collections.IEnumerable> fonte de dados é atribuída para o <xref:System.Windows.Forms.BindingSource> componente, o <xref:System.Windows.Forms.BindingSource> cria um <xref:System.ComponentModel.IBindingList> e adiciona o conteúdo do <xref:System.Collections.IEnumerable> fonte de dados para a lista.  
  
### <a name="design-time-support"></a>Suporte a tempo de design  
 Alguns tipos de objeto não podem ser criados em tempo de design, como objetos criados de uma classe de fábrica ou objetos retornados por um serviço Web. Às vezes é necessário associar os controles a esses tipos em tempo de design, mesmo que não haja nenhum objeto na memória aos quais os controles podem ser associados. Por exemplo, convém rotular os cabeçalhos de coluna de uma <xref:System.Windows.Forms.DataGridView> controle com os nomes de propriedades públicas do seu tipo personalizado.  
  
 Para dar suporte a esse cenário, o <xref:System.Windows.Forms.BindingSource> componente oferece suporte a associação a um <xref:System.Type>. Quando você atribui um <xref:System.Type> para o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade, o <xref:System.Windows.Forms.BindingSource> componente cria vazio <xref:System.ComponentModel.BindingList%601> de <xref:System.Type> itens. Os controles que você associa subsequentemente ao <xref:System.Windows.Forms.BindingSource> componente será alertado sobre a presença do esquema do seu tipo ou propriedades em tempo de design ou em tempo de execução. Para obter mais informações, consulte [Como associar um controle dos Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Métodos estáticos ListBindingHelper  
 O <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>, e <xref:System.Windows.Forms.BindingSource> tipos de toda a lógica comum compartilhamento para gerar uma lista de um `DataSource` / `DataMember` par. Além disso, essa lógica comum é publicamente exposta para ser usada por autores de controle e terceiros nos seguintes métodos `static`:  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Classificação e filtragem com a interface IBindingListView  
 O <xref:System.Windows.Forms.BindingSource> componente implementa o <xref:System.ComponentModel.IBindingListView> interface, que estende o <xref:System.ComponentModel.IBindingList> interface. O <xref:System.ComponentModel.IBindingList> oferece a única coluna de classificação e o <xref:System.ComponentModel.IBindingListView> oferece avançados de classificação e filtragem. Com <xref:System.ComponentModel.IBindingListView>, você pode classificar e filtrar itens na fonte de dados, se a fonte de dados também implementa uma dessas interfaces. O <xref:System.Windows.Forms.BindingSource> componente não fornece uma implementação de referência desses membros. Em vez disso, as chamadas são encaminhadas para a lista subjacente.  
  
 A tabela a seguir descreve as propriedades que você pode usar para classificação e filtragem.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Filter%2A>|Se a fonte de dados é um <xref:System.ComponentModel.IBindingListView>, obtém ou define a expressão usada para filtrar quais linhas são exibidas.|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Sort%2A>|Se a fonte de dados é um <xref:System.ComponentModel.IBindingList>, obtém ou define um nome de coluna usado para classificação e informações de ordem de classificação.<br /><br /> -ou-<br /><br /> Se a fonte de dados é um <xref:System.ComponentModel.IBindingListView> e dá suporte à classificação, avançada obtém vários nomes de coluna usados para classificação e a ordem de classificação|  
  
### <a name="integration-with-bindingnavigator"></a>Integração com o BindingNavigator  
 Você pode usar o <xref:System.Windows.Forms.BindingSource> componente para associar qualquer controle Windows Forms a uma fonte de dados, mas o <xref:System.Windows.Forms.BindingNavigator> controle foi projetado especificamente para trabalhar com o <xref:System.Windows.Forms.BindingSource> componente. O <xref:System.Windows.Forms.BindingNavigator> controle fornece uma interface do usuário para controlar o <xref:System.Windows.Forms.BindingSource> item atual do componente. Por padrão, o <xref:System.Windows.Forms.BindingNavigator> controle fornece botões que correspondem aos métodos de navegação no <xref:System.Windows.Forms.BindingSource> componente. Para obter mais informações, consulte [Como navegar em dados com o controle BindingNavigator dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Visão geral do componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [Controle BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Associação de dados do Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Como associar um controle do Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Como refletir atualizações feitas na fonte de dados em um controle do Windows Forms com o BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
