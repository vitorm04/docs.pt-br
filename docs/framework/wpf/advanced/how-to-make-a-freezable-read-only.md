---
title: "Como tornar um congelável somente leitura"
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
helpviewer_keywords: Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c407a2fcccfbda29ba23f63ba6ae71302c734d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-freezable-read-only"></a>Como tornar um congelável somente leitura
Este exemplo mostra como fazer uma <xref:System.Windows.Freezable> somente leitura chamando seu <xref:System.Windows.Freezable.Freeze%2A> método.  
  
 Não é possível congelar uma <xref:System.Windows.Freezable> objeto se qualquer uma das seguintes condições for `true` sobre o objeto:  
  
-   Ele tem propriedades animadas ou associadas a dados.  
  
-   Ela tem propriedades que são definidas por um recurso dinâmico. Para obter mais informações sobre recursos dinâmicos, consulte o [recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Ele contém <xref:System.Windows.Freezable> subobjetos não podem ser congelados.  
  
 Se essas condições forem `false` para sua <xref:System.Windows.Freezable> objeto e você não pretende modificá-lo, considere congelamento para obter benefícios de desempenho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir congela um <xref:System.Windows.Media.SolidColorBrush>, que é um tipo de <xref:System.Windows.Freezable> objeto.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Para obter mais informações sobre <xref:System.Windows.Freezable> objetos, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
