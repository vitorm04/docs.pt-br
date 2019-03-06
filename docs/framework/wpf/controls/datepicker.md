---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: a135188b2c573a578aa5b6be4910e6d02471aee1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362247"
---
# <a name="datepicker"></a>DatePicker
O <xref:System.Windows.Controls.DatePicker> controle permite que o usuário selecione uma data digitando-o em um campo de texto ou usando uma lista suspensa <xref:System.Windows.Controls.Calendar> controle.  
  
 A ilustração a seguir mostra um <xref:System.Windows.Controls.DatePicker>.  
  
 ![Controle DatePicker](./media/ndp-datepicker.png "NDP_DatePicker")  
Controle DatePicker  
  
 Muitos de uma <xref:System.Windows.Controls.DatePicker> propriedades do controle são para gerenciar seu interno <xref:System.Windows.Controls.Calendar>e a função de forma idêntica para a propriedade equivalente em <xref:System.Windows.Controls.Calendar>. Em particular, o <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, e <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> propriedades funcionam de maneira idêntica às suas <xref:System.Windows.Controls.Calendar> equivalentes. Para obter mais informações, consulte <xref:System.Windows.Controls.Calendar>.  
  
 Os usuários podem digitar uma data diretamente em um campo de texto, que define o <xref:System.Windows.Controls.DatePicker.Text%2A> propriedade. Se o <xref:System.Windows.Controls.DatePicker> não é possível converter a cadeia de caracteres inserida como uma data válida, o <xref:System.Windows.Controls.DatePicker.DateValidationError> evento será gerado. Por padrão, isso faz com que uma exceção, mas um manipulador de eventos <xref:System.Windows.Controls.DatePicker.DateValidationError> pode definir o <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> propriedade `false` e impedir que uma exceção que está sendo gerado.  
  
## <a name="see-also"></a>Consulte também
- [Controles](index.md)
- [Estilo e modelagem](styling-and-templating.md)
