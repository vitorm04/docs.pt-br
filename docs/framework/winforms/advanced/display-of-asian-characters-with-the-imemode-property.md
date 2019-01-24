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
ms.openlocfilehash: 25602e1a878443bd54411dfd6481581abebda5c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500507"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>Exibição de caracteres asiáticos com a propriedade ImeMode
O <xref:System.Windows.Forms.Control.ImeMode%2A> por formulários e controles, a propriedade é usada para forçar um modo específico para um editor de método de entrada (IME). O IME é um componente essencial para escrever scripts de chinês, japonês e coreano, já que esses sistemas de escrita têm mais caracteres que podem ser codificados para um teclado normal. Por exemplo, você talvez queira permitir que apenas caracteres ASCII em uma caixa de texto específica. Nesse caso, você pode definir as <xref:System.Windows.Forms.Control.ImeMode%2A> propriedade para <xref:System.Windows.Forms.ImeMode> e os usuários somente poderão inserir caracteres ASCII para a caixa de texto. O valor padrão de <xref:System.Windows.Forms.Control.ImeMode%2A> é de propriedade <xref:System.Windows.Forms.ImeMode>, portanto, se você definir a propriedade de um formulário, todos os controles no formulário herdarão essa definição. Para obter mais informações, consulte <xref:System.Windows.Forms.Control.ImeMode%2A> ) e <xref:System.Windows.Forms.ImeMode>.  
  
## <a name="see-also"></a>Consulte também

- [Globalizando aplicativos dos Windows Forms](globalizing-windows-forms.md)
