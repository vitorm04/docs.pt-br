---
title: Exibir mais de um mês no controle MonthCalendar
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
ms.openlocfilehash: 5d3925bc19ddcd67742f0ab8b5b2e45530820f38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745892"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Como exibir mais de um mês no controle MonthCalendar dos Windows Forms
O controle de <xref:System.Windows.Forms.MonthCalendar> de Windows Forms pode exibir até 12 meses por vez. Por padrão, o controle exibe apenas um mês, mas você pode especificar quantos meses são exibidos e como eles são organizados dentro do controle. Quando você altera as dimensões de calendário, o controle é redimensionado, portanto, certifique-se de que haja espaço suficiente no formulário para as novas dimensões.  
  
### <a name="to-display-multiple-months"></a>Para exibir vários meses  
  
- Defina a propriedade <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> como o número de meses a serem exibidos horizontal e verticalmente.  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>Veja também

- [Controle MonthCalendar](monthcalendar-control-windows-forms.md)
- [Como selecionar um intervalo de datas no controle MonthCalendar dos Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Como alterar a aparência do controle MonthCalendar dos Windows Forms](how-to-change-monthcalendar-control-appearance.md)
