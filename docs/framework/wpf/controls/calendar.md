---
title: Calendário
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: 9a64c6cd6fc1cc53383f2617f7a7a78959e87c4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124774"
---
# <a name="calendar"></a>Calendário
Um calendário permite ao usuário selecionar uma data usando uma exibição visual do calendário.  
  
 Um <xref:System.Windows.Controls.Calendar> controle pode ser usado sozinho ou como parte da lista suspensa um <xref:System.Windows.Controls.DatePicker> controle. Para obter mais informações, consulte <xref:System.Windows.Controls.DatePicker>.  
  
 A ilustração a seguir mostra dois <xref:System.Windows.Controls.Calendar> controla, um com as seleções e datas de blecaute e outro sem.  
  
 ![Controles de calendário](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Controles de calendário  
  
 A tabela a seguir fornece informações sobre as tarefas que são normalmente associadas a <xref:System.Windows.Controls.Calendar>.  
  
|Tarefa|Implementação|  
|----------|--------------------|  
|Especifica as datas que não podem ser selecionadas.|Use a propriedade <xref:System.Windows.Controls.Calendar.BlackoutDates%2A>.|  
|Ter o <xref:System.Windows.Controls.Calendar> exibir um mês, um ano inteiro ou uma década.|Defina o <xref:System.Windows.Controls.Calendar.DisplayMode%2A> propriedade para o mês, ano ou década.|  
|Especifique se o usuário pode selecionar uma data, um intervalo de datas ou vários intervalos de datas.|Use o <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Especifique o intervalo de datas que o <xref:System.Windows.Controls.Calendar> exibe.|Use o <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> e <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> propriedades.|  
|Especificar se a data atual for realçada.|Use a propriedade <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A>. Por padrão, <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> é `true`.|  
|Alterar o tamanho do <xref:System.Windows.Controls.Calendar>.|Use uma <xref:System.Windows.Controls.Viewbox> ou defina o <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriedade para um <xref:System.Windows.Media.ScaleTransform>. Observe que, se você definir a <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades de um <xref:System.Windows.Controls.Calendar>, o Calendário real não altera seu tamanho.|  
  
 O <xref:System.Windows.Controls.Calendar> controle fornece navegação básica usando o mouse ou teclado. A tabela a seguir resume a navegação com o teclado.  
  
|Combinação de teclas|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Ação|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|TECLA DE DIREÇÃO|<xref:System.Windows.Controls.CalendarMode.Month>|As alterações a <xref:System.Windows.Controls.Calendar.SelectedDate%2A> propriedade se o <xref:System.Windows.Controls.Calendar.SelectionMode%2A> não está definida <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|TECLA DE DIREÇÃO|<xref:System.Windows.Controls.CalendarMode.Year>|Altera o mês do <xref:System.Windows.Controls.Calendar.DisplayDate%2A> propriedade. Observe que o <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|TECLA DE DIREÇÃO|<xref:System.Windows.Controls.CalendarMode.Decade>|Altera o ano do <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Observe que o <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|SHIFT + TECLA DE DIREÇÃO|<xref:System.Windows.Controls.CalendarMode.Month>|Se <xref:System.Windows.Controls.Calendar.SelectionMode%2A> não está definido como <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> ou <xref:System.Windows.Controls.CalendarSelectionMode.None>, estende o intervalo de datas selecionados.|  
|HOME|<xref:System.Windows.Controls.CalendarMode.Month>|As alterações a <xref:System.Windows.Controls.Calendar.SelectedDate%2A> ao primeiro dia do mês atual.|  
|HOME|<xref:System.Windows.Controls.CalendarMode.Year>|Altera o mês do <xref:System.Windows.Controls.Calendar.DisplayDate%2A> ao primeiro mês do ano. O <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|HOME|<xref:System.Windows.Controls.CalendarMode.Decade>|Altera o ano do <xref:System.Windows.Controls.Calendar.DisplayDate%2A> para o primeiro ano da década. O <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|As alterações a <xref:System.Windows.Controls.Calendar.SelectedDate%2A> até o último dia do mês atual.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Altera o mês do <xref:System.Windows.Controls.Calendar.DisplayDate%2A> para o último mês do ano. O <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Altera o ano do <xref:System.Windows.Controls.Calendar.DisplayDate%2A> para o último ano da década. O <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|CTRL+SETA PARA CIMA|Qualquer|Alterna para a próxima maior <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Se <xref:System.Windows.Controls.Calendar.DisplayMode%2A> já está <xref:System.Windows.Controls.CalendarMode.Decade>, nenhuma ação.|  
|CTRL + SETA PARA BAIXO|Qualquer|Alterna para o próximo menor <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Se <xref:System.Windows.Controls.Calendar.DisplayMode%2A> já está <xref:System.Windows.Controls.CalendarMode.Month>, nenhuma ação.|  
|BARRA DE ESPAÇOS ou ENTER|<xref:System.Windows.Controls.CalendarMode.Year> ou <xref:System.Windows.Controls.CalendarMode.Decade>|Comutadores <xref:System.Windows.Controls.Calendar.DisplayMode%2A> para o <xref:System.Windows.Controls.CalendarMode.Month> ou <xref:System.Windows.Controls.CalendarMode.Year> representado pelo item focalizado.|  
  
## <a name="see-also"></a>Consulte também

- [Controles](index.md)
- [Estilo e modelagem](styling-and-templating.md)
