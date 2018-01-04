---
title: Como localizar o elemento de origem em um manipulador de eventos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d62d657b886b867481088e32fe1dd0614377e146
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>Como localizar o elemento de origem em um manipulador de eventos
Este exemplo mostra como localizar o elemento de origem em um manipulador de eventos.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos que é declarado em um arquivo code-behind. Quando um usuário clica no botão que o manipulador está associado, o manipulador altera um valor de propriedade. O código do manipulador usa o <xref:System.Windows.RoutedEventArgs.Source%2A> propriedade dos dados do evento roteado relatado nos argumentos de evento para alterar o <xref:System.Windows.FrameworkElement.Width%2A> valor da propriedade a <xref:System.Windows.RoutedEventArgs.Source%2A> elemento.  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.RoutedEventArgs>  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
