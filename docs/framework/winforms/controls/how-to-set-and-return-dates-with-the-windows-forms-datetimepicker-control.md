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
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Como definir e retornar datas com o controle DateTimePicker dos Windows Forms
A data ou a hora atualmente selecionada no controle de <xref:System.Windows.Forms.DateTimePicker> de Windows Forms é determinada pela propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A>. Você pode definir a propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A> antes que o controle seja exibido (por exemplo, em tempo de design ou no evento de <xref:System.Windows.Forms.Form.Load> do formulário) para determinar qual data será selecionada inicialmente no controle. Por padrão, o <xref:System.Windows.Forms.DateTimePicker.Value%2A> do controle é definido como a data atual. Se você alterar o <xref:System.Windows.Forms.DateTimePicker.Value%2A> do controle no código, o controle será atualizado automaticamente no formulário para refletir a nova configuração.  
  
 A propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A> retorna uma estrutura de <xref:System.DateTime> como seu valor. Há várias propriedades da estrutura de <xref:System.DateTime> que retornam informações específicas sobre a data de exibição. Essas propriedades só podem ser usadas para retornar um valor; não as utilize para definir um valor.  
  
- Para valores de data, as propriedades <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>e <xref:System.DateTime.Year%2A> retornam valores inteiros para essas unidades de tempo da data selecionada. A propriedade <xref:System.DateTime.DayOfWeek%2A> retorna um valor que indica o dia da semana Selecionado (os valores possíveis são listados na enumeração <xref:System.DayOfWeek>).  
  
- Para valores de tempo, as propriedades <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>e <xref:System.DateTime.Millisecond%2A> retornam valores inteiros para essas unidades de tempo. Para configurar o controle para exibir horas, consulte [Como exibir a hora com o controle DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Definir o valor de data e hora do controle  
  
- Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A> como um valor de data ou hora.  
  
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
  
- Chame a propriedade <xref:System.Windows.Forms.DateTimePicker.Text%2A> para retornar o valor inteiro, conforme formatado no controle, ou chame o método apropriado da propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A> para retornar uma parte do valor. Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> para converter as informações em uma cadeia de caracteres que pode ser exibida para o usuário.  
  
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
- [Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
