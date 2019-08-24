---
title: 'Como: Encaixar controles nos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58b61af306385a245bedf16e370e6830c370a622
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987483"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Como: Encaixar controles em Windows Forms

Você pode encaixar controles nas bordas do formulário ou fazer com que eles preencham o contêiner do controle (um controle de contêiner ou formulário). Por exemplo, o Windows Explorer encaixa seu <xref:System.Windows.Forms.TreeView> controle no lado esquerdo da janela e seu <xref:System.Windows.Forms.ListView> controle no lado direito da janela. Use a <xref:System.Windows.Forms.Control.Dock%2A> propriedade para todos os controles de Windows Forms visíveis para definir o modo de encaixe.

> [!NOTE]
> Controles são encaixados na ordem z inversa.

A <xref:System.Windows.Forms.Control.Dock%2A> Propriedade interage com a <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade. Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](autosize-property-overview.md).

## <a name="to-dock-a-control"></a>Para encaixar um controle

1. No Visual Studio, selecione o controle que você deseja encaixar.

2. Na janela **Propriedades** , clique na seta à direita da <xref:System.Windows.Forms.Control.Dock%2A> propriedade.

   Um editor será exibido que mostra uma série de caixas que representam as bordas e o centro do formulário.

3. Clique no botão que representa a borda do formulário no qual você deseja encaixar o controle. Para preencher o conteúdo do controle de contêiner ou formulário do controle, clique na caixa do centro. Clique em **(nenhum)** para desabilitar o encaixe.

   O controle é redimensionado automaticamente para ajustar os limites da borda encaixada.

   > [!NOTE]
   > Controles herdados devem ser `Protected` para poderem ser encaixados. Para alterar o nível de acesso de um controle, defina sua propriedade modificador na janela **Propriedades** .

## <a name="see-also"></a>Consulte também

- [Controles dos Windows Forms](index.md)
- [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)
- [Controles dos Windows Forms por função](windows-forms-controls-by-function.md)
- [Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Visão geral da propriedade AutoSize](autosize-property-overview.md)
- [Como: Controles de ancoragem em Windows Forms](how-to-anchor-controls-on-windows-forms.md)
