---
title: Visão geral do controle ListView (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: 3ac1bc5482d00419ec8a41815633150e30b4039a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613981"
---
# <a name="listview-control-overview-windows-forms"></a>Visão geral do controle ListView (Windows Forms)
O controle <xref:System.Windows.Forms.ListView> do Windows Forms exibe uma lista de itens com ícones. É possível usar uma exibição de lista para criar uma interface do usuário, como o painel direito do Windows Explorer. O controle tem quatro modos de exibição: LargeIcon, SmallIcon, lista e detalhes.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>O que você pode fazer com o Controle ListView  
  
> [!NOTE]
>  O “organizar lado a lado”, um modo de exibição adicional, está disponível apenas nos sistemas operacionais Windows XP e Windows Server 2003. Para obter mais informações, confira [Como: Habilitar a exibição de bloco em um Windows Forms controle ListView](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 O modo LargeIcon exibe ícones grandes ao lado do texto do item; os itens aparecerão em várias colunas se o controle for grande o suficiente. O modo SmallIcon funciona da mesma forma, mas exibe ícones pequenos. O modo de Lista exibe ícones pequenos, mas sempre em uma única coluna. O modo de Detalhes exibe itens em várias colunas. Para obter detalhes, consulte [como: Adicionar colunas para o Windows Forms controle ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md). O modo de exibição é determinado pelo <xref:System.Windows.Forms.ListView.View%2A> propriedade. Todos os modos de exibição podem exibir imagens de listas de imagens. Para obter detalhes, consulte [como: Exibir ícones para o Windows Forms controle ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 A tabela a seguir lista alguns do <xref:System.Windows.Forms.ListView> membros e as exibições são válidos no.  
  
|Membro do ListView|Exibir|  
|---------------------|----------|  
|Propriedade <xref:System.Windows.Forms.ListView.Alignment%2A>|<xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>|  
|Propriedade <xref:System.Windows.Forms.ListView.AutoArrange%2A>|<xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>|  
|Método <xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>|<xref:System.Windows.Forms.View.Details>|  
|Propriedade <xref:System.Windows.Forms.ListView.Columns%2A>|<xref:System.Windows.Forms.View.Details> ou <xref:System.Windows.Forms.View.Tile>|  
|Evento <xref:System.Windows.Forms.ListView.DrawSubItem>|<xref:System.Windows.Forms.View.Details>|  
|Método <xref:System.Windows.Forms.ListView.FindItemWithText%2A>|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List> ou <xref:System.Windows.Forms.View.Tile>|  
|Método <xref:System.Windows.Forms.ListView.FindNearestItem%2A>|<xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.LargeIcon>|  
|Método <xref:System.Windows.Forms.ListView.GetItemAt%2A>|<xref:System.Windows.Forms.View.Details> ou <xref:System.Windows.Forms.View.Tile>|  
|Propriedade <xref:System.Windows.Forms.ListView.Groups%2A>|Todas as exibições, exceto <xref:System.Windows.Forms.View.List>|  
|Propriedade <xref:System.Windows.Forms.ListView.HeaderStyle%2A>|<xref:System.Windows.Forms.View.Details>.|  
|Propriedade <xref:System.Windows.Forms.ListView.InsertionMark%2A>|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.Tile>|  
  
 A propriedade de chave do <xref:System.Windows.Forms.ListView> controle é <xref:System.Windows.Forms.ListView.Items%2A>, que contém os itens exibidos pelo controle. O <xref:System.Windows.Forms.ListView.SelectedItems%2A> propriedade contém uma coleção de itens selecionados no momento no controle. O usuário pode selecionar vários itens, por exemplo, para arrastar e soltar vários itens de cada vez em outro controle, se o <xref:System.Windows.Forms.ListView.MultiSelect%2A> estiver definida como `true`. O <xref:System.Windows.Forms.ListView> controle poderá exibir caixas de seleção ao lado dos itens, se o <xref:System.Windows.Forms.ListView.CheckBoxes%2A> estiver definida como `true`.  
  
 O <xref:System.Windows.Forms.ListView.Activation%2A> propriedade determina o tipo de ação que o usuário deve executar para ativar um item na lista: as opções são <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>, e <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick> a ativação exige um único clique para ativar o item. <xref:System.Windows.Forms.ItemActivation.TwoClick> ativação exige que o usuário clicar duas vezes para ativar o item; um único clique altera a cor do texto do item. <xref:System.Windows.Forms.ItemActivation.Standard> ativação exige que o usuário clicar duas vezes para ativar um item, mas o item não altera a aparência.  
  
 O <xref:System.Windows.Forms.ListView> controle também dá suporte a estilos visuais e outros recursos disponíveis na plataforma do Windows XP, incluindo o agrupamento, a exibição lado a lado e marcas de inserção. Para obter mais informações, consulte [Recursos do Windows XP e Controles dos Windows Forms](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ListView>
- [Controle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [Como: Adicionar e remover itens com o controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Como: Adicionar colunas para o controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Como: Exibir ícones para o controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Como: Exibir subitens em colunas com o controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Como: Selecione um Item no controle de ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Como: Agrupar itens em um controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
- [Como: Exibir uma marca de inserção em um controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Como: Adicionar recursos de pesquisa a um controle ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Como: Criar uma Interface do usuário Multipainel com Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)
