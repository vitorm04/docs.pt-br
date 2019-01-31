---
title: 'Como: Alterar a aparência do controle do Windows Forms MonthCalendar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: b7f321c1557bc7ea19213f2fc67767fe56328cf4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258910"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Como: Alterar a aparência do controle do Windows Forms MonthCalendar
Os formulários do Windows <xref:System.Windows.Forms.MonthCalendar> controle permite que você personalize a aparência do calendário de várias maneiras. Por exemplo, você pode definir o esquema de cores e optar por exibir ou ocultar os números de semana e a data atual.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Alterar o esquema de cores do calendário do mês  
  
-   Definir propriedades como <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> e <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. O <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> propriedade também determina a cor da fonte para os dias da semana. O <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriedade determina a cor das datas que precedem e seguem o mês exibido ou meses.  
  
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
    >  Desde o Windows Vista e dependendo do tema, definir algumas propriedades pode não mudar a aparência do calendário. Por exemplo, se o Windows está configurado para usar o tema Aero, definir a <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, ou <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriedades não tem nenhum efeito. Isso ocorre porque uma versão atualizada do calendário é renderizada com uma aparência derivada no tempo de execução do tema atual do sistema operacional. Se quiser usar essas propriedades e habilitar a versão anterior do calendário, desabilite os estilos visuais para o aplicativo. Desabilitar os estilos visuais pode afetar a aparência e o comportamento de outros controles no seu aplicativo. Para desabilitar estilos visuais no Visual Basic, abra o Designer de projeto e desmarque a **estilos visuais do XP habilitar** caixa de seleção. Para desabilitar estilos visuais em C#, abra Program.cs e comente `Application.EnableVisualStyles();`. Para obter mais informações sobre estilos visuais, consulte [como: Habilitar estilos visuais do Windows XP](https://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).  
  
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
  
     (Visual c#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
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
- [Controle MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [Como: Selecione um intervalo de datas no controle MonthCalendar dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Como: Exibir dias específicos em negrito com o Windows Forms controle MonthCalendar](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Como: Exibir mais de um mês no controle MonthCalendar dos Windows Forms](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
