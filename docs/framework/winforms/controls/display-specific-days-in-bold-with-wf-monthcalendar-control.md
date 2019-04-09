---
title: 'Como: Exibir dias específicos em negrito com o controle MonthCalendar do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
ms.openlocfilehash: cf3ec21aa0272f60599f5659d78214120bcfcaf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073689"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>Como: Exibir dias específicos em negrito com o controle MonthCalendar do Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.MonthCalendar> controle pode exibir dias em negrito, como datas únicas ou em uma base de repetição. Você pode fazer isso para chamar atenção para datas especiais, como feriados e fins de semana.  
  
 Três propriedades controlam esse recurso. O <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> propriedade contém datas únicas. O <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> propriedade contém as datas exibidas em negrito todo ano. O <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> propriedade contém as datas exibidas em negrito todo mês. Cada uma dessas propriedades contém uma matriz de <xref:System.DateTime> objetos. Para adicionar ou remover uma data de uma dessas listas, você deve adicionar ou remover um <xref:System.DateTime> objeto.  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>Para exibir uma data em negrito  
  
1.  Criar o <xref:System.DateTime> objetos.  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2.  Coloque uma única data em negrito chamando o <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, ou <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> método da <xref:System.Windows.Forms.MonthCalendar> controle.  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     – ou –  
  
     Tornar um conjunto de datas em negrito todas de uma vez criando uma matriz de <xref:System.DateTime> objetos e atribuindo-o a uma das propriedades.  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>Para exibir uma data na fonte normal  
  
1.  Para exibir uma data única em negrito na fonte normal chamando o <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, ou <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> método.  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     – ou –  
  
     Remova todas as datas em negrito de uma das três listas chamando o <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, ou <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> método.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  Atualize a aparência da fonte chamando o <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> método.  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Controle MonthCalendar](monthcalendar-control-windows-forms.md)
- [Como: Selecionar um intervalo de datas no controle MonthCalendar do Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Como: Alterar a aparência do controle MonthCalendar do Windows Forms](how-to-change-monthcalendar-control-appearance.md)
- [Como: Exibir mais de um mês no controle MonthCalendar do Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
