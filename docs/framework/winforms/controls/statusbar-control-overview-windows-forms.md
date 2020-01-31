---
title: Visão geral do controle StatusBar
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: b0b97bc3cb0291871e1fd113d82d0b480b53cdba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742869"
---
# <a name="statusbar-control-overview-windows-forms"></a>Visão geral do controle StatusBar (Windows Forms)
> [!IMPORTANT]
> Os controles <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> substituem e adicionam funcionalidade aos controles <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel>; no entanto, os controles <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
 O [Controle StatusBar](statusbar-control-windows-forms.md) dos Windows Forms é usado em formulários como uma área, normalmente exibido na parte inferior de uma janela, na qual um aplicativo pode exibir diversos tipos de informações de status. os controles de <xref:System.Windows.Forms.StatusBar> podem ter painéis de barra de status que exibem texto ou ícones para indicar o estado ou uma série de ícones em uma animação que indicam que um processo está funcionando; por exemplo, o Microsoft Word indica que o documento está sendo salvo.  
  
## <a name="using-the-statusbar-control"></a>Usando o controle StatusBar  
 O Internet Explorer usa uma barra de status para indicar a URL de uma página quando o mouse rola sobre o hiperlink; O Microsoft Word fornece informações sobre localização da página, localização da seção e modos de edição, como sobrescrever e controle de revisão; e o Visual Studio usa a barra de status para fornecer informações sensíveis ao contexto, como dizer como manipular janelas encaixáveis como encaixadas ou flutuantes.  
  
 Você pode exibir uma única mensagem na barra de status definindo a propriedade <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> como `false` (o padrão) e definindo a propriedade <xref:System.Windows.Forms.StatusBar.Text%2A> da barra de status como o texto que você deseja que apareça na barra de status. Você pode dividir a barra de status em painéis para exibir mais de um tipo de informação, definindo a propriedade <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> como `true` e usando o método <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> de <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado](determine-which-panel-wf-statusbar-control-was-clicked.md)
