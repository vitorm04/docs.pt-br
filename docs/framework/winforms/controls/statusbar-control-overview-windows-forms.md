---
title: Visão geral do controle StatusBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: bd58d4c70e3a3c88e57fe242957f669d1944fd71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964430"
---
# <a name="statusbar-control-overview-windows-forms"></a>Visão geral do controle StatusBar (Windows Forms)
> [!IMPORTANT]
> Os <xref:System.Windows.Forms.StatusStrip> controles <xref:System.Windows.Forms.ToolStripStatusLabel> e <xref:System.Windows.Forms.StatusBar> substituem e adicionam funcionalidade aos <xref:System.Windows.Forms.StatusBarPanel> controles e; no entanto <xref:System.Windows.Forms.StatusBarPanel> , os <xref:System.Windows.Forms.StatusBar> controles e são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolha.  
  
 O [Controle StatusBar](statusbar-control-windows-forms.md) dos Windows Forms é usado em formulários como uma área, normalmente exibido na parte inferior de uma janela, na qual um aplicativo pode exibir diversos tipos de informações de status. <xref:System.Windows.Forms.StatusBar>os controles podem ter painéis de barra de status que exibem texto ou ícones para indicar o estado ou uma série de ícones em uma animação que indicam que um processo está funcionando; por exemplo, o Microsoft Word indica que o documento está sendo salvo.  
  
## <a name="using-the-statusbar-control"></a>Usando o controle StatusBar  
 O Internet Explorer usa uma barra de status para indicar a URL de uma página quando o mouse rola sobre o hiperlink; O Microsoft Word fornece informações sobre localização da página, localização da seção e modos de edição, como sobrescrever e controle de revisão; e o Visual Studio usa a barra de status para fornecer informações sensíveis ao contexto, como dizer como manipular janelas encaixáveis como encaixadas ou flutuantes.  
  
 Você pode exibir uma única mensagem na barra de status definindo a <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> Propriedade como `false` (o padrão) e definindo a <xref:System.Windows.Forms.StatusBar.Text%2A> propriedade da barra de status como o texto que você deseja que apareça na barra de status. Você pode dividir a barra de status em painéis para exibir mais de um tipo de informação, definindo <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> a propriedade `true` como e usando <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> o método <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>de.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Como: Determine em qual painel no controle StatusBar Windows Forms foi clicado](determine-which-panel-wf-statusbar-control-was-clicked.md)
