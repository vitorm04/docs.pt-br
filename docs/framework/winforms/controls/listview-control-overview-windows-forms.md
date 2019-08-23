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
ms.openlocfilehash: 7b7eac942a7e857ad731c0f77389e84aee287c08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952161"
---
# <a name="listview-control-overview-windows-forms"></a>Visão geral do controle ListView (Windows Forms)
O controle <xref:System.Windows.Forms.ListView> do Windows Forms exibe uma lista de itens com ícones. É possível usar uma exibição de lista para criar uma interface do usuário, como o painel direito do Windows Explorer. O controle tem quatro modos de exibição: LargeIcon, SmallIcon, List e details.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>O que você pode fazer com o Controle ListView  
  
> [!NOTE]
> O “organizar lado a lado”, um modo de exibição adicional, está disponível apenas nos sistemas operacionais Windows XP e Windows Server 2003. Para obter mais informações, confira [Como: Habilitar exibição de bloco em um Windows Forms controle](how-to-enable-tile-view-in-a-windows-forms-listview-control.md)ListView.  
  
 O modo LargeIcon exibe ícones grandes ao lado do texto do item; os itens aparecerão em várias colunas se o controle for grande o suficiente. O modo SmallIcon funciona da mesma forma, mas exibe ícones pequenos. O modo de Lista exibe ícones pequenos, mas sempre em uma única coluna. O modo de Detalhes exibe itens em várias colunas. Para obter detalhes, confira [Como: Adicione colunas ao controle](how-to-add-columns-to-the-windows-forms-listview-control.md)Windows Forms ListView. O modo de exibição é determinado pela <xref:System.Windows.Forms.ListView.View%2A> propriedade. Todos os modos de exibição podem exibir imagens de listas de imagens. Para obter detalhes, confira [Como: Exiba os ícones para o controle](how-to-display-icons-for-the-windows-forms-listview-control.md)Windows Forms ListView.  
  
 A tabela a seguir lista alguns dos <xref:System.Windows.Forms.ListView> Membros e os modos de exibição em que eles são válidos.  
  
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
|Propriedade <xref:System.Windows.Forms.ListView.Groups%2A>|Todas as exibições, exceto<xref:System.Windows.Forms.View.List>|  
|Propriedade <xref:System.Windows.Forms.ListView.HeaderStyle%2A>|<xref:System.Windows.Forms.View.Details>.|  
|Propriedade <xref:System.Windows.Forms.ListView.InsertionMark%2A>|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon> ou <xref:System.Windows.Forms.View.Tile>|  
  
 A propriedade de chave do <xref:System.Windows.Forms.ListView> controle é <xref:System.Windows.Forms.ListView.Items%2A>, que contém os itens exibidos pelo controle. A <xref:System.Windows.Forms.ListView.SelectedItems%2A> propriedade contém uma coleção dos itens selecionados no momento no controle. O usuário pode selecionar vários itens, por exemplo, para arrastar e soltar vários itens de cada vez para outro controle, se <xref:System.Windows.Forms.ListView.MultiSelect%2A> a propriedade for definida `true`como. O <xref:System.Windows.Forms.ListView> controle pode exibir caixas de seleção ao lado dos itens, se <xref:System.Windows.Forms.ListView.CheckBoxes%2A> a propriedade for definida `true`como.  
  
 A <xref:System.Windows.Forms.ListView.Activation%2A> propriedade determina o tipo de ação que o usuário deve executar para ativar um item na lista: as opções são <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>e <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick>a ativação requer um único clique para ativar o item. <xref:System.Windows.Forms.ItemActivation.TwoClick>a ativação exige que o usuário clique duas vezes para ativar o item; um único clique altera a cor do texto do item. <xref:System.Windows.Forms.ItemActivation.Standard>a ativação exige que o usuário clique duas vezes para ativar um item, mas o item não altera a aparência.  
  
 O <xref:System.Windows.Forms.ListView> controle também dá suporte aos estilos visuais e outros recursos disponíveis na plataforma Windows XP, incluindo agrupamento, exibição de bloco e marcas de inserção.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListView>
- [Controle ListView](listview-control-windows-forms.md)
- [Como: Adicionar e remover itens com o controle Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Como: Adicionar colunas ao controle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Como: Exibir ícones para o controle Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Como: Exibir subitens em colunas com o controle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Como: Selecionar um item no controle Windows Forms ListView](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Como: Agrupar itens em um controle Windows Forms ListView](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Como: Exibir uma marca de inserção em um controle ListView Windows Forms](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Como: Adicionar recursos de pesquisa a um controle ListView](how-to-add-search-capabilities-to-a-listview-control.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Como: Criar uma interface do usuário multipainel com Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
