---
title: Visão geral do controle DateTimePicker (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: cf44cdff7da06a27921ce5881199a3a88b1096f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528330"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>Visão geral do controle DateTimePicker (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DateTimePicker> controle permite que o usuário selecione um único item em uma lista de datas ou horas. Quando usado para representar uma data, ele aparece em duas partes: uma lista suspensa com uma data representada em texto e uma grade exibida ao clicar na seta para baixo ao lado da lista. A grade é semelhante a <xref:System.Windows.Forms.MonthCalendar> controle, que pode ser usado para selecionar várias datas. Para obter mais informações sobre o <xref:System.Windows.Forms.MonthCalendar> , consulte [visão geral do controle MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Propriedades da chave  
 Se desejar o <xref:System.Windows.Forms.DateTimePicker> a ser exibido como um controle para separação ou editando tempos, em vez de datas, defina o <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> propriedade `true` e o <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriedade <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Para obter mais informações, consulte [Como exibir a hora com o controle DateTimePicker](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).  
  
 Quando o <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> está definida como `true`, é exibida uma caixa de seleção ao lado da data selecionada no controle. Quando a caixa de seleção é marcada, é possível atualizar o valor de data e hora selecionado. Quando a caixa de seleção está vazia, o valor aparece indisponível.  
  
 O controle <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> e <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> propriedades determinam o intervalo de datas e horas. O <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade contém a data e hora atual do controle é definido como. Para ver mais detalhes, consulte [Como definir e retornar datas com o controle DateTimePicker dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Os valores podem ser exibidos em quatro formatos, que são definidos pelo <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriedade: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>, ou <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Se um formato personalizado for selecionado, você deve definir o <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> propriedade como uma cadeia de caracteres apropriada. Para ver mais detalhes, consulte [Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)  
 [Como definir e retornar datas com o controle DateTimePicker dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
