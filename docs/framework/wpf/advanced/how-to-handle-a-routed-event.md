---
title: Como identificar um evento roteado
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
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83f59f2df9311f30995b18529a733a5569c85ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-a-routed-event"></a>Como identificar um evento roteado
Este exemplo mostra como os eventos de propagação funcionam e como escrever um manipulador que pode processar os dados de eventos roteados.  
  
## <a name="example"></a>Exemplo  
 Em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], os elementos são organizados em uma estrutura de árvore de elementos. O elemento pai pode participar da manipulação de eventos que são inicialmente gerados por elementos filho na árvore de elementos. Isso é possibilitado pelo roteamento de eventos.  
  
 Eventos roteados geralmente seguem uma das duas estratégias de roteamento, propagação ou túnel. Este exemplo enfoca o evento e usa a <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> eventos para mostrar como roteamento funciona.  
  
 O exemplo a seguir cria dois <xref:System.Windows.Controls.Button> controla e usa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributo sintaxe para anexar um manipulador de eventos a um elemento pai comum, que neste exemplo é <xref:System.Windows.Controls.StackPanel>. Em vez de anexar manipuladores de eventos individuais para cada <xref:System.Windows.Controls.Button> elemento filho, o exemplo usa a sintaxe para anexar o manipulador de eventos para o <xref:System.Windows.Controls.StackPanel> elemento pai. Esse padrão de manipulação de eventos mostra como usar o roteamento de eventos como uma técnica para reduzir o número de elementos aos quais um manipulador está anexado. Todos os eventos de bolha para cada <xref:System.Windows.Controls.Button> rota por meio do elemento pai.  
  
 Observe que no pai <xref:System.Windows.Controls.StackPanel> elemento, o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> nome do evento especificado como o atributo é parcialmente qualificado ao nomear a <xref:System.Windows.Controls.Button> classe. O <xref:System.Windows.Controls.Button> classe é um <xref:System.Windows.Controls.Primitives.ButtonBase> derivado da classe que tem o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento na sua lista de membros. Essa técnica parcial de qualificação para anexar um manipulador de eventos será necessária se o evento que está sendo manipulado não existir nos membros de listagem do elemento ao qual o manipulador de eventos roteados está conectado.  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 A exemplo a seguir trata o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  O exemplo informa qual elemento manipula o evento e qual elemento gera o evento. O manipulador de eventos é executado quando o usuário clica em um dos botões.  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.RoutedEvent>  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [Sintaxe XAML em detalhes](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
