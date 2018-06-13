---
title: Como definir o texto exibido por um controle dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: e41ce3e91e6c2a3c91dd0dc39723df1185721096
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532988"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>Como definir o texto exibido por um controle dos Windows Forms usando o designer
Controles dos Windows Forms normalmente exibem algum texto que está relacionado à função primária do controle. Por exemplo, um <xref:System.Windows.Forms.Button> controle exibe uma legenda que indica a ação que será executada quando o botão é clicado. Para todos os controles, você pode definir ou retornar o texto usando o <xref:System.Windows.Forms.Control.Text%2A> propriedade. Você pode alterar a fonte usando o <xref:System.Windows.Forms.Control.Font%2A> propriedade.  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a>Para definir o texto e a fonte com o designer  
  
1.  Na janela Propriedades, defina o <xref:System.Windows.Forms.Control.Text%2A> propriedade do controle para uma cadeia de caracteres apropriada.  
  
     Para criar uma tecla de atalho sublinhada, inclua um e comercial (&) antes da letra que será a tecla de atalho.  
  
2.  Na janela Propriedades, clique no botão de reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.Control.Font%2A> propriedade.  
  
     Na caixa de diálogo de fonte padrão, escolha a fonte, o estilo da fonte, o tamanho, efeitos (como riscado ou sublinhado) e o script que você deseja.  
  
## <a name="see-also"></a>Consulte também  
 [Como definir o texto exibido por um controle dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Usando fontes e texto](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
