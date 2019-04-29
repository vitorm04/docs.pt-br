---
title: 'Como: Alterar o atraso do componente ToolTip do Windows Forms'
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
ms.openlocfilehash: cf257cccd272c16c3d7c3d403456265444fc8ac8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781232"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Como: Alterar o atraso do componente ToolTip do Windows Forms
Há vários valores de atraso que podem ser definidas para um Windows Forms <xref:System.Windows.Forms.ToolTip> componente. A unidade de medida para todas essas propriedades é milissegundos. O <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> propriedade determina quanto tempo o usuário deve apontar para o controle associado para a cadeia de caracteres de dica de ferramenta apareça. O <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> propriedade define o número de milissegundos que leva para cadeias de caracteres de dica de ferramenta subsequentes sejam exibidas quando o mouse se move de um controle associado a dica de ferramenta para outra. O <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> propriedade determina o período de tempo que a cadeia de caracteres de dica de ferramenta é mostrada. Você pode definir esses valores individualmente ou definindo o valor da <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriedade; o outro atraso são definidas com base no valor atribuído para o <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriedade. Por exemplo, quando <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> é definido como um valor de N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> é definido como N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> é definido como o valor de <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> dividido por cinco (ou N/5), e <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> é definido como um valor que é cinco vezes o valor da <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriedade (ou 5N).  
  
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
  
## <a name="see-also"></a>Consulte também

- [Visão geral do componente ToolTip](tooltip-component-overview-windows-forms.md)
- [Como: Definir ToolTips para controles em um Windows Form no tempo de Design](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Componente ToolTip](tooltip-component-windows-forms.md)
