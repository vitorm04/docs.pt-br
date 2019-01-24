---
title: 'Como: Definir o texto exibido por um Windows Forms usando o Designer de controle'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: cea2bcdb973e1deb5e0e6cf7fcc31b7c084dc446
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510579"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>Como: Definir o texto exibido por um Windows Forms usando o Designer de controle
Controles dos Windows Forms normalmente exibem algum texto que está relacionado à função primária do controle. Por exemplo, um <xref:System.Windows.Forms.Button> controle normalmente exibe uma legenda que indica qual ação será executada quando o botão é clicado. Para todos os controles, você pode definir ou retornar o texto usando o <xref:System.Windows.Forms.Control.Text%2A> propriedade. Você pode alterar a fonte usando o <xref:System.Windows.Forms.Control.Font%2A> propriedade.  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a>Para definir o texto e a fonte com o designer  
  
1.  Na janela Propriedades, defina o <xref:System.Windows.Forms.Control.Text%2A> propriedade do controle para uma cadeia de caracteres apropriada.  
  
     Para criar uma tecla de atalho sublinhada, inclua um e comercial (&) antes da letra que será a tecla de atalho.  
  
2.  Na janela Propriedades, clique no botão de reticências (![captura de tela VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.Control.Font%2A> propriedade.  
  
     Na caixa de diálogo de fonte padrão, escolha a fonte, o estilo da fonte, o tamanho, efeitos (como riscado ou sublinhado) e o script que você deseja.  
  
## <a name="see-also"></a>Consulte também
- [Como: Definir o texto exibido pelo controle de um Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Usando fontes e texto](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
- [Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
