---
title: Visão geral do controle ProgressBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: bd2b9615b0061a8f2133229edb49357cde69b39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="progressbar-control-overview-windows-forms"></a>Visão geral do controle ProgressBar (Windows Forms)
> [!IMPORTANT]
>  O controle <xref:System.Windows.Forms.ToolStripProgressBar> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ProgressBar>, no entanto, o controle <xref:System.Windows.Forms.ProgressBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar> controle indica o progresso de um processo, exibindo um número apropriado de retângulos organizados em uma barra horizontal. Quando o processo for concluído, a barra será preenchida. Barras de progresso são normalmente usadas para conceder ao usuário uma ideia de quanto tempo levará para um processo ser concluído, como por exemplo, quando um arquivo grande está sendo carregado.  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.ProgressBar> controle só pode ser orientado horizontalmente no formulário.  
  
## <a name="key-properties-and-methods"></a>Propriedades e métodos de tecla  
 Propriedades de chave do <xref:System.Windows.Forms.ProgressBar> controle são <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, e <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. O <xref:System.Windows.Forms.ProgressBar.Minimum%2A> e <xref:System.Windows.Forms.ProgressBar.Maximum%2A> propriedades definir os valores mínimos e máximo que pode exibir a barra de progresso. O <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade representa o progresso que foi feito para concluir a operação. Como a barra exibida no controle é composta de blocos, o valor exibido pelo <xref:System.Windows.Forms.ProgressBar> controle apenas aproxima o <xref:System.Windows.Forms.ProgressBar.Value%2A> valor atual da propriedade. Com base no tamanho do <xref:System.Windows.Forms.ProgressBar> controle, o <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade determina quando exibir o próximo bloco.  
  
 A maneira mais comum para atualizar o valor de andamento atual é escrever código para definir o <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade. No exemplo de carregamento de um arquivo grande, você pode definir o máximo para o tamanho do arquivo em quilobytes. Por exemplo, se o <xref:System.Windows.Forms.ProgressBar.Maximum%2A> propriedade será definida como 100, o <xref:System.Windows.Forms.ProgressBar.Minimum%2A> está definida como 10 e o <xref:System.Windows.Forms.ProgressBar.Value%2A> estiver definida como 50, 5 retângulos serão exibidos. Isso é metade do número que pode ser exibido.  
  
 No entanto, existem outras maneiras para modificar o valor exibido pelo <xref:System.Windows.Forms.ProgressBar> controle, além de configuração de <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade diretamente. O <xref:System.Windows.Forms.ProgressBar.Step%2A> propriedade pode ser usada para especificar um valor a incrementar o <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade. Em seguida, chamar o <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> método incrementar o valor. Para variar o valor de incremento, você pode usar o <xref:System.Windows.Forms.ProgressBar.Increment%2A> método e especifique um valor com o qual incrementar o <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade.  
  
 Outro controle graficamente informando ao usuário sobre uma ação atual é o <xref:System.Windows.Forms.StatusBar> controle.  
  
> [!IMPORTANT]
>  O <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> controles substituir e adiciona a funcionalidade para o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controla; no entanto, o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controles são mantidos para compatibilidade com versões anteriores e o uso futuro, se você Escolha.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ProgressBar>  
 [Controle ProgressBar](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
