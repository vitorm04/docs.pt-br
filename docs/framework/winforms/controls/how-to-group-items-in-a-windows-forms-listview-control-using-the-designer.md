---
title: Como agrupar itens em um controle ListView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: c532cadc5b42c26f1598c4e7586309cf690456bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539330"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Como agrupar itens em um controle ListView dos Windows Forms usando o designer
O recurso de agrupamento do <xref:System.Windows.Forms.ListView> controle permite que você exibir conjuntos de itens relacionados em grupos. Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo. Você pode usar <xref:System.Windows.Forms.ListView> grupos para facilitar a navegação listas grandes mais fáceis com o agrupamento de itens em ordem alfabética, por data, ou por qualquer outro grupo lógico. A imagem a seguir mostra alguns itens agrupados.  
  
 ![Grupos de ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
 Para habilitar o agrupamento, você primeiro deve criar um ou mais <xref:System.Windows.Forms.ListViewGroup> objetos no designer ou programaticamente. Depois que um grupo tiver sido definido, você poderá atribuir itens a ele.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> os grupos estão disponíveis apenas em [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando o aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método. Em sistemas operacionais anteriores, nenhum código relacionado a grupos tem efeito e os grupos não serão exibidos. Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>Adicionar ou remover grupos no designer  
  
1.  No **propriedades** janela, clique no **reticências** (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) próximo ao o <xref:System.Windows.Forms.ListView.Groups%2A> propriedade.  
  
     O **Editor de coleção de ListViewGroup** é exibido.  
  
2.  Para adicionar um grupo, clique no botão **Adicionar**. Você pode definir propriedades do novo grupo, como o <xref:System.Windows.Forms.ListViewGroup.Header%2A> e <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> propriedades. Para remover um grupo, selecione-o e clique no botão **Remover**.  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>Atribuir itens aos grupos no designer  
  
1.  No **propriedades** janela, clique no **reticências** (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) próximo ao o <xref:System.Windows.Forms.ListView.Items%2A> propriedade.  
  
     O **Editor de coleção de ListViewItem** é exibido.  
  
2.  Para adicionar um novo item, clique no botão **Adicionar**. Você pode definir propriedades do novo item, como o <xref:System.Windows.Forms.ListViewItem.Text%2A> e <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> propriedades.  
  
3.  Selecione o <xref:System.Windows.Forms.ListViewItem.Group%2A> propriedade e escolha um grupo na lista suspensa.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [Controle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Recursos do Windows XP e controles do Windows Forms](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
