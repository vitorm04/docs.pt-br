---
title: Visão geral do controle MonthCalendar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: 7ed917afe2640fe2ffef4904a3795c5f0e84ded9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="monthcalendar-control-overview-windows-forms"></a>Visão geral do controle MonthCalendar (Windows Forms)
O controle <xref:System.Windows.Forms.MonthCalendar> dos Windows Forms apresenta uma interface gráfica intuitiva para os usuários exibirem e definirem as informações de data. O controle exibe um calendário: uma grade que contém os dias numerados do mês, organizados em colunas abaixo dos dias da semana, com o intervalo selecionado de datas realçado. Você pode selecionar um outro mês clicando nos botões de seta em um dos lados da legenda do mês. Ao contrário de semelhante <xref:System.Windows.Forms.DateTimePicker> controle, você pode selecionar mais de uma data com esse controle. Para obter mais informações sobre o <xref:System.Windows.Forms.DateTimePicker> , consulte [controle DateTimePicker](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>Configurar o controle MonthCalendar  
 O <xref:System.Windows.Forms.MonthCalendar> aparência do controle é altamente configurável. Por padrão, a data do dia atual é exibida dentro de um círculo e também está disponível na parte inferior da grade. Você pode alterar esse recurso definindo a <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> e <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> propriedades `false`. Você também pode adicionar números de semana do calendário, definindo o <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> propriedade `true`. Definindo o <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> propriedade, você pode ter vários meses exibidos horizontalmente e verticalmente. Por padrão, o domingo é mostrado como o primeiro dia da semana, mas qualquer dia pode ser designado usando o <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> propriedade.  
  
 Você também pode definir certas datas a ser exibido em negrito em uma base única, por ano ou mensal, adicionando <xref:System.DateTime> objetos para o <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>, e <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> propriedades. Para obter mais informações, consulte [Como exibir dados específicos em negrito com o controle MonthCalendar dos Windows Forms](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 A propriedade de chave de <xref:System.Windows.Forms.MonthCalendar> controle é <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, o intervalo de datas selecionado no controle. O <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> valor não pode exceder o número máximo de dias que podem ser selecionadas, definido <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> propriedade. As datas mais antigas e mais recentes, o usuário pode selecionar são determinadas pelo <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> e <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> propriedades.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MonthCalendar>  
 [Controle MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
