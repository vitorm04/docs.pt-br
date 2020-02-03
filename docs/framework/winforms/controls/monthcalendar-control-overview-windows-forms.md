---
title: Visão geral do controle MonthCalendar
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: a9b56164339d03b380a564b21855f6d94ec06af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734934"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>Visão geral do controle MonthCalendar (Windows Forms)
O controle <xref:System.Windows.Forms.MonthCalendar> dos Windows Forms apresenta uma interface gráfica intuitiva para os usuários exibirem e definirem as informações de data. O controle exibe um calendário: uma grade que contém os dias numerados do mês, organizados em colunas abaixo dos dias da semana, com o intervalo selecionado de datas realçado. Você pode selecionar um outro mês clicando nos botões de seta em um dos lados da legenda do mês. Ao contrário do controle de <xref:System.Windows.Forms.DateTimePicker> semelhante, você pode selecionar mais de uma data com este controle. Para obter mais informações sobre o controle de <xref:System.Windows.Forms.DateTimePicker>, consulte o [controle DateTimePicker](datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>Configurar o controle MonthCalendar  
 A aparência do controle de <xref:System.Windows.Forms.MonthCalendar> é altamente configurável. Por padrão, a data do dia atual é exibida dentro de um círculo e também está disponível na parte inferior da grade. Você pode alterar esse recurso definindo as propriedades <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> e <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> como `false`. Você também pode adicionar números de semana ao calendário definindo a propriedade <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> como `true`. Ao definir a propriedade <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>, você pode ter vários meses exibidos horizontal e verticalmente. Por padrão, domingo é mostrado como o primeiro dia da semana, mas qualquer dia pode ser designado usando a propriedade <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>.  
  
 Você também pode definir determinadas datas para serem exibidas em negrito em uma base única, anual ou mensal, adicionando <xref:System.DateTime> objetos às propriedades <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>e <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>. Para obter mais informações, consulte [Como exibir dados específicos em negrito com o controle MonthCalendar dos Windows Forms](display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 A propriedade de chave do controle de <xref:System.Windows.Forms.MonthCalendar> é <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, o intervalo de datas selecionado no controle. O valor de <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> não pode exceder o número máximo de dias que podem ser selecionados, definido na propriedade <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>. As datas mais antigas e mais recentes que o usuário pode selecionar são determinadas pelas propriedades <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> e <xref:System.Windows.Forms.MonthCalendar.MinDate%2A>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MonthCalendar>
- [Controle MonthCalendar](monthcalendar-control-windows-forms.md)
