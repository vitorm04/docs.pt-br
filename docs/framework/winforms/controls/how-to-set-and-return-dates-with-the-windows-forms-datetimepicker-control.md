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
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Como: Definir e retornar datas com o controle DateTimePicker do Windows Forms
A data atualmente selecionada ou a hora em formulários do Windows <xref:System.Windows.Forms.DateTimePicker> controle é determinado pelo <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade. Você pode definir as <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade antes do controle é exibido (por exemplo, em tempo de design ou no formulário de <xref:System.Windows.Forms.Form.Load> eventos) para determinar qual data será inicialmente selecionada no controle. Por padrão, o controle <xref:System.Windows.Forms.DateTimePicker.Value%2A> é definido como a data atual. Se você alterar o controle <xref:System.Windows.Forms.DateTimePicker.Value%2A> no código, o controle será atualizado automaticamente no formulário para refletir a nova configuração.  
  
 O <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade retorna um <xref:System.DateTime> estrutura como seu valor. Há várias propriedades do <xref:System.DateTime> estrutura que retornam informações específicas sobre a data exibida. Essas propriedades só podem ser usadas para retornar um valor; não as utilize para definir um valor.  
  
-   Para obter valores de data, o <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, e <xref:System.DateTime.Year%2A> propriedades retornam valores inteiros para essas unidades de tempo da data selecionada. O <xref:System.DateTime.DayOfWeek%2A> propriedade retorna um valor que indica o dia da semana selecionado (os valores possíveis são listados no <xref:System.DayOfWeek> enumeração).  
  
-   Para obter valores de tempo, o <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, e <xref:System.DateTime.Millisecond%2A> propriedades retornam valores inteiros para essas unidades de tempo. Para configurar o controle para exibir horas, consulte [como: Exibir a hora com o controle DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Definir o valor de data e hora do controle  
  
-   Defina o <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade para um valor de data ou hora.  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>Retornar o valor de data e hora  
  
-   Chame o <xref:System.Windows.Forms.DateTimePicker.Text%2A> propriedade para retornar o valor inteiro como formatado no controle ou chame o método apropriado do <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade retornar uma parte do valor. Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> para converter as informações em uma cadeia de caracteres que pode ser exibida ao usuário.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Controle DateTimePicker](datetimepicker-control-windows-forms.md)
- [Como: Exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
