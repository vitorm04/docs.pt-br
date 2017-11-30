---
title: "Como alterar a aparência do controle MonthCalendar do Windows Forms"
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
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 38cddb4222077c21d72828371a8fe025184c4f75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a><span data-ttu-id="3c9c1-102">Como alterar a aparência do controle MonthCalendar do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c9c1-102">How to: Change the Windows Forms MonthCalendar Control&#39;s Appearance</span></span>
<span data-ttu-id="3c9c1-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> controle permite que você personalize a aparência do calendário de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="3c9c1-104">Por exemplo, você pode definir o esquema de cores e optar por exibir ou ocultar os números de semana e a data atual.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="3c9c1-105">Alterar o esquema de cores do calendário do mês</span><span class="sxs-lookup"><span data-stu-id="3c9c1-105">To change the month calendar's color scheme</span></span>  
  
-   <span data-ttu-id="3c9c1-106">Definir propriedades, como <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> e <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="3c9c1-107">O <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> propriedade também determina a cor da fonte para os dias da semana.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="3c9c1-108">O <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriedade determina a cor das datas que precedem e seguem o mês exibido ou meses.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3c9c1-109">Desde o Windows Vista e dependendo do tema, definir algumas propriedades pode não mudar a aparência do calendário.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="3c9c1-110">Por exemplo, se o Windows é configurado para usar o tema Aero, definindo o <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, ou <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriedades não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="3c9c1-111">Isso ocorre porque uma versão atualizada do calendário é renderizada com uma aparência derivada no tempo de execução do tema atual do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="3c9c1-112">Se quiser usar essas propriedades e habilitar a versão anterior do calendário, desabilite os estilos visuais para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="3c9c1-113">Desabilitar os estilos visuais pode afetar a aparência e o comportamento de outros controles no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="3c9c1-114">Para desativar estilos visuais no Visual Basic, abra o Designer de projeto e desmarque o **estilos visuais XP habilitar** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="3c9c1-115">Para desabilitar estilos visuais em C#, abra Program.cs e comente `Application.EnableVisualStyles();`.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="3c9c1-116">Para obter mais informações sobre estilos visuais, consulte [Como habilitar os estilos visuais do Windows XP](http://msdn.microsoft.com/en-us/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).</span><span class="sxs-lookup"><span data-stu-id="3c9c1-116">For more information about visual styles, see [How to: Enable Windows XP Visual Styles](http://msdn.microsoft.com/en-us/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="3c9c1-117">Exibir a data atual na parte inferior do controle</span><span class="sxs-lookup"><span data-stu-id="3c9c1-117">To display the current date at the bottom of the control</span></span>  
  
-   <span data-ttu-id="3c9c1-118">Defina a propriedade <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="3c9c1-119">O exemplo abaixo alterna entre exibir e omitir a data atual ao clicar duas vezes no formulário.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     <span data-ttu-id="3c9c1-120">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-120">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="3c9c1-121">Exibir números de semana</span><span class="sxs-lookup"><span data-stu-id="3c9c1-121">To display week numbers</span></span>  
  
-   <span data-ttu-id="3c9c1-122">Defina a propriedade <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="3c9c1-123">Você pode definir essa propriedade no código ou na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="3c9c1-124">Números de semana são exibidos em uma coluna separada à esquerda do primeiro dia da semana.</span><span class="sxs-lookup"><span data-stu-id="3c9c1-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3c9c1-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c9c1-125">See Also</span></span>  
 [<span data-ttu-id="3c9c1-126">Controle MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="3c9c1-126">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="3c9c1-127">Como selecionar um intervalo de datas no controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c9c1-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="3c9c1-128">Como exibir dias específicos em negrito com o controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c9c1-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="3c9c1-129">Como exibir mais de um mês no controle MonthCalendar dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c9c1-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
