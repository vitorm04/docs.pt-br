---
title: "Como substituir a árvore lógica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e487220f8b06515f3d37f7d55ab7ff6214c85d92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-the-logical-tree"></a>Como substituir a árvore lógica
Embora não seja necessário na maioria dos casos, autores de controle avançados têm a opção de substituir a árvore lógica.  
  
## <a name="example"></a>Exemplo  
 Este exemplo descreve como subclasse <xref:System.Windows.Controls.StackPanel> para substituir a árvore lógica, nesse caso, para impor um comportamento que o painel somente pode ter e processará apenas um único elemento filho. Isso não é necessariamente um comportamento praticamente desejável, mas é mostrado aqui como um meio de que ilustra o cenário para substituir a árvore lógica normal de um elemento.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).
