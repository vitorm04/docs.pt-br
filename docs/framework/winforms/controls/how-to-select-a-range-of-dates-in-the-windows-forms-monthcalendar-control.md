---
title: Selecionar um intervalo de datas no controle MonthCalendar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
ms.openlocfilehash: bda96af21a8f86a54d5c0fe0204546b980076d26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732903"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Como selecionar um intervalo de datas no controle MonthCalendar dos Windows Forms
Um recurso importante do controle de <xref:System.Windows.Forms.MonthCalendar> de Windows Forms é que o usuário pode selecionar um intervalo de datas. Esse recurso é um aprimoramento do recurso de seleção de data do controle de <xref:System.Windows.Forms.DateTimePicker>, que permite que o usuário selecione um único valor de data/hora. Você pode definir um intervalo de datas ou obter um intervalo de seleção definido pelo usuário usando as propriedades do controle de <xref:System.Windows.Forms.MonthCalendar>. O exemplo de código a seguir demonstra como definir um intervalo de seleção.  
  
### <a name="to-select-a-range-of-dates"></a>Para selecionar um intervalo de datas  
  
1. Crie <xref:System.DateTime> objetos que representam a primeira e a última datas em um intervalo.  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2. Definir a propriedade <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>.  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     –ou–  
  
     Definir as propriedades <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> e <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A>.  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Controle MonthCalendar](monthcalendar-control-windows-forms.md)
- [Como alterar a aparência do controle MonthCalendar dos Windows Forms](how-to-change-monthcalendar-control-appearance.md)
- [Como exibir dias específicos em negrito com o controle MonthCalendar dos Windows Forms](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Como exibir mais de um mês no controle MonthCalendar do Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
