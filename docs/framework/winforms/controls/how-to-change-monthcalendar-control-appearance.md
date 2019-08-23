---
title: 'Como: Alterar a aparência do controle MonthCalendar do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 5582624d881b2d8039bcd5e8ac45e548c7b38f57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929042"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Como: Alterar a aparência do controle MonthCalendar do Windows Forms
O controle <xref:System.Windows.Forms.MonthCalendar> Windows Forms permite que você personalize a aparência do calendário de várias maneiras. Por exemplo, você pode definir o esquema de cores e optar por exibir ou ocultar os números de semana e a data atual.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Alterar o esquema de cores do calendário do mês  
  
- Defina propriedades como <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> e <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. A <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Propriedade também determina a cor da fonte para os dias da semana. A <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriedade determina a cor das datas que precedem e seguem o mês ou os meses exibidos.  
  
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
    > Desde o Windows Vista e dependendo do tema, definir algumas propriedades pode não mudar a aparência do calendário. Por exemplo, se o Windows estiver configurado para usar o tema Aero, definir <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>propriedades <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>,, <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> ou não terá nenhum efeito. Isso ocorre porque uma versão atualizada do calendário é renderizada com uma aparência derivada no tempo de execução do tema atual do sistema operacional. Se quiser usar essas propriedades e habilitar a versão anterior do calendário, desabilite os estilos visuais para o aplicativo. Desabilitar os estilos visuais pode afetar a aparência e o comportamento de outros controles no seu aplicativo. Para desabilitar os estilos visuais no Visual Basic, abra o designer de projeto e desmarque a caixa de seleção **Habilitar estilos visuais do XP** . Para desabilitar estilos visuais em C#, abra Program.cs e comente `Application.EnableVisualStyles();`. Para obter mais informações sobre estilos visuais, consulte [habilitando estilos visuais](/windows/desktop/controls/cookbook-overview).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Exibir a data atual na parte inferior do controle  
  
- Defina a propriedade <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> como `true`. O exemplo abaixo alterna entre exibir e omitir a data atual ao clicar duas vezes no formulário.  
  
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
  
     (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Exibir números de semana  
  
- Defina a propriedade <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> como `true`. Você pode definir essa propriedade no código ou na janela Propriedades.  
  
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

- [Controle MonthCalendar](monthcalendar-control-windows-forms.md)
- [Como: Selecione um intervalo de datas no controle Windows Forms MonthCalendar](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Como: Exibir dias específicos em negrito com o controle de MonthCalendar Windows Forms](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Como: Exibir mais de um mês no controle de MonthCalendar Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
