---
title: Visão geral do componente BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
ms.openlocfilehash: 2237ba71487afc132f9164243a664b277397ccfa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098631"
---
# <a name="bindingsource-component-overview"></a>Visão geral do componente BindingSource
O <xref:System.Windows.Forms.BindingSource> componente é projetado para simplificar o processo de associar controles a uma fonte de dados subjacente. O <xref:System.Windows.Forms.BindingSource> componente atua como um canal e uma fonte de dados para vincular a outros controles. Ele fornece uma abstração da conexão de dados do formulário enquanto passa comandos para a lista de dados subjacente. Além disso, você pode adicionar dados diretamente a ele para que o próprio componente funcione como uma fonte de dados.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>Componente BindingSource como um intermediário  
 O <xref:System.Windows.Forms.BindingSource> componente atua como a fonte de dados para alguns ou todos os controles no formulário. No Visual Studio, o <xref:System.Windows.Forms.BindingSource> pode ser associado a um controle por meio do `DataBindings` propriedade, que é acessível a partir de **propriedades** janela. Consulte também [como: Associar controles dos Windows Forms com o componente BindingSource usando o Designer](bind-wf-controls-with-the-bindingsource.md).  
  
 Você pode associar o <xref:System.Windows.Forms.BindingSource> componente para ambas as fontes de dados simples, como uma única propriedade de um objeto ou um conjunto básico de ter <xref:System.Collections.ArrayList>e fontes de dados complexos, como uma tabela de banco de dados. O <xref:System.Windows.Forms.BindingSource> componente atua como um intermediário que fornece serviços de gerenciamento a moeda e associação. Em tempo de design ou tempo de execução, você pode associar uma <xref:System.Windows.Forms.BindingSource> componente a uma fonte de dados complexos, definindo seu <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedades para o banco de dados e a tabela, respectivamente. A ilustração a seguir demonstra onde o <xref:System.Windows.Forms.BindingSource> componente se adapta a arquitetura de vinculação de dados existente.  
  
 ![Fonte de associação e arquitetura de vinculação de dados](./media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
>  Em tempo de design, algumas ações, como arrastar uma tabela de banco de dados de uma janela de dados em um formulário em branco, criará o <xref:System.Windows.Forms.BindingSource> componente, associá-lo à fonte de dados subjacente e adicionar controles de reconhecimento de dados em uma operação. Confira também [Associando controles dos Windows Forms a dados no Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>Componente BindingSource como uma fonte de dados  
 Se você começar a adicionar itens para o <xref:System.Windows.Forms.BindingSource> componente sem primeiro especificar uma lista deve ser vinculado, o componente atuam como uma fonte de dados do estilo de lista e aceitar esses adicionou itens.  
  
 Além disso, você pode escrever código para fornecer funcionalidade "AddNew" personalizada por meio das <xref:System.Windows.Forms.BindingSource.AddingNew> evento, que é gerado quando o <xref:System.Windows.Forms.BindingSource.AddNew%2A> método é chamado antes que o item que está sendo adicionado à lista. Para obter mais informações, consulte [Arquitetura do componente BindingSource](bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Navegação  
 Para usuários que precisam navegar nos dados em um formulário, o <xref:System.Windows.Forms.BindingNavigator> componente permite que você navegue e manipule dados em conjunto com um <xref:System.Windows.Forms.BindingSource> componente. Para obter mais informações, consulte [Controle BindingNavigator](bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Manipulação de dados  
 A: <xref:System.Windows.Forms.BindingSource> atua como um <xref:System.Windows.Forms.CurrencyManager> para todas as suas associações e pode, portanto, fornecer acesso a informações de moeda e posição em relação à fonte de dados. A tabela a seguir mostra os membros que o <xref:System.Windows.Forms.BindingSource> componente fornece para acessar e manipular os dados subjacentes.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Current%2A>|Obtém o item atual da fonte de dados.|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Position%2A>|Obtém ou define a posição atual na lista subjacente.|  
|Propriedade <xref:System.Windows.Forms.BindingSource.List%2A>|Obtém a lista que é a avaliação do <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> avaliação. Se <xref:System.Windows.Forms.BindingSource.DataMember%2A> não estiver definido, retorna a lista especificada por <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|Método <xref:System.Windows.Forms.BindingSource.Insert%2A>|Insere um item na lista no índice especificado.|  
|Método <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>|Remove o item atual da lista.|  
|Método <xref:System.Windows.Forms.BindingSource.EndEdit%2A>|Aplica as alterações pendentes à fonte de dados subjacente.|  
|Método <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>|Cancela a operação de edição atual.|  
|Método <xref:System.Windows.Forms.BindingSource.AddNew%2A>|Adiciona um novo item à lista subjacente. Se a fonte de dados implementa <xref:System.ComponentModel.IBindingList> e retorna um item do <xref:System.Windows.Forms.BindingSource.AddingNew> evento, adiciona esse item. Caso contrário, a solicitação é passada para a lista <xref:System.ComponentModel.IBindingList.AddNew%2A> método. Se a lista subjacente não é um <xref:System.ComponentModel.IBindingList>, o item é criado automaticamente por meio de seu construtor padrão público.|  
  
## <a name="sorting-and-filtering"></a>Classificando e filtrando  
 Normalmente, você deve trabalhar com uma exibição ordenada ou filtrada da fonte de dados. A tabela a seguir mostra os membros que o <xref:System.Windows.Forms.BindingSource> fornece de fonte de dados do componente.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Sort%2A>|Se a fonte de dados for um <xref:System.ComponentModel.IBindingList>, obtém ou define um nome de coluna usado para classificação e informações de ordem de classificação. Se a fonte de dados for um <xref:System.ComponentModel.IBindingListView> e dá suporte à classificação, avançada obtém vários nomes de colunas usados para classificação e informações de ordem de classificação|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Filter%2A>|Se a fonte de dados for um <xref:System.ComponentModel.IBindingListView>, obtém ou define a expressão usada para filtrar quais linhas são exibidas.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Arquitetura do componente BindingSource](bindingsource-component-architecture.md)
- [Componente BindingSource](bindingsource-component.md)
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Associação de dados do Windows Forms](../windows-forms-data-binding.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
