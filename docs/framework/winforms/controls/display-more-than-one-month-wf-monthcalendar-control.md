---
title: 'Como: Exibir mais de um mês no controle MonthCalendar do Windows Forms'
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
ms.openlocfilehash: 79100b52d8e0a5b651edb9d6555a4497287ed858
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209548"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="536bf-102">Como: Exibir mais de um mês no controle MonthCalendar do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="536bf-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="536bf-103">Os formulários do Windows <xref:System.Windows.Forms.MonthCalendar> controle pode exibir até 12 meses por vez.</span><span class="sxs-lookup"><span data-stu-id="536bf-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="536bf-104">Por padrão, o controle exibe apenas um mês, mas você pode especificar o número de meses é exibido e como eles são organizados dentro do controle.</span><span class="sxs-lookup"><span data-stu-id="536bf-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="536bf-105">Quando você altera as dimensões de calendário, o controle é redimensionado, portanto, certifique-se que há espaço suficiente no formulário para as novas dimensões.</span><span class="sxs-lookup"><span data-stu-id="536bf-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="536bf-106">Para exibir vários meses</span><span class="sxs-lookup"><span data-stu-id="536bf-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="536bf-107">Defina o <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> propriedade para o número de meses a serem exibidas horizontal e verticalmente.</span><span class="sxs-lookup"><span data-stu-id="536bf-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="536bf-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="536bf-108">See also</span></span>

- [<span data-ttu-id="536bf-109">Controle MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="536bf-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="536bf-110">Como: Selecione um intervalo de datas no controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="536bf-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="536bf-111">Como: Alterar a aparência do controle do Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="536bf-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
