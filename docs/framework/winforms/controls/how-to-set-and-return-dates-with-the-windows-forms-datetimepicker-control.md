---
title: 'Como: Definir e retornar datas com o controle DateTimePicker do Windows Forms'
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
ms.openlocfilehash: cc4f0bdf7355cda61e6cb95f5e0b18c4f83aa62b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081535"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="25a3c-102">Como: Definir e retornar datas com o controle DateTimePicker do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25a3c-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="25a3c-103">A data atualmente selecionada ou a hora em formulários do Windows <xref:System.Windows.Forms.DateTimePicker> controle é determinado pelo <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="25a3c-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="25a3c-104">Você pode definir as <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade antes do controle é exibido (por exemplo, em tempo de design ou no formulário de <xref:System.Windows.Forms.Form.Load> eventos) para determinar qual data será inicialmente selecionada no controle.</span><span class="sxs-lookup"><span data-stu-id="25a3c-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="25a3c-105">Por padrão, o controle <xref:System.Windows.Forms.DateTimePicker.Value%2A> é definido como a data atual.</span><span class="sxs-lookup"><span data-stu-id="25a3c-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="25a3c-106">Se você alterar o controle <xref:System.Windows.Forms.DateTimePicker.Value%2A> no código, o controle será atualizado automaticamente no formulário para refletir a nova configuração.</span><span class="sxs-lookup"><span data-stu-id="25a3c-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="25a3c-107">O <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade retorna um <xref:System.DateTime> estrutura como seu valor.</span><span class="sxs-lookup"><span data-stu-id="25a3c-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="25a3c-108">Há várias propriedades do <xref:System.DateTime> estrutura que retornam informações específicas sobre a data exibida.</span><span class="sxs-lookup"><span data-stu-id="25a3c-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="25a3c-109">Essas propriedades só podem ser usadas para retornar um valor; não as utilize para definir um valor.</span><span class="sxs-lookup"><span data-stu-id="25a3c-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
-   <span data-ttu-id="25a3c-110">Para obter valores de data, o <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, e <xref:System.DateTime.Year%2A> propriedades retornam valores inteiros para essas unidades de tempo da data selecionada.</span><span class="sxs-lookup"><span data-stu-id="25a3c-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="25a3c-111">O <xref:System.DateTime.DayOfWeek%2A> propriedade retorna um valor que indica o dia da semana selecionado (os valores possíveis são listados no <xref:System.DayOfWeek> enumeração).</span><span class="sxs-lookup"><span data-stu-id="25a3c-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
-   <span data-ttu-id="25a3c-112">Para obter valores de tempo, o <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, e <xref:System.DateTime.Millisecond%2A> propriedades retornam valores inteiros para essas unidades de tempo.</span><span class="sxs-lookup"><span data-stu-id="25a3c-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="25a3c-113">Para configurar o controle para exibir horas, consulte [como: Exibir a hora com o controle DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="25a3c-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="25a3c-114">Definir o valor de data e hora do controle</span><span class="sxs-lookup"><span data-stu-id="25a3c-114">To set the date and time value of the control</span></span>  
  
-   <span data-ttu-id="25a3c-115">Defina o <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade para um valor de data ou hora.</span><span class="sxs-lookup"><span data-stu-id="25a3c-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="25a3c-116">Retornar o valor de data e hora</span><span class="sxs-lookup"><span data-stu-id="25a3c-116">To return the date and time value</span></span>  
  
-   <span data-ttu-id="25a3c-117">Chame o <xref:System.Windows.Forms.DateTimePicker.Text%2A> propriedade para retornar o valor inteiro como formatado no controle ou chame o método apropriado do <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade retornar uma parte do valor.</span><span class="sxs-lookup"><span data-stu-id="25a3c-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="25a3c-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> para converter as informações em uma cadeia de caracteres que pode ser exibida ao usuário.</span><span class="sxs-lookup"><span data-stu-id="25a3c-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25a3c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25a3c-119">See also</span></span>

- [<span data-ttu-id="25a3c-120">Controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="25a3c-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="25a3c-121">Como: Exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25a3c-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
