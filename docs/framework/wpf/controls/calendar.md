---
title: Calendário
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: e99a716e7ca8f7b2c9ed11543f37e0b8cb7422a6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460815"
---
# <a name="calendar"></a>Calendário
Um calendário permite ao usuário selecionar uma data usando uma exibição visual do calendário.  
  
 Um controle de <xref:System.Windows.Controls.Calendar> pode ser usado por conta própria ou como uma parte suspensa de um controle de <xref:System.Windows.Controls.DatePicker>. Para obter mais informações, consulte <xref:System.Windows.Controls.DatePicker>.  
  
 A ilustração a seguir mostra dois controles <xref:System.Windows.Controls.Calendar>, um com seleções e datas de blecaute e outro sem.  
  
 ![Controles de calendário](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Controles de calendário  
  
 A tabela a seguir fornece informações sobre as tarefas que normalmente são associadas ao <xref:System.Windows.Controls.Calendar>.  
  
|Tarefa|Implementação|  
|----------|--------------------|  
|Especifica as datas que não podem ser selecionadas.|Use a propriedade <xref:System.Windows.Controls.Calendar.BlackoutDates%2A>.|  
|O <xref:System.Windows.Controls.Calendar> exibir um mês, um ano inteiro ou uma década.|Defina a propriedade <xref:System.Windows.Controls.Calendar.DisplayMode%2A> como mês, ano ou década.|  
|Especifique se o usuário pode selecionar uma data, um intervalo de datas ou vários intervalos de datas.|Use o <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Especifique o intervalo de datas que o <xref:System.Windows.Controls.Calendar> exibe.|Use as propriedades <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> e <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A>.|  
|Especificar se a data atual for realçada.|Use a propriedade <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A>. Por padrão, <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> é `true`.|  
|Altere o tamanho do <xref:System.Windows.Controls.Calendar>.|Use uma <xref:System.Windows.Controls.Viewbox> ou defina a propriedade <xref:System.Windows.FrameworkElement.LayoutTransform%2A> como uma <xref:System.Windows.Media.ScaleTransform>. Observe que, se você definir as propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> de um <xref:System.Windows.Controls.Calendar>, o calendário real não alterará seu tamanho.|  
  
 O controle de <xref:System.Windows.Controls.Calendar> fornece navegação básica usando o mouse ou o teclado. A tabela a seguir resume a navegação com o teclado.  
  
|Combinação de teclas|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Ação|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|TECLA DE DIREÇÃO|<xref:System.Windows.Controls.CalendarMode.Month>|Altera a propriedade <xref:System.Windows.Controls.Calendar.SelectedDate%2A> se a propriedade <xref:System.Windows.Controls.Calendar.SelectionMode%2A> não estiver definida como <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|TECLA DE DIREÇÃO|<xref:System.Windows.Controls.CalendarMode.Year>|Altera o mês da propriedade <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Observe que o <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|TECLA DE DIREÇÃO|<xref:System.Windows.Controls.CalendarMode.Decade>|Altera o ano da <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Observe que o <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|SHIFT + TECLA DE DIREÇÃO|<xref:System.Windows.Controls.CalendarMode.Month>|Se <xref:System.Windows.Controls.Calendar.SelectionMode%2A> não estiver definido como <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> ou <xref:System.Windows.Controls.CalendarSelectionMode.None>, estenderá o intervalo de datas selecionadas.|  
|HOME|<xref:System.Windows.Controls.CalendarMode.Month>|Altera o <xref:System.Windows.Controls.Calendar.SelectedDate%2A> para o primeiro dia do mês atual.|  
|HOME|<xref:System.Windows.Controls.CalendarMode.Year>|Altera o mês do <xref:System.Windows.Controls.Calendar.DisplayDate%2A> para o primeiro mês do ano. O <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|HOME|<xref:System.Windows.Controls.CalendarMode.Decade>|Altera o ano do <xref:System.Windows.Controls.Calendar.DisplayDate%2A> para o primeiro ano da década. O <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|Altera o <xref:System.Windows.Controls.Calendar.SelectedDate%2A> para o último dia do mês atual.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Altera o mês do <xref:System.Windows.Controls.Calendar.DisplayDate%2A> para o último mês do ano. O <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Altera o ano do <xref:System.Windows.Controls.Calendar.DisplayDate%2A> para o último ano da década. O <xref:System.Windows.Controls.Calendar.SelectedDate%2A> não é alterado.|  
|CTRL+SETA PARA CIMA|Qualquer|Alterna para o próximo <xref:System.Windows.Controls.Calendar.DisplayMode%2A>maior. Se <xref:System.Windows.Controls.Calendar.DisplayMode%2A> já estiver <xref:System.Windows.Controls.CalendarMode.Decade>, nenhuma ação.|  
|CTRL + SETA PARA BAIXO|Qualquer|Alterna para o próximo <xref:System.Windows.Controls.Calendar.DisplayMode%2A>menor. Se <xref:System.Windows.Controls.Calendar.DisplayMode%2A> já estiver <xref:System.Windows.Controls.CalendarMode.Month>, nenhuma ação.|  
|BARRA DE ESPAÇOS ou ENTER|<xref:System.Windows.Controls.CalendarMode.Year> ou <xref:System.Windows.Controls.CalendarMode.Decade>|Alterna <xref:System.Windows.Controls.Calendar.DisplayMode%2A> para o <xref:System.Windows.Controls.CalendarMode.Month> ou <xref:System.Windows.Controls.CalendarMode.Year> representado pelo item focalizado.|  
  
## <a name="see-also"></a>Consulte também

- [Controles](index.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
