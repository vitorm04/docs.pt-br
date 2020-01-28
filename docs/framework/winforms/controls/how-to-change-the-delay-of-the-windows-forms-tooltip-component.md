---
title: Alterar o atraso do componente de dica de ferramenta
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
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746580"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Como alterar o atraso do componente ToolTip dos Windows Forms
Há vários valores de atraso que podem ser definidos para um componente Windows Forms <xref:System.Windows.Forms.ToolTip>. A unidade de medida para todas essas propriedades é milissegundos. A propriedade <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> determina por quanto tempo o usuário deve apontar para o controle associado para que a cadeia de dica de ferramenta apareça. A propriedade <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> define o número de milissegundos que leva para que as cadeias de caracteres de dica de ferramenta subsequentes sejam exibidas à medida que o mouse se move de um controle associado à dica de ferramenta para outro. A propriedade <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> determina o período de tempo em que a cadeia de dica de ferramenta é mostrada. Você pode definir esses valores individualmente ou definindo o valor da propriedade <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>; as outras propriedades de atraso são definidas com base no valor atribuído à propriedade <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>. Por exemplo, quando <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> é definido como um valor N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> é definido como N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> é definido como o valor de <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> dividido por cinco (ou N/5) e <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> é definido como um valor que é cinco vezes o valor da propriedade <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> (ou 5N).  
  
### <a name="to-set-the-delay"></a>Para definir o atraso  
  
1. Defina as seguintes propriedades conforme mostrado neste exemplo.  
  
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
  
## <a name="see-also"></a>Veja também

- [Visão geral do componente ToolTip](tooltip-component-overview-windows-forms.md)
- [Como definir ToolTips para controles em um Windows Form no tempo de design](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Componente ToolTip](tooltip-component-windows-forms.md)
