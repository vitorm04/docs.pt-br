---
title: Como agrupar itens em um controle ListView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 40105ba9ffdc6f61cd9a9e382ba5d2610cbcbca2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417302"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Como agrupar itens em um controle ListView dos Windows Forms usando o designer
O recurso de agrupamento a <xref:System.Windows.Forms.ListView> controle permite que você exibir conjuntos de itens relacionados em grupos. Esses grupos são separados na tela por cabeçalhos de grupo horizontal que contêm os títulos do grupo. Você pode usar <xref:System.Windows.Forms.ListView> grupos para facilitar a navegação em listas grandes agrupando itens em ordem alfabética, por data, ou por qualquer outro agrupamento lógico. A imagem a seguir mostra alguns itens agrupados.  
  
 ![Grupos de ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
 Para habilitar o agrupamento, você deve criar primeiro um ou mais <xref:System.Windows.Forms.ListViewGroup> objetos no designer ou programaticamente. Depois que um grupo tiver sido definido, você poderá atribuir itens a ele.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> os grupos estão disponíveis apenas no [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando seu aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método. Em sistemas operacionais anteriores, nenhum código relacionado a grupos tem efeito e os grupos não serão exibidos. Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>Adicionar ou remover grupos no designer  
  
1.  No **propriedades** janela, clique no **reticências** (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) lado o <xref:System.Windows.Forms.ListView.Groups%2A> propriedade.  
  
     O **Editor de coleção de ListViewGroup** é exibido.  
  
2.  Para adicionar um grupo, clique no botão **Adicionar**. Você pode definir as propriedades do novo grupo, como o <xref:System.Windows.Forms.ListViewGroup.Header%2A> e <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> propriedades. Para remover um grupo, selecione-o e clique no botão **Remover**.  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>Atribuir itens aos grupos no designer  
  
1.  No **propriedades** janela, clique no **reticências** (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) lado o <xref:System.Windows.Forms.ListView.Items%2A> propriedade.  
  
     O **Editor de coleção de ListViewItem** é exibido.  
  
2.  Para adicionar um novo item, clique no botão **Adicionar**. Você pode definir as propriedades do novo item, como o <xref:System.Windows.Forms.ListViewItem.Text%2A> e <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> propriedades.  
  
3.  Selecione o <xref:System.Windows.Forms.ListViewItem.Group%2A> propriedade e escolha um grupo na lista suspensa.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [Controle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Recursos do Windows XP e controles do Windows Forms](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
