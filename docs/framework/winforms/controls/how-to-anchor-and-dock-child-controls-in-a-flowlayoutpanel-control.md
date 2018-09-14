---
title: Como ancorar e encaixar controles filho em um controle FlowLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: b53547e8e61e69834f262407de490422e6b6bb00
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615135"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Como ancorar e encaixar controles filho em um controle FlowLayoutPanel
O <xref:System.Windows.Forms.FlowLayoutPanel> controlar dá suporte a <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades em seus controles filho.  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Ancorar e encaixar controles filho em um controle FlowLayoutPanel  
  
1.  Criar um <xref:System.Windows.Forms.FlowLayoutPanel> controle no formulário.  
  
2.  Defina a <xref:System.Windows.Forms.Control.Width%2A> do <xref:System.Windows.Forms.FlowLayoutPanel> o controle para **300**e defina seu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> para <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
3.  Criar duas <xref:System.Windows.Forms.Button> controles e colocá-los no <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
4.  Defina as <xref:System.Windows.Forms.Control.Width%2A> do primeiro botão para **200**.  
  
5.  Defina as <xref:System.Windows.Forms.Control.Dock%2A> propriedade do segundo botão para <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    > [!NOTE]
    >  O segundo botão assume a mesma largura que o primeiro. Ele não se alonga pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
6.  Defina as <xref:System.Windows.Forms.Control.Dock%2A> propriedade do segundo botão para `None`. Isso faz com que o botão assuma a largura original.  
  
7.  Defina as <xref:System.Windows.Forms.Control.Anchor%2A> propriedade do segundo botão para `Left, Right`.  
  
    > [!IMPORTANT]
    >  O segundo botão assume a mesma largura que o primeiro. Ele não se alonga pela largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle. Esta é a regra geral de ancoragem e encaixe no controle de <xref:System.Windows.Forms.FlowLayoutPanel> controle: para direções de fluxo vertical, o <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a largura de uma coluna implícita do controle filho mais largo na coluna. Todos os outros controles nesta coluna com <xref:System.Windows.Forms.Control.Anchor%2A> ou <xref:System.Windows.Forms.Control.Dock%2A> propriedades são alinhadas ou alongadas para caber nesta coluna implícita. O comportamento funciona de maneira similar a direções de fluxo horizontal. O <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a altura de uma linha implícita do controle filho mais alto na linha, e todos os controles filho encaixados ou ancorados nesta linha são alinhados ou dimensionados para se ajustar à linha implícita.  
  
## <a name="example"></a>Exemplo  
 A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão azul em um <xref:System.Windows.Forms.FlowLayoutPanel>. O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.LeftToRight>.  
  
 ![Ancoragem FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 A ilustração a seguir mostra quatro botões que são ancorados e encaixados em relação ao botão azul em um <xref:System.Windows.Forms.FlowLayoutPanel>. O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
 ![Ancoragem FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 O exemplo de código a seguir demonstra vários <xref:System.Windows.Forms.Control.Anchor%2A> valores de propriedades de um <xref:System.Windows.Forms.Button> de controle em um <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [Visão geral do controle FlowLayoutPanel](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
