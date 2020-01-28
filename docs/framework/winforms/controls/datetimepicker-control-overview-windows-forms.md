---
title: Visão geral do controle DateTimePicker
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 63271dd91116c1f68d426f3ed5aa710644ded928
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746933"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>Visão geral do controle DateTimePicker (Windows Forms)
O controle de <xref:System.Windows.Forms.DateTimePicker> de Windows Forms permite que o usuário selecione um único item de uma lista de datas ou horas. Quando usado para representar uma data, ele aparece em duas partes: uma lista suspensa com uma data representada em texto e uma grade exibida ao clicar na seta para baixo ao lado da lista. A grade é semelhante ao controle de <xref:System.Windows.Forms.MonthCalendar>, que pode ser usado para selecionar várias datas. Para obter mais informações sobre o controle de <xref:System.Windows.Forms.MonthCalendar>, consulte [visão geral do controle MonthCalendar](monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Propriedades da chave  
 Se você quiser que a <xref:System.Windows.Forms.DateTimePicker> apareça como um controle para seleção ou edição de horas em vez de datas, defina a propriedade <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> como `true` e a propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A> como <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Para obter mais informações, consulte [Como exibir a hora com o controle DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
 Quando a propriedade <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> é definida como `true`, uma caixa de seleção é exibida ao lado da data selecionada no controle. Quando a caixa de seleção é marcada, é possível atualizar o valor de data e hora selecionado. Quando a caixa de seleção está vazia, o valor aparece indisponível.  
  
 As propriedades <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> e <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> do controle determinam o intervalo de datas e horas. A propriedade <xref:System.Windows.Forms.DateTimePicker.Value%2A> contém a data e a hora atuais em que o controle está definido. Para ver mais detalhes, consulte [Como definir e retornar datas com o controle DateTimePicker dos Windows Forms](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Os valores podem ser exibidos em quatro formatos, que são definidos pela propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A>: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>ou <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Se um formato personalizado for selecionado, você deverá definir a propriedade <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> como uma cadeia de caracteres apropriada. Para ver mais detalhes, consulte [Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Veja também

- [Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [Como definir e retornar datas com o controle DateTimePicker dos Windows Forms](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
