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
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="83d0a-102">Como exibir mais de um mês no controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83d0a-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="83d0a-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> controle pode exibir até 12 meses por vez.</span><span class="sxs-lookup"><span data-stu-id="83d0a-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="83d0a-104">Por padrão, o controle exibe somente um mês, mas você pode especificar o número de meses é exibido e como eles são organizados dentro do controle.</span><span class="sxs-lookup"><span data-stu-id="83d0a-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="83d0a-105">Quando você alterar as dimensões de calendário, o controle é redimensionado, portanto, se que há espaço suficiente no formulário para as novas dimensões.</span><span class="sxs-lookup"><span data-stu-id="83d0a-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="83d0a-106">Para exibir vários meses</span><span class="sxs-lookup"><span data-stu-id="83d0a-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="83d0a-107">Definir o <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> propriedade para o número de meses para exibir horizontalmente e verticalmente.</span><span class="sxs-lookup"><span data-stu-id="83d0a-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="83d0a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83d0a-108">See Also</span></span>  
 [<span data-ttu-id="83d0a-109">Controle MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="83d0a-109">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="83d0a-110">Como selecionar um intervalo de datas no controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83d0a-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="83d0a-111">Como alterar a aparência do controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83d0a-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
