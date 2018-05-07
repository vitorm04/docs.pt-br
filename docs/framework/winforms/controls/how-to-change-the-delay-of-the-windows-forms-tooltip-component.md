---
title: Como alterar o atraso do componente ToolTip dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 20dcd941b142daa672312edb618a1c3e4597442d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Como alterar o atraso do componente ToolTip dos Windows Forms
Há vários valores de atraso que podem ser definidas para um Windows Forms <xref:System.Windows.Forms.ToolTip> componente. A unidade de medida para todas essas propriedades é milissegundos. O <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> propriedade determina quanto tempo o usuário deve apontar para o controle associado a cadeia de caracteres de dica de ferramenta apareça. O <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> propriedade define o número de milissegundos que leva para subsequentes cadeias de caracteres de dica de ferramenta sejam exibidas quando o mouse se move de um controle associado a dica de ferramenta para outra. O <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> propriedade determina o período de tempo que a cadeia de caracteres de dica de ferramenta é exibida. Você pode definir esses valores, individualmente ou definindo o valor da <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriedade; o atraso outro propriedades são definidas com base no valor atribuído ao <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriedade. Por exemplo, quando <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> é definido como um valor N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> é definido como N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> é definido como o valor de <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> dividido em cinco (ou N/5), e <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> é definido como um valor que é cinco vezes o valor da <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriedade (ou 5N).  
  
### <a name="to-set-the-delay"></a>Para definir o atraso  
  
1.  Defina as seguintes propriedades conforme mostrado neste exemplo.  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Como definir ToolTips para controles em um Windows Form no tempo de design](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [Componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
