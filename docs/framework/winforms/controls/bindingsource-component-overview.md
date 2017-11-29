---
title: "Visão geral do componente BindingSource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf46a3d5207f3414bc8abd5fd7bdb904e91f07d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="bindingsource-component-overview"></a>Visão geral do componente BindingSource
O <xref:System.Windows.Forms.BindingSource> componente é projetado para simplificar o processo de associar controles a uma fonte de dados subjacente. O <xref:System.Windows.Forms.BindingSource> componente atua como um canal e para outros controles vincular a uma fonte de dados. Ele fornece uma abstração da conexão de dados do formulário enquanto passa comandos para a lista de dados subjacente. Além disso, você pode adicionar dados diretamente a ele para que o próprio componente funcione como uma fonte de dados.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>Componente BindingSource como um intermediário  
 O <xref:System.Windows.Forms.BindingSource> componente atua como a fonte de dados para alguns ou todos os controles no formulário. No Visual Studio, o <xref:System.Windows.Forms.BindingSource> podem ser associados a um controle por meio do `DataBindings` propriedade, que é acessível a partir de **propriedades** janela. Confira também [Como associar controles dos Windows Forms ao componente BindingSource usando o Designer](../../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md).  
  
 Você pode vincular o <xref:System.Windows.Forms.BindingSource> componente ambas as fontes de dados simples, como uma única propriedade de um objeto ou um conjunto básico de como <xref:System.Collections.ArrayList>e fontes de dados complexas, como uma tabela de banco de dados. O <xref:System.Windows.Forms.BindingSource> componente atua como um intermediário que fornece serviços de gerenciamento a associação e moeda. Em tempo de design ou tempo de execução, você pode associar um <xref:System.Windows.Forms.BindingSource> componente a uma fonte de dados complexos, definindo seu <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedades para o banco de dados e a tabela, respectivamente. A ilustração a seguir demonstra onde o <xref:System.Windows.Forms.BindingSource> componente se adapta a arquitetura de associação de dados existente.  
  
 ![Fonte de associação e arquitetura de vinculação de dados](../../../../docs/framework/winforms/controls/media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
>  Em tempo de design, algumas ações, como arrastar uma tabela de banco de dados de uma janela de dados em um formulário em branco, criará o <xref:System.Windows.Forms.BindingSource> componente, associá-lo à fonte de dados subjacente e adicionar controles de dados em uma única operação. Confira também [Associando controles dos Windows Forms a dados no Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>Componente BindingSource como uma fonte de dados  
 Se você começar a adicionar itens para o <xref:System.Windows.Forms.BindingSource> componente sem primeiro especificar uma lista deve ser vinculado, o componente atuam como uma fonte de dados de lista-style e aceitar esses adicionou itens.  
  
 Além disso, você pode escrever código para fornecer funcionalidade personalizada de "AddNew" por meio do <xref:System.Windows.Forms.BindingSource.AddingNew> evento, que é gerada quando o <xref:System.Windows.Forms.BindingSource.AddNew%2A> método é chamado antes do item que está sendo adicionado à lista. Para obter mais informações, consulte [Arquitetura do componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Navegação  
 Para usuários que precisam para navegar os dados em um formulário, o <xref:System.Windows.Forms.BindingNavigator> componente permite que você navegue e manipular dados em conjunto com um <xref:System.Windows.Forms.BindingSource> componente. Para obter mais informações, consulte [Controle BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Manipulação de dados  
 O: <xref:System.Windows.Forms.BindingSource> atua como um <xref:System.Windows.Forms.CurrencyManager> para todas as suas associações e pode, portanto, fornecer acesso a informações de moeda e a posição em relação a fonte de dados. A tabela a seguir mostra os membros de <xref:System.Windows.Forms.BindingSource> componente fornece para acessar e manipular os dados subjacentes.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Current%2A>|Obtém o item atual da fonte de dados.|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Position%2A>|Obtém ou define a posição atual na lista subjacente.|  
|Propriedade <xref:System.Windows.Forms.BindingSource.List%2A>|Obtém a lista que é a avaliação do <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> avaliação. Se <xref:System.Windows.Forms.BindingSource.DataMember%2A> não está definido, retorna a lista especificada por <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|Método <xref:System.Windows.Forms.BindingSource.Insert%2A>|Insere um item na lista no índice especificado.|  
|Método <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>|Remove o item atual da lista.|  
|Método <xref:System.Windows.Forms.BindingSource.EndEdit%2A>|Aplica as alterações pendentes à fonte de dados subjacente.|  
|Método <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>|Cancela a operação de edição atual.|  
|Método <xref:System.Windows.Forms.BindingSource.AddNew%2A>|Adiciona um novo item à lista subjacente. Se a fonte de dados implementa <xref:System.ComponentModel.IBindingList> e retorna um item a partir de <xref:System.Windows.Forms.BindingSource.AddingNew> evento, adiciona esse item. Caso contrário, a solicitação é passada para a lista <xref:System.ComponentModel.IBindingList.AddNew%2A> método. Se a lista subjacente não é um <xref:System.ComponentModel.IBindingList>, o item é criado automaticamente por meio de seu construtor padrão público.|  
  
## <a name="sorting-and-filtering"></a>Classificando e filtrando  
 Normalmente, você deve trabalhar com uma exibição ordenada ou filtrada da fonte de dados. A tabela a seguir mostra os membros que o <xref:System.Windows.Forms.BindingSource> fornece de fonte de dados do componente.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Sort%2A>|Se a fonte de dados é um <xref:System.ComponentModel.IBindingList>, obtém ou define um nome de coluna usado para classificação e informações de ordem de classificação. Se a fonte de dados é um <xref:System.ComponentModel.IBindingListView> e dá suporte à classificação, avançada obtém vários nomes de coluna usados para classificar e informações de ordem de classificação|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Filter%2A>|Se a fonte de dados é um <xref:System.ComponentModel.IBindingListView>, obtém ou define a expressão usada para filtrar quais linhas são exibidas.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Arquitetura do componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-architecture.md)  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Controle BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Vinculação de dados dos Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
