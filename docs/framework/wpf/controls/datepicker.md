---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 910ce09bfad6a46e3d96784b980ee4175c3d26a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550054"
---
# <a name="datepicker"></a>DatePicker
O <xref:System.Windows.Controls.DatePicker> controle permite que o usuário selecione uma data ou digitando-o em um campo de texto ou usando uma lista suspensa <xref:System.Windows.Controls.Calendar> controle.  
  
 A ilustração a seguir mostra um <xref:System.Windows.Controls.DatePicker>.  
  
 ![Controle de DatePicker](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")  
Controle DatePicker  
  
 Muitas de um <xref:System.Windows.Controls.DatePicker> são propriedades de controle para gerenciar seu interno <xref:System.Windows.Controls.Calendar>e a função de forma idêntica para a propriedade equivalente no <xref:System.Windows.Controls.Calendar>. Em particular, o <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, e <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> propriedades funcionam de forma idêntica ao seu <xref:System.Windows.Controls.Calendar> correspondentes. Para obter mais informações, consulte <xref:System.Windows.Controls.Calendar>.  
  
 Os usuários podem digitar uma data diretamente em um campo de texto, que define o <xref:System.Windows.Controls.DatePicker.Text%2A> propriedade. Se o <xref:System.Windows.Controls.DatePicker> não é possível converter a cadeia de caracteres inserida como uma data válida, o <xref:System.Windows.Controls.DatePicker.DateValidationError> evento será gerado. Por padrão, isso faz com que uma exceção, mas um manipulador de eventos <xref:System.Windows.Controls.DatePicker.DateValidationError> pode definir o <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> propriedade `false` e impedir que uma exceção seja gerado.  
  
## <a name="see-also"></a>Consulte também  
 [Controles](../../../../docs/framework/wpf/controls/index.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)
