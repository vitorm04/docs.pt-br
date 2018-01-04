---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd2a1755ae076369661b2c9a7a2b744961cdb129
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="datepicker"></a><span data-ttu-id="839ba-102">DatePicker</span><span class="sxs-lookup"><span data-stu-id="839ba-102">DatePicker</span></span>
<span data-ttu-id="839ba-103">O <xref:System.Windows.Controls.DatePicker> controle permite que o usuário selecione uma data ou digitando-o em um campo de texto ou usando uma lista suspensa <xref:System.Windows.Controls.Calendar> controle.</span><span class="sxs-lookup"><span data-stu-id="839ba-103">The <xref:System.Windows.Controls.DatePicker> control allows the user to select a date by either typing it into a text field or by using a drop-down <xref:System.Windows.Controls.Calendar> control.</span></span>  
  
 <span data-ttu-id="839ba-104">A ilustração a seguir mostra um <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="839ba-104">The following illustration shows a <xref:System.Windows.Controls.DatePicker>.</span></span>  
  
 <span data-ttu-id="839ba-105">![Controle de DatePicker](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span><span class="sxs-lookup"><span data-stu-id="839ba-105">![DatePicker control](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span></span>  
<span data-ttu-id="839ba-106">Controle DatePicker</span><span class="sxs-lookup"><span data-stu-id="839ba-106">DatePicker Control</span></span>  
  
 <span data-ttu-id="839ba-107">Muitas de um <xref:System.Windows.Controls.DatePicker> são propriedades de controle para gerenciar seu interno <xref:System.Windows.Controls.Calendar>e a função de forma idêntica para a propriedade equivalente no <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="839ba-107">Many of a <xref:System.Windows.Controls.DatePicker> control's properties are for managing its built-in <xref:System.Windows.Controls.Calendar>, and function identically to the equivalent property in <xref:System.Windows.Controls.Calendar>.</span></span> <span data-ttu-id="839ba-108">Em particular, o <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, e <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> propriedades funcionam de forma idêntica ao seu <xref:System.Windows.Controls.Calendar> correspondentes.</span><span class="sxs-lookup"><span data-stu-id="839ba-108">In particular, the <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, and <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> properties function identically to their <xref:System.Windows.Controls.Calendar> counterparts.</span></span> <span data-ttu-id="839ba-109">Para obter mais informações, consulte <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="839ba-109">For more information, see <xref:System.Windows.Controls.Calendar>.</span></span>  
  
 <span data-ttu-id="839ba-110">Os usuários podem digitar uma data diretamente em um campo de texto, que define o <xref:System.Windows.Controls.DatePicker.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="839ba-110">Users can type a date directly into a text field, which sets the <xref:System.Windows.Controls.DatePicker.Text%2A> property.</span></span> <span data-ttu-id="839ba-111">Se o <xref:System.Windows.Controls.DatePicker> não é possível converter a cadeia de caracteres inserida como uma data válida, o <xref:System.Windows.Controls.DatePicker.DateValidationError> evento será gerado.</span><span class="sxs-lookup"><span data-stu-id="839ba-111">If the <xref:System.Windows.Controls.DatePicker> cannot convert the entered string to a valid date, the <xref:System.Windows.Controls.DatePicker.DateValidationError> event will be raised.</span></span> <span data-ttu-id="839ba-112">Por padrão, isso faz com que uma exceção, mas um manipulador de eventos <xref:System.Windows.Controls.DatePicker.DateValidationError> pode definir o <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> propriedade `false` e impedir que uma exceção seja gerado.</span><span class="sxs-lookup"><span data-stu-id="839ba-112">By default, this causes an exception, but an event handler for <xref:System.Windows.Controls.DatePicker.DateValidationError> can set the <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> property to `false` and prevent an exception from being raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839ba-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="839ba-113">See Also</span></span>  
 [<span data-ttu-id="839ba-114">Controles</span><span class="sxs-lookup"><span data-stu-id="839ba-114">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="839ba-115">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="839ba-115">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
