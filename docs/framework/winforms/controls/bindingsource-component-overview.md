---
title: Visão geral do componente BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
ms.openlocfilehash: 9c9c9fb574b9f3e687b2d8d5c4606bfb66ebfa64
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364456"
---
# <a name="bindingsource-component-overview"></a>Visão geral do componente BindingSource
O <xref:System.Windows.Forms.BindingSource> componente é projetado para simplificar o processo de vinculação de controles a uma fonte de dados subjacente. O <xref:System.Windows.Forms.BindingSource> componente atua como um canal e uma fonte de dados para que outros controles se associem. Ele fornece uma abstração da conexão de dados do formulário enquanto passa comandos para a lista de dados subjacente. Além disso, você pode adicionar dados diretamente a ele para que o próprio componente funcione como uma fonte de dados.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>Componente BindingSource como um intermediário  
 O <xref:System.Windows.Forms.BindingSource> componente atua como a fonte de dados para alguns ou todos os controles no formulário. No Visual Studio, o <xref:System.Windows.Forms.BindingSource> pode ser associado a um controle por meio `DataBindings` da propriedade, que é acessível na janela **Propriedades** . Consulte [também como: Associar controles de Windows Forms com o componente BindingSource usando o](bind-wf-controls-with-the-bindingsource.md)designer.  
  
 Você pode associar o <xref:System.Windows.Forms.BindingSource> componente a ambas as fontes de dados simples, como uma única propriedade de um objeto ou uma coleção <xref:System.Collections.ArrayList>básica, como, e fontes de dados complexas, como uma tabela de banco de dado. O <xref:System.Windows.Forms.BindingSource> componente atua como um intermediário que fornece serviços de associação e gerenciamento de moedas. Em tempo de design ou em tempo de execução, você <xref:System.Windows.Forms.BindingSource> pode associar um componente a uma fonte de dados <xref:System.Windows.Forms.BindingSource.DataSource%2A> complexa <xref:System.Windows.Forms.BindingSource.DataMember%2A> definindo suas propriedades e como o banco de dados e a tabela, respectivamente. A ilustração a seguir demonstra onde <xref:System.Windows.Forms.BindingSource> o componente se encaixa na arquitetura de vinculação de dados existente.  
  
 ![Fonte de associação e arquitetura de vinculação de dados](./media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
>  Em tempo de design, algumas ações, como arrastar uma tabela de banco de dados de uma janela de dado para um formulário <xref:System.Windows.Forms.BindingSource> em branco, criarão o componente, o associarão à fonte de dados subjacente e adicionarão controles com reconhecimento de dados em uma única operação. Confira também [Associando controles dos Windows Forms a dados no Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>Componente BindingSource como uma fonte de dados  
 Se você começar a adicionar itens ao <xref:System.Windows.Forms.BindingSource> componente sem primeiro especificar uma lista a ser associada, o componente atuará como uma fonte de dados de estilo de lista e aceitará esses itens adicionados.  
  
 Além disso, você pode escrever código para fornecer funcionalidade personalizada "AddNew" por meio do <xref:System.Windows.Forms.BindingSource.AddingNew> evento, que é gerado quando o <xref:System.Windows.Forms.BindingSource.AddNew%2A> método é chamado antes do item que está sendo adicionado à lista. Para obter mais informações, consulte [Arquitetura do componente BindingSource](bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Navegação  
 Para usuários que precisam navegar pelos dados em um formulário, o <xref:System.Windows.Forms.BindingNavigator> componente permite que você navegue e manipule dados, em coordenação com um <xref:System.Windows.Forms.BindingSource> componente. Para obter mais informações, consulte [Controle BindingNavigator](bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Manipulação de dados  
 O: <xref:System.Windows.Forms.BindingSource> atua como um <xref:System.Windows.Forms.CurrencyManager> para todas as suas associações e pode, portanto, fornecer acesso às informações de moeda e de posição referentes à fonte de dados. A tabela a seguir mostra os membros que <xref:System.Windows.Forms.BindingSource> o componente fornece para acessar e manipular os dados subjacentes.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Current%2A>|Obtém o item atual da fonte de dados.|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Position%2A>|Obtém ou define a posição atual na lista subjacente.|  
|Propriedade <xref:System.Windows.Forms.BindingSource.List%2A>|Obtém a lista que é a avaliação da <xref:System.Windows.Forms.BindingSource.DataSource%2A> avaliação e. <xref:System.Windows.Forms.BindingSource.DataMember%2A> Se <xref:System.Windows.Forms.BindingSource.DataMember%2A> não estiver definido, retornará a lista especificada por <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|Método <xref:System.Windows.Forms.BindingSource.Insert%2A>|Insere um item na lista no índice especificado.|  
|Método <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>|Remove o item atual da lista.|  
|Método <xref:System.Windows.Forms.BindingSource.EndEdit%2A>|Aplica as alterações pendentes à fonte de dados subjacente.|  
|Método <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>|Cancela a operação de edição atual.|  
|Método <xref:System.Windows.Forms.BindingSource.AddNew%2A>|Adiciona um novo item à lista subjacente. Se a fonte de dados <xref:System.ComponentModel.IBindingList> implementar e retornar um item <xref:System.Windows.Forms.BindingSource.AddingNew> do evento, o adicionará esse item. Caso contrário, a solicitação será passada para o método <xref:System.ComponentModel.IBindingList.AddNew%2A> da lista. Se a lista subjacente não for um <xref:System.ComponentModel.IBindingList>, o item será criado automaticamente por meio de seu construtor público sem parâmetros.|  
  
## <a name="sorting-and-filtering"></a>Classificando e filtrando  
 Normalmente, você deve trabalhar com uma exibição ordenada ou filtrada da fonte de dados. A tabela a seguir mostra os membros que <xref:System.Windows.Forms.BindingSource> a fonte de dados de componente fornece.  
  
|Membro|Descrição|  
|------------|-----------------|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Sort%2A>|Se a fonte de dados for <xref:System.ComponentModel.IBindingList>um, Obtém ou define um nome de coluna usado para classificar e classificar informações de ordem. Se a fonte de dados for <xref:System.ComponentModel.IBindingListView> um e oferecer suporte à classificação avançada, o obterá vários nomes de coluna usados para classificação e classificação de informações de ordem|  
|Propriedade <xref:System.Windows.Forms.BindingSource.Filter%2A>|Se a fonte de dados for <xref:System.ComponentModel.IBindingListView>um, Obtém ou define a expressão usada para filtrar quais linhas são exibidas.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Arquitetura do componente BindingSource](bindingsource-component-architecture.md)
- [Componente BindingSource](bindingsource-component.md)
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Associação de dados do Windows Forms](../windows-forms-data-binding.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
