---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 3e66b2306c11c54db14eb05cc6860257635cc653
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460362"
---
# <a name="datepicker"></a>DatePicker
O controle de <xref:System.Windows.Controls.DatePicker> permite que o usuário selecione uma data digitando-a em um campo de texto ou usando um controle de <xref:System.Windows.Controls.Calendar> suspensa.  
  
 A ilustração a seguir mostra uma <xref:System.Windows.Controls.DatePicker>.  
  
 ![Controle DatePicker](./media/ndp-datepicker.png "NDP_DatePicker")  
Controle DatePicker  
  
 Muitas das propriedades de um controle de <xref:System.Windows.Controls.DatePicker> são para gerenciar suas <xref:System.Windows.Controls.Calendar>internas e funcionam de forma idêntica à propriedade equivalente no <xref:System.Windows.Controls.Calendar>. Em particular, as propriedades <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>e <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> funcionam de forma idêntica às suas <xref:System.Windows.Controls.Calendar> contrapartes. Para obter mais informações, consulte <xref:System.Windows.Controls.Calendar>.  
  
 Os usuários podem digitar uma data diretamente em um campo de texto, que define a propriedade <xref:System.Windows.Controls.DatePicker.Text%2A>. Se o <xref:System.Windows.Controls.DatePicker> não puder converter a cadeia de caracteres inserida em uma data válida, o evento <xref:System.Windows.Controls.DatePicker.DateValidationError> será gerado. Por padrão, isso causa uma exceção, mas um manipulador de eventos para <xref:System.Windows.Controls.DatePicker.DateValidationError> pode definir a propriedade <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> como `false` e impedir que uma exceção seja gerada.  
  
## <a name="see-also"></a>Consulte também

- [Controles](index.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
