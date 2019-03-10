---
title: 'Como: Exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: c201455acaa9bde521afd623424d0cfc403b1bff
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705864"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Como: Exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.DateTimePicker> controle oferece flexibilidade na formatação da exibição de datas e horas no controle. O <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriedade permite que você selecione um dos formatos predefinidos, listados no <xref:System.Windows.Forms.DateTimePickerFormat>. Se nenhum deles for adequado para suas finalidades, você pode criar seu próprio estilo de formato usando caracteres de formato listados no <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Para exibir um formato personalizado  
  
1.  Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A> como `DateTimePickerFormat.Custom`.  
  
2.  Defina o <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> propriedade como uma cadeia de caracteres de formato.  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a>Para adicionar texto ao valor formatado  
  
1.  Use aspas simples para incluir qualquer caractere que não seja um caractere de formato como "M" ou um delimitador como ":". Por exemplo, a cadeia de formato a seguir exibe a data atual com o formato "hoje é: 05:30:31 março de sexta-feira 02, 2012" na cultura inglês (Estados Unidos).  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     Dependendo da configuração de cultura, todos os caracteres que não estiverem entre aspas simples poderão ser alterados. Por exemplo, a cadeia de caracteres de formato acima exibe a data atual com o formato "hoje é: 05:30:31 março de sexta-feira 02, 2012" na cultura inglês (Estados Unidos). Observe que a primeira vírgula é colocada entre aspas simples, porque não se pretende que ela seja um caractere delimitador como em "hh:mm:ss". Em outra cultura, o formato pode ser exibido como "hoje é: Março de 05.30.31 sexta-feira 02, 2012".  
  
## <a name="see-also"></a>Consulte também
- [Controle DateTimePicker](datetimepicker-control-windows-forms.md)
- [Como: Definidas e retornar datas com o controle DateTimePicker dos Windows Forms](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
