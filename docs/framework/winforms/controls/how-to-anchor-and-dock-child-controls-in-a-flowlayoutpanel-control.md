---
title: Como ancorar e encaixar controles filho em um controle FlowLayoutPanel
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 183e9ea4a8451b3d1ed59aa5200dd4da22e50cf1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Como ancorar e encaixar controles filho em um controle FlowLayoutPanel
O <xref:System.Windows.Forms.FlowLayoutPanel> controle oferece suporte a <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades em seus controles filhos.  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Ancorar e encaixar controles filho em um controle FlowLayoutPanel  
  
1.  Criar um <xref:System.Windows.Forms.FlowLayoutPanel> controle do formulário.  
  
2.  Definir o <xref:System.Windows.Forms.Control.Width%2A> do <xref:System.Windows.Forms.FlowLayoutPanel> controle **300**e defina seu <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> para <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
3.  Criar dois <xref:System.Windows.Forms.Button> controla e colocá-los no <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
4.  Definir o <xref:System.Windows.Forms.Control.Width%2A> do primeiro botão **200**.  
  
5.  Definir o <xref:System.Windows.Forms.Control.Dock%2A> propriedade do segundo botão para <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    > [!NOTE]
    >  O segundo botão assume a mesma largura que o primeiro. Ele não se estique na largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
6.  Definir o <xref:System.Windows.Forms.Control.Dock%2A> propriedade do segundo botão para `None`. Isso faz com que o botão assuma a largura original.  
  
7.  Definir o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade do segundo botão para `Left, Right`.  
  
    > [!IMPORTANT]
    >  O segundo botão assume a mesma largura que o primeiro. Ele não se estique na largura do <xref:System.Windows.Forms.FlowLayoutPanel> controle. Essa é a regra geral de ancoragem e encaixe no <xref:System.Windows.Forms.FlowLayoutPanel> controle: para obter instruções de fluxo vertical, o <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a largura de uma coluna implícita do maior controle filho na coluna. Todos os outros controles nesta coluna com <xref:System.Windows.Forms.Control.Anchor%2A> ou <xref:System.Windows.Forms.Control.Dock%2A> propriedades são alinhadas ou ampliadas para ajustar essa coluna implícita. O comportamento funciona de maneira similar a direções de fluxo horizontal. O <xref:System.Windows.Forms.FlowLayoutPanel> controle calcula a altura de uma linha implícita do controle filho mais alto na linha, e todos os controles filho ancorada ou ancorada nesta linha são alinhados ou dimensionados para ajustar a linha implícita.  
  
## <a name="example"></a>Exemplo  
 A ilustração a seguir mostra quatro botões que estão ancorado e encaixado em relação a um botão azul em um <xref:System.Windows.Forms.FlowLayoutPanel>. O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.LeftToRight>.  
  
 ![Ancoragem FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 A ilustração a seguir mostra quatro botões que estão ancorado e encaixado em relação a um botão azul em um <xref:System.Windows.Forms.FlowLayoutPanel>. O <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> é <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
 ![Ancoragem FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 O exemplo de código a seguir demonstra várias <xref:System.Windows.Forms.Control.Anchor%2A> valores de propriedades de um <xref:System.Windows.Forms.Button> controlar um <xref:System.Windows.Forms.FlowLayoutPanel> controle.  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [Visão geral do controle FlowLayoutPanel](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
