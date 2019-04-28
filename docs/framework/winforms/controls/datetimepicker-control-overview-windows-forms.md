---
title: Visão geral do controle DateTimePicker (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 451172b51427e4932470c53737c7bc276920271c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909162"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>Visão geral do controle DateTimePicker (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.DateTimePicker> controle permite que o usuário selecionar um único item em uma lista de datas ou horas. Quando usado para representar uma data, ele aparece em duas partes: uma lista suspensa com uma data representada em texto e uma grade exibida ao clicar na seta para baixo ao lado da lista. A grade é semelhante a <xref:System.Windows.Forms.MonthCalendar> controle, que pode ser usado para selecionar várias datas. Para obter mais informações sobre o <xref:System.Windows.Forms.MonthCalendar> de controle, consulte [visão geral do controle MonthCalendar](monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Propriedades da chave  
 Se desejar que o <xref:System.Windows.Forms.DateTimePicker> a ser exibido como um controle de seleção ou edição de vezes em vez de datas, defina a <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> propriedade a ser `true` e o <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriedade para <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Confira mais informações em [Como Exibir a hora com o controle DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
 Quando o <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> estiver definida como `true`, uma caixa de seleção é exibida ao lado da data selecionada no controle. Quando a caixa de seleção é marcada, é possível atualizar o valor de data e hora selecionado. Quando a caixa de seleção está vazia, o valor aparece indisponível.  
  
 O controle <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> e <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> propriedades determinam o intervalo de datas e horas. O <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriedade contém a data e hora atuais do controle é definido como. Para obter detalhes, confira [Como: Definir e retornar datas com o Windows Forms controle DateTimePicker](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Os valores podem ser exibidos em quatro formatos, que são definidos com o <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriedade: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>, ou <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Se um formato personalizado for selecionado, você deve definir o <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> propriedade como uma cadeia de caracteres apropriada. Para obter detalhes, confira [Como: Exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Consulte também

- [Como: Exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [Como: Definidas e retornar datas com o controle DateTimePicker dos Windows Forms](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
