---
title: Como alterar a aparência do controle MonthCalendar do Windows Forms
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d2a3f12368d5215f7fe7611aa2f06e6b0fb1192
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a>Como alterar a aparência do controle MonthCalendar do Windows Forms
Windows Forms <xref:System.Windows.Forms.MonthCalendar> controle permite que você personalize a aparência do calendário de várias maneiras. Por exemplo, você pode definir o esquema de cores e optar por exibir ou ocultar os números de semana e a data atual.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Alterar o esquema de cores do calendário do mês  
  
-   Definir propriedades, como <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> e <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. O <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> propriedade também determina a cor da fonte para os dias da semana. O <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriedade determina a cor das datas que precedem e seguem o mês exibido ou meses.  
  
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
    >  Desde o Windows Vista e dependendo do tema, definir algumas propriedades pode não mudar a aparência do calendário. Por exemplo, se o Windows é configurado para usar o tema Aero, definindo o <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, ou <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriedades não tem nenhum efeito. Isso ocorre porque uma versão atualizada do calendário é renderizada com uma aparência derivada no tempo de execução do tema atual do sistema operacional. Se quiser usar essas propriedades e habilitar a versão anterior do calendário, desabilite os estilos visuais para o aplicativo. Desabilitar os estilos visuais pode afetar a aparência e o comportamento de outros controles no seu aplicativo. Para desativar estilos visuais no Visual Basic, abra o Designer de projeto e desmarque o **estilos visuais XP habilitar** caixa de seleção. Para desabilitar estilos visuais em C#, abra Program.cs e comente `Application.EnableVisualStyles();`. Para obter mais informações sobre estilos visuais, consulte [Como habilitar os estilos visuais do Windows XP](http://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Exibir a data atual na parte inferior do controle  
  
-   Defina a propriedade <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> como `true`. O exemplo abaixo alterna entre exibir e omitir a data atual ao clicar duas vezes no formulário.  
  
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
  
     (Visual c# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Exibir números de semana  
  
-   Defina a propriedade <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> como `true`. Você pode definir essa propriedade no código ou na janela Propriedades.  
  
     Números de semana são exibidos em uma coluna separada à esquerda do primeiro dia da semana.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Controle MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Como selecionar um intervalo de datas no controle MonthCalendar dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Como exibir dias específicos em negrito com o controle MonthCalendar dos Windows Forms](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [Como exibir mais de um mês no controle MonthCalendar dos Windows Forms](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
