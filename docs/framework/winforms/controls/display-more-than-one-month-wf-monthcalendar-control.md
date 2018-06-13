---
title: Como exibir mais de um mês no controle MonthCalendar dos Windows Forms
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
ms.openlocfilehash: a71f85af2d51faf37160aba7fa89a8421b4523d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524867"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Como exibir mais de um mês no controle MonthCalendar dos Windows Forms
Windows Forms <xref:System.Windows.Forms.MonthCalendar> controle pode exibir até 12 meses por vez. Por padrão, o controle exibe somente um mês, mas você pode especificar o número de meses é exibido e como eles são organizados dentro do controle. Quando você alterar as dimensões de calendário, o controle é redimensionado, portanto, se que há espaço suficiente no formulário para as novas dimensões.  
  
### <a name="to-display-multiple-months"></a>Para exibir vários meses  
  
-   Definir o <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> propriedade para o número de meses para exibir horizontalmente e verticalmente.  
  
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
 [Controle MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Como selecionar um intervalo de datas no controle MonthCalendar dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Como alterar a aparência do controle MonthCalendar dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
