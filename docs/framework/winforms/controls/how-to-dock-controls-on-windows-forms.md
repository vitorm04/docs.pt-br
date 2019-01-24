---
title: 'Como: Encaixar controles nos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: f4a9d3bcf7f9db1634da2b2f06177c05061af28e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733539"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Como: Encaixar controles nos Windows Forms
Você pode encaixar controles nas bordas do formulário ou fazer com que eles preencham o contêiner do controle (um controle de contêiner ou formulário). Por exemplo, o Windows Explorer encaixa seu <xref:System.Windows.Forms.TreeView> controle para o lado esquerdo da janela e sua <xref:System.Windows.Forms.ListView> controle para o lado direito da janela. Use o <xref:System.Windows.Forms.Control.Dock%2A> propriedade para todos os controles de Windows Forms visíveis definir o modo de encaixe.  
  
> [!NOTE]
>  Controles são encaixados na ordem z inversa.  
  
 O <xref:System.Windows.Forms.Control.Dock%2A> propriedade interage com o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade. Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
### <a name="to-dock-a-control"></a>Para encaixar um controle  
  
1.  Selecione o controle que deseja encaixar.  
  
2.  Na janela Propriedades, clique na seta à direita do <xref:System.Windows.Forms.Control.Dock%2A> propriedade.  
  
     Um editor será exibido que mostra uma série de caixas que representam as bordas e o centro do formulário.  
  
3.  Clique no botão que representa a borda do formulário no qual você deseja encaixar o controle. Para preencher o conteúdo do controle de contêiner ou formulário do controle, clique na caixa do centro. Clique em **(nenhum)** para desabilitar o encaixe.  
  
     O controle é redimensionado automaticamente para ajustar os limites da borda encaixada.  
  
    > [!NOTE]
    >  Controles herdados devem ser `Protected` para poderem ser encaixados. Para alterar o nível de acesso de um controle, defina sua propriedade **Modifier** na janela Propriedades.  
  
## <a name="see-also"></a>Consulte também
- [Controles dos Windows Forms](../../../../docs/framework/winforms/controls/index.md)
- [Organizando Controles nos Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
- [Controles dos Windows Forms por função](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
- [Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Visão geral da propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
- [Como: Ancoragem de controles nos Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
