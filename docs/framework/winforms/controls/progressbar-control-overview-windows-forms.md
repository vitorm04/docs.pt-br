---
title: Visão geral do controle ProgressBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: 7dd434492cd688527ddbce5aaffa442a0b40a9e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968313"
---
# <a name="progressbar-control-overview-windows-forms"></a>Visão geral do controle ProgressBar (Windows Forms)
> [!IMPORTANT]
> O controle <xref:System.Windows.Forms.ToolStripProgressBar> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ProgressBar>, no entanto, o controle <xref:System.Windows.Forms.ProgressBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 O controle <xref:System.Windows.Forms.ProgressBar> de Windows Forms indica o progresso de um processo exibindo um número apropriado de retângulos organizados em uma barra horizontal. Quando o processo for concluído, a barra será preenchida. Barras de progresso são normalmente usadas para conceder ao usuário uma ideia de quanto tempo levará para um processo ser concluído, como por exemplo, quando um arquivo grande está sendo carregado.  
  
> [!NOTE]
> O <xref:System.Windows.Forms.ProgressBar> controle só pode ser orientado horizontalmente no formulário.  
  
## <a name="key-properties-and-methods"></a>Propriedades e métodos de tecla  
 As <xref:System.Windows.Forms.ProgressBar> principais propriedades do controle são <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>e <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. As <xref:System.Windows.Forms.ProgressBar.Minimum%2A> propriedades <xref:System.Windows.Forms.ProgressBar.Maximum%2A> e definem os valores máximo e mínimo que a barra de progresso pode exibir. A <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade representa o progresso que foi feito para concluir a operação. Como a barra exibida no controle é composta de blocos, o valor exibido pelo <xref:System.Windows.Forms.ProgressBar> controle aproxima-se apenas do <xref:System.Windows.Forms.ProgressBar.Value%2A> valor atual da propriedade. Com base no tamanho do <xref:System.Windows.Forms.ProgressBar> controle, a <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade determina quando exibir o próximo bloco.  
  
 A maneira mais comum de atualizar o valor de progresso atual é escrever o código para definir <xref:System.Windows.Forms.ProgressBar.Value%2A> a propriedade. No exemplo de carregamento de um arquivo grande, você pode definir o máximo para o tamanho do arquivo em quilobytes. Por exemplo, se a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> propriedade for definida como 100, a <xref:System.Windows.Forms.ProgressBar.Minimum%2A> propriedade será definida como 10 e a <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade será definida como 50, serão exibidos 5 retângulos. Isso é metade do número que pode ser exibido.  
  
 No entanto, há outras maneiras de modificar o valor exibido pelo <xref:System.Windows.Forms.ProgressBar> controle, além de definir a <xref:System.Windows.Forms.ProgressBar.Value%2A> propriedade diretamente. A <xref:System.Windows.Forms.ProgressBar.Step%2A> propriedade pode ser usada para especificar um valor para o qual <xref:System.Windows.Forms.ProgressBar.Value%2A> incrementar a propriedade. Em seguida, chamar <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> o método aumentará o valor. Para variar o valor de incremento, você pode <xref:System.Windows.Forms.ProgressBar.Increment%2A> usar o método e especificar um valor com o qual <xref:System.Windows.Forms.ProgressBar.Value%2A> incrementar a propriedade.  
  
 Outro controle que informa graficamente ao usuário sobre uma ação atual é o <xref:System.Windows.Forms.StatusBar> controle.  
  
> [!IMPORTANT]
> Os <xref:System.Windows.Forms.StatusStrip> controles <xref:System.Windows.Forms.ToolStripStatusLabel> e <xref:System.Windows.Forms.StatusBar> substituem e adicionam funcionalidade aos <xref:System.Windows.Forms.StatusBarPanel> controles e; no entanto <xref:System.Windows.Forms.StatusBarPanel> , os <xref:System.Windows.Forms.StatusBar> controles e são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolha.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ProgressBar>
- [Controle ProgressBar](progressbar-control-windows-forms.md)
