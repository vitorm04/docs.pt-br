---
title: Como definir um escopo de nome
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
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3007088f849f40e4e9b4f1846c19c98c33e95c17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-name-scope"></a>Como definir um escopo de nome
Para animar com <xref:System.Windows.Media.Animation.Storyboard> no código, você deve criar um <xref:System.Windows.NameScope> e registrar os nomes dos objetos de destino com o elemento que possui esse escopo de nomes. No exemplo a seguir, uma <xref:System.Windows.NameScope> é criado para `myMainPanel`. Dois botões, `button1` e `button2`, são adicionados ao painel e seus nomes registrados. Várias animações e um <xref:System.Windows.Media.Animation.Storyboard> são criados. O storyboard <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método é usado para iniciar as animações.  
  
 Porque `button1`, `button2`, e `myMainPanel` compartilham o mesmo escopo de nomes, qualquer um deles pode ser usado com o <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método para iniciar as animações.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a>Consulte também  
 [Animar uma propriedade usando um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
