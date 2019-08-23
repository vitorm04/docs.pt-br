---
title: 'Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 9a00fcd53211dd126c0e9203d6d577959b971e70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922914"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel
O <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.Control.Dock%2A> controle<xref:System.Windows.Forms.Control.Anchor%2A> oferece suporte às propriedades e em seus controles filho.  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Ancorar e encaixar controles filho em um controle FlowLayoutPanel  
  
1. Crie um <xref:System.Windows.Forms.FlowLayoutPanel> controle no formulário.  
  
2. Defina o <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.TopDown>do controle como 300 e defina seu como. <xref:System.Windows.Forms.FlowLayoutPanel>  
  
3. Crie dois <xref:System.Windows.Forms.Button> controles e coloque-os <xref:System.Windows.Forms.FlowLayoutPanel> no controle.  
  
4. Defina o <xref:System.Windows.Forms.Control.Width%2A> do primeiro botão como **200**.  
  
5. Defina a <xref:System.Windows.Forms.Control.Dock%2A> Propriedade do segundo botão como <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    > [!NOTE]
    > O segundo botão assume a mesma largura que o primeiro. Ele não se estende pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
6. Defina a <xref:System.Windows.Forms.Control.Dock%2A> Propriedade do segundo botão como `None`. Isso faz com que o botão assuma a largura original.  
  
7. Defina a <xref:System.Windows.Forms.Control.Anchor%2A> Propriedade do segundo botão como `Left, Right`.  
  
    > [!IMPORTANT]
    >  O segundo botão assume a mesma largura que o primeiro. Ele não se estende pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle. Essa é a regra geral para ancorar e encaixar <xref:System.Windows.Forms.FlowLayoutPanel> no controle: para direções de fluxo vertical <xref:System.Windows.Forms.FlowLayoutPanel> , o controle calcula a largura de uma coluna implícita do controle filho mais largo na coluna. Todos os outros controles nesta coluna com <xref:System.Windows.Forms.Control.Anchor%2A> propriedades <xref:System.Windows.Forms.Control.Dock%2A> or são alinhados ou ampliados para se ajustarem a essa coluna implícita. O comportamento funciona de maneira similar a direções de fluxo horizontal. O <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a altura de uma linha implícita do controle filho mais alto na linha e todos os controles filho ancorados ou ancorados nessa linha são alinhados ou dimensionados para se ajustarem à linha implícita.  
  
## <a name="example"></a>Exemplo  
 A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão <xref:System.Windows.Forms.FlowLayoutPanel>azul em um. O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.LeftToRight>.  
  
 ![Ancoragem FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão <xref:System.Windows.Forms.FlowLayoutPanel>azul em um. O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
 ![Ancoragem FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 O exemplo de código a seguir <xref:System.Windows.Forms.Control.Anchor%2A> demonstra vários valores de <xref:System.Windows.Forms.Button> propriedade para um <xref:System.Windows.Forms.FlowLayoutPanel> controle em um controle.  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Visão geral do controle FlowLayoutPanel](flowlayoutpanel-control-overview.md)
