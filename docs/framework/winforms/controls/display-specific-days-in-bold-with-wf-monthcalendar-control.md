---
title: "Como exibir dados específicos em negrito com o controle MonthCalendar dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18a199592a8bfbef2e4a15b056e37af6d885f5f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="3bd74-102">Como exibir dados específicos em negrito com o controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3bd74-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="3bd74-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> controle pode exibir dias em negrito, como datas singulares ou em uma base de repetição.</span><span class="sxs-lookup"><span data-stu-id="3bd74-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="3bd74-104">Você pode fazer isso para chamar atenção para datas especiais, como feriados e fins de semana.</span><span class="sxs-lookup"><span data-stu-id="3bd74-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="3bd74-105">Três propriedades controlam esse recurso.</span><span class="sxs-lookup"><span data-stu-id="3bd74-105">Three properties control this feature.</span></span> <span data-ttu-id="3bd74-106">O <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> propriedade contém datas único.</span><span class="sxs-lookup"><span data-stu-id="3bd74-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="3bd74-107">O <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> propriedade contém datas aparecem em negrito todo ano.</span><span class="sxs-lookup"><span data-stu-id="3bd74-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="3bd74-108">O <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> propriedade contém datas aparecem em negrito em cada mês.</span><span class="sxs-lookup"><span data-stu-id="3bd74-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="3bd74-109">Cada uma dessas propriedades contém uma matriz de <xref:System.DateTime> objetos.</span><span class="sxs-lookup"><span data-stu-id="3bd74-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="3bd74-110">Para adicionar ou remover uma data de uma dessas listas, adicionar ou remover um <xref:System.DateTime> objeto.</span><span class="sxs-lookup"><span data-stu-id="3bd74-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="3bd74-111">Para exibir uma data em negrito</span><span class="sxs-lookup"><span data-stu-id="3bd74-111">To make a date appear in bold type</span></span>  
  
1.  <span data-ttu-id="3bd74-112">Criar o <xref:System.DateTime> objetos.</span><span class="sxs-lookup"><span data-stu-id="3bd74-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2.  <span data-ttu-id="3bd74-113">Colocar uma única data em negrito chamando o <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, ou <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> método o <xref:System.Windows.Forms.MonthCalendar> controle.</span><span class="sxs-lookup"><span data-stu-id="3bd74-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="3bd74-114">– ou –</span><span class="sxs-lookup"><span data-stu-id="3bd74-114">–or–</span></span>  
  
     <span data-ttu-id="3bd74-115">Tornar um conjunto de datas em negrito todos de uma vez criando uma matriz de <xref:System.DateTime> objetos e atribuí-la a uma das propriedades.</span><span class="sxs-lookup"><span data-stu-id="3bd74-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="3bd74-116">Para exibir uma data na fonte normal</span><span class="sxs-lookup"><span data-stu-id="3bd74-116">To make a date appear in the regular font</span></span>  
  
1.  <span data-ttu-id="3bd74-117">Para exibir uma data em negrito único na fonte normal chamando o <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, ou <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3bd74-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="3bd74-118">– ou –</span><span class="sxs-lookup"><span data-stu-id="3bd74-118">–or–</span></span>  
  
     <span data-ttu-id="3bd74-119">Remova todas as datas em negrito de uma das três listas chamando o <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, ou <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3bd74-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <span data-ttu-id="3bd74-120">Atualizar a aparência da fonte, chamando o <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3bd74-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3bd74-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bd74-121">See Also</span></span>  
 [<span data-ttu-id="3bd74-122">Controle MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="3bd74-122">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="3bd74-123">Como selecionar um intervalo de datas no controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3bd74-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="3bd74-124">Como alterar a aparência do controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3bd74-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="3bd74-125">Como exibir mais de um mês no controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3bd74-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
