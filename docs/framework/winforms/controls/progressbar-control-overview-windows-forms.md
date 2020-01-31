---
title: Visão geral do controle ProgressBar
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: a0c4a0401d06614ab3ad148b932ebc64080c592c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741286"
---
# <a name="progressbar-control-overview-windows-forms"></a>Visão geral do controle ProgressBar (Windows Forms)
> [!IMPORTANT]
> O controle <xref:System.Windows.Forms.ToolStripProgressBar> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ProgressBar>, no entanto, o controle <xref:System.Windows.Forms.ProgressBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 O controle de <xref:System.Windows.Forms.ProgressBar> de Windows Forms indica o progresso de um processo exibindo um número apropriado de retângulos organizados em uma barra horizontal. Quando o processo for concluído, a barra será preenchida. Barras de progresso são normalmente usadas para conceder ao usuário uma ideia de quanto tempo levará para um processo ser concluído, como por exemplo, quando um arquivo grande está sendo carregado.  
  
> [!NOTE]
> O controle de <xref:System.Windows.Forms.ProgressBar> só pode ser orientado horizontalmente no formulário.  
  
## <a name="key-properties-and-methods"></a>Propriedades e métodos de tecla  
 As propriedades de chave do controle de <xref:System.Windows.Forms.ProgressBar> são <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>e <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. As propriedades <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> definem os valores máximo e mínimo que a barra de progresso pode exibir. A propriedade <xref:System.Windows.Forms.ProgressBar.Value%2A> representa o progresso que foi feito para concluir a operação. Como a barra exibida no controle é composta de blocos, o valor exibido pelo controle de <xref:System.Windows.Forms.ProgressBar> aproxima-se apenas do valor atual da propriedade <xref:System.Windows.Forms.ProgressBar.Value%2A>. Com base no tamanho do controle de <xref:System.Windows.Forms.ProgressBar>, a propriedade <xref:System.Windows.Forms.ProgressBar.Value%2A> determina quando exibir o próximo bloco.  
  
 A maneira mais comum de atualizar o valor de progresso atual é escrever o código para definir a propriedade <xref:System.Windows.Forms.ProgressBar.Value%2A>. No exemplo de carregamento de um arquivo grande, você pode definir o máximo para o tamanho do arquivo em quilobytes. Por exemplo, se a propriedade <xref:System.Windows.Forms.ProgressBar.Maximum%2A> for definida como 100, a propriedade <xref:System.Windows.Forms.ProgressBar.Minimum%2A> será definida como 10 e a propriedade <xref:System.Windows.Forms.ProgressBar.Value%2A> será definida como 50, serão exibidos 5 retângulos. Isso é metade do número que pode ser exibido.  
  
 No entanto, há outras maneiras de modificar o valor exibido pelo controle de <xref:System.Windows.Forms.ProgressBar>, além de definir a propriedade <xref:System.Windows.Forms.ProgressBar.Value%2A> diretamente. A propriedade <xref:System.Windows.Forms.ProgressBar.Step%2A> pode ser usada para especificar um valor para o qual incrementar a propriedade <xref:System.Windows.Forms.ProgressBar.Value%2A>. Em seguida, chamar o método <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> aumentará o valor. Para variar o valor de incremento, você pode usar o método <xref:System.Windows.Forms.ProgressBar.Increment%2A> e especificar um valor com o qual incrementar a propriedade <xref:System.Windows.Forms.ProgressBar.Value%2A>.  
  
 Outro controle que informa graficamente ao usuário sobre uma ação atual é o controle de <xref:System.Windows.Forms.StatusBar>.  
  
> [!IMPORTANT]
> Os controles <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> substituem e adicionam funcionalidade aos controles <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel>; no entanto, os controles <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ProgressBar>
- [Controle ProgressBar](progressbar-control-windows-forms.md)
