---
title: Definir e retornar datas com o controle DateTimePicker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
ms.openlocfilehash: 1e0aa58e98748ccde9411f0f4871adbae3a5f14d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747107"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="d895c-102">Como definir e retornar datas com o controle DateTimePicker dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d895c-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="d895c-103">A data ou a hora atualmente selecionada no controle de <xref:System.Windows.Forms.DateTimePicker> de Windows Forms é determinada pela propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="d895c-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="d895c-104">Você pode definir a propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A> antes que o controle seja exibido (por exemplo, em tempo de design ou no evento de <xref:System.Windows.Forms.Form.Load> do formulário) para determinar qual data será selecionada inicialmente no controle.</span><span class="sxs-lookup"><span data-stu-id="d895c-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="d895c-105">Por padrão, o <xref:System.Windows.Forms.DateTimePicker.Value%2A> do controle é definido como a data atual.</span><span class="sxs-lookup"><span data-stu-id="d895c-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="d895c-106">Se você alterar o <xref:System.Windows.Forms.DateTimePicker.Value%2A> do controle no código, o controle será atualizado automaticamente no formulário para refletir a nova configuração.</span><span class="sxs-lookup"><span data-stu-id="d895c-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="d895c-107">A propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A> retorna uma estrutura de <xref:System.DateTime> como seu valor.</span><span class="sxs-lookup"><span data-stu-id="d895c-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="d895c-108">Há várias propriedades da estrutura de <xref:System.DateTime> que retornam informações específicas sobre a data de exibição.</span><span class="sxs-lookup"><span data-stu-id="d895c-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="d895c-109">Essas propriedades só podem ser usadas para retornar um valor; não as utilize para definir um valor.</span><span class="sxs-lookup"><span data-stu-id="d895c-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
- <span data-ttu-id="d895c-110">Para valores de data, as propriedades <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>e <xref:System.DateTime.Year%2A> retornam valores inteiros para essas unidades de tempo da data selecionada.</span><span class="sxs-lookup"><span data-stu-id="d895c-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="d895c-111">A propriedade <xref:System.DateTime.DayOfWeek%2A> retorna um valor que indica o dia da semana Selecionado (os valores possíveis são listados na enumeração <xref:System.DayOfWeek>).</span><span class="sxs-lookup"><span data-stu-id="d895c-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
- <span data-ttu-id="d895c-112">Para valores de tempo, as propriedades <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>e <xref:System.DateTime.Millisecond%2A> retornam valores inteiros para essas unidades de tempo.</span><span class="sxs-lookup"><span data-stu-id="d895c-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="d895c-113">Para configurar o controle para exibir horas, consulte [Como exibir a hora com o controle DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="d895c-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="d895c-114">Definir o valor de data e hora do controle</span><span class="sxs-lookup"><span data-stu-id="d895c-114">To set the date and time value of the control</span></span>  
  
- <span data-ttu-id="d895c-115">Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A> como um valor de data ou hora.</span><span class="sxs-lookup"><span data-stu-id="d895c-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="d895c-116">Retornar o valor de data e hora</span><span class="sxs-lookup"><span data-stu-id="d895c-116">To return the date and time value</span></span>  
  
- <span data-ttu-id="d895c-117">Chame a propriedade <xref:System.Windows.Forms.DateTimePicker.Text%2A> para retornar o valor inteiro, conforme formatado no controle, ou chame o método apropriado da propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A> para retornar uma parte do valor.</span><span class="sxs-lookup"><span data-stu-id="d895c-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="d895c-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> para converter as informações em uma cadeia de caracteres que pode ser exibida para o usuário.</span><span class="sxs-lookup"><span data-stu-id="d895c-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
    ```vb  
    MessageBox.Show("The selected value is ", DateTimePicker1.Text)  
    MessageBox.Show("The day of the week is ",   
       DateTimePicker1.Value.DayOfWeek.ToString)  
    MessageBox.Show("Millisecond is: ",   
       DateTimePicker1.Value.Millisecond.ToString)  
    ```  
  
    ```csharp  
    MessageBox.Show ("The selected value is " +   
       dateTimePicker1.Text);  
    MessageBox.Show ("The day of the week is " +   
       dateTimePicker1.Value.DayOfWeek.ToString());  
    MessageBox.Show("Millisecond is: " +   
       dateTimePicker1.Value.Millisecond.ToString());  
    ```  
  
    ```cpp  
    MessageBox::Show (String::Concat("The selected value is ",  
       dateTimePicker1->Text));  
    MessageBox::Show (String::Concat("The day of the week is ",  
       dateTimePicker1->Value.DayOfWeek.ToString()));  
    MessageBox::Show(String::Concat("Millisecond is: ",  
       dateTimePicker1->Value.Millisecond.ToString()));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d895c-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="d895c-119">See also</span></span>

- [<span data-ttu-id="d895c-120">Controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="d895c-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="d895c-121">Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d895c-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
