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
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="c7e8a-102">Como exibir mais de um mês no controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7e8a-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="c7e8a-103">O controle de <xref:System.Windows.Forms.MonthCalendar> de Windows Forms pode exibir até 12 meses por vez.</span><span class="sxs-lookup"><span data-stu-id="c7e8a-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="c7e8a-104">Por padrão, o controle exibe apenas um mês, mas você pode especificar quantos meses são exibidos e como eles são organizados dentro do controle.</span><span class="sxs-lookup"><span data-stu-id="c7e8a-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="c7e8a-105">Quando você altera as dimensões de calendário, o controle é redimensionado, portanto, certifique-se de que haja espaço suficiente no formulário para as novas dimensões.</span><span class="sxs-lookup"><span data-stu-id="c7e8a-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="c7e8a-106">Para exibir vários meses</span><span class="sxs-lookup"><span data-stu-id="c7e8a-106">To display multiple months</span></span>  
  
- <span data-ttu-id="c7e8a-107">Defina a propriedade <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> como o número de meses a serem exibidos horizontal e verticalmente.</span><span class="sxs-lookup"><span data-stu-id="c7e8a-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c7e8a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7e8a-108">See also</span></span>

- [<span data-ttu-id="c7e8a-109">Controle MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="c7e8a-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="c7e8a-110">Como selecionar um intervalo de datas no controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7e8a-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="c7e8a-111">Como alterar a aparência do controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7e8a-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
