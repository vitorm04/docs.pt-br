---
title: Exibição de caracteres asiáticos com a propriedade ImeMode
ms.date: 03/30/2017
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
ms.openlocfilehash: 70be2506603856b1ce7787f74f3b9b203c155cec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>Exibição de caracteres asiáticos com a propriedade ImeMode
O <xref:System.Windows.Forms.Control.ImeMode%2A> propriedade é usada por formulários e controles para forçar um modo específico para um editor de método de entrada (IME). O IME é um componente essencial para escrever scripts chinês, japonês e coreano, pois esses sistemas de escrita têm mais caracteres que podem ser codificados para um teclado normal. Por exemplo, convém permitir que apenas caracteres ASCII em uma caixa de texto. Nesse caso, você pode definir o <xref:System.Windows.Forms.Control.ImeMode%2A> propriedade <xref:System.Windows.Forms.ImeMode> e os usuários somente poderão inserir caracteres ASCII para a caixa de texto. O valor padrão de <xref:System.Windows.Forms.Control.ImeMode%2A> é de propriedade <xref:System.Windows.Forms.ImeMode>, portanto, se você definir a propriedade de um formulário, todos os controles no formulário herdarão essa definição. Para obter mais informações, consulte <xref:System.Windows.Forms.Control.ImeMode%2A> ) e <xref:System.Windows.Forms.ImeMode>.  
  
## <a name="see-also"></a>Consulte também  
 [Globalizando o Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
