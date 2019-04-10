---
title: 'Como: Selecionar um intervalo de datas no controle MonthCalendar do Windows Forms'
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
ms.openlocfilehash: 82d0499cb40f79a3110b8432fbee66774bcc14a7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332229"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Como: Selecionar um intervalo de datas no controle MonthCalendar do Windows Forms
Um recurso importante dos formulários Windows <xref:System.Windows.Forms.MonthCalendar> controle é que o usuário pode selecionar um intervalo de datas. Esse recurso é um aprimoramento o recurso de seleção de data do <xref:System.Windows.Forms.DateTimePicker> controle, que permite apenas que o usuário selecione um valor único de data/hora. Você pode definir um intervalo de datas ou obter um intervalo de seleção definido pelo usuário usando as propriedades do <xref:System.Windows.Forms.MonthCalendar> controle. O exemplo de código a seguir demonstra como definir um intervalo de seleção.  
  
### <a name="to-select-a-range-of-dates"></a>Para selecionar um intervalo de datas  
  
1. Criar <xref:System.DateTime> objetos que representam a primeira e última data em um intervalo.  
  
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
  
     – ou –  
  
     Defina as <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> e <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> propriedades.  
  
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
- [Como: Alterar a aparência do controle MonthCalendar do Windows Forms](how-to-change-monthcalendar-control-appearance.md)
- [Como: Exibir dias específicos em negrito com o controle MonthCalendar do Windows Forms](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Como: Exibir mais de um mês no controle MonthCalendar do Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
