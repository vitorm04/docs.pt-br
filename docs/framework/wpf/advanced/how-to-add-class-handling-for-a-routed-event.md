---
title: Como adicionar tratamento de classes para um evento roteado
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
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f0315bbd1d1a5ab2ae08d8bc1810e240cb6a5a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>Como adicionar tratamento de classes para um evento roteado
Eventos roteados podem ser manipulados por manipuladores de classe ou de instância em qualquer nó da rota. Manipuladores de classe são invocados primeiro e podem ser usados pelas implementações de classe para suprimir eventos da manipulação de instâncias ou apresentar outros comportamentos específicos de evento em eventos pertencentes a classes base. Este exemplo ilustra duas técnicas intimamente relacionadas para implementar manipuladores de classe.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa uma classe personalizada com base no <xref:System.Windows.Controls.Canvas> painel. A premissa básica do aplicativo é que a classe personalizada apresenta comportamentos nos seus elementos filho, incluindo a interceptação de cliques com o botão esquerdo do mouse e a marcação deles como manipulados, antes que a classe de elementos filho ou os manipuladores de instância dela sejam invocados.  
  
 O <xref:System.Windows.UIElement> classe expõe um método virtual que permite tratamento de classe no <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> evento, simplesmente sobrescrevendo o evento. Essa será a maneira mais simples de implementar a manipulação de classes se tal método virtual estiver disponível em algum lugar na hierarquia da classe. O código a seguir mostra o <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementação no "MyEditContainer" que é derivada de <xref:System.Windows.Controls.Canvas>. A implementação marca o evento como manipulado nos argumentos e adiciona algum código para dar ao elemento de origem uma alteração visível básica.  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 Se nenhum virtual estiver disponível em classes base ou para o método particular, tratamento de classe pode ser adicionado diretamente usando um método de utilitário do <xref:System.Windows.EventManager> classe <xref:System.Windows.EventManager.RegisterClassHandler%2A>. Este método só deve ser chamado dentro da inicialização estática de classes que estão adicionando a manipulação de classes. Este exemplo adiciona outro manipulador para <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , e nesse caso, a classe registrada é a classe personalizada. Por outro lado, ao usar os virtuais, a classe registrada é realmente a <xref:System.Windows.UIElement> classe base. Em casos em que as classes base e subclasses registram tratamento de classe, os manipuladores de subclasse são invocados primeiro. O comportamento em um aplicativo seria que primeiro esse manipulador mostraria sua caixa de mensagem e, em seguida, a alteração visual no manipulador do método virtual seria mostrada.  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.EventManager>  
 [Marcando eventos roteados como manipulados e tratamento de classes](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Manipular um evento roteado](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
