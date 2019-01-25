---
title: Visão geral do controle StatusBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: c3e52a91a31eb898d0176bc35a97cda7de9a8368
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491344"
---
# <a name="statusbar-control-overview-windows-forms"></a>Visão geral do controle StatusBar (Windows Forms)
> [!IMPORTANT]
>  O <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> controles substituam e adicionem funcionalidade para o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controla; no entanto, o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controles sejam mantidos para compatibilidade com versões anteriores e uso futuro, se você Escolha.  
  
 O [Controle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) dos Windows Forms é usado em formulários como uma área, normalmente exibido na parte inferior de uma janela, na qual um aplicativo pode exibir diversos tipos de informações de status. <xref:System.Windows.Forms.StatusBar> os controles podem ter painéis da barra de status sobre eles que exibem texto ou ícones para indicar o estado ou uma série de ícones em uma animação que indicam que um processo está funcionando. Por exemplo, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicando que o documento está sendo salvo.  
  
## <a name="using-the-statusbar-control"></a>Usando o controle StatusBar  
 Internet Explorer usa uma barra de status para indicar a URL de uma página quando o mouse passa sobre o hiperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] fornece informações sobre o local da página, local de seção e editar modos como sobrescrever e controle de revisão; e o Visual Studio usa a barra de status para fornecer informações contextuais, como informá-lo como manipular janelas encaixáveis como encaixadas ou flutuantes.  
  
 Você pode exibir uma única mensagem na barra de status, definindo o <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> propriedade para `false` (o padrão) e configurando o <xref:System.Windows.Forms.StatusBar.Text%2A> propriedade da barra de status para o texto que você deseja que apareça na barra de status. Você pode dividir a barra de status em painéis para exibir mais de um tipo de informação, configurando o <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> propriedade para `true` e usando o <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> método <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Como: Determinar qual painel no controle StatusBar dos Windows Forms foi clicado](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
