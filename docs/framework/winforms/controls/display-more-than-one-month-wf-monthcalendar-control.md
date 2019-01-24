---
title: 'Como: Exibir mais de um mês no controle MonthCalendar dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
ms.openlocfilehash: 164369ab1a94249470b57e546db64be8e17b99bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582022"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Como: Exibir mais de um mês no controle MonthCalendar dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.MonthCalendar> controle pode exibir até 12 meses por vez. Por padrão, o controle exibe apenas um mês, mas você pode especificar o número de meses é exibido e como eles são organizados dentro do controle. Quando você altera as dimensões de calendário, o controle é redimensionado, portanto, certifique-se que há espaço suficiente no formulário para as novas dimensões.  
  
### <a name="to-display-multiple-months"></a>Para exibir vários meses  
  
-   Defina o <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> propriedade para o número de meses a serem exibidas horizontal e verticalmente.  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>Consulte também
- [Controle MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [Como: Selecione um intervalo de datas no controle MonthCalendar dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Como: Alterar a aparência do controle do Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
