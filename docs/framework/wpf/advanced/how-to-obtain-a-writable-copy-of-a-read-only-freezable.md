---
title: "Como obter uma cópia gravável de um congelável somente leitura"
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
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fe22e49ee28de60bc76d7a4f543462bbcfac48c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>Como obter uma cópia gravável de um congelável somente leitura
Este exemplo mostra como usar o <xref:System.Windows.Freezable.Clone%2A> método para criar uma cópia gravável somente leitura <xref:System.Windows.Freezable>.  
  
 Após um <xref:System.Windows.Freezable> objeto está marcado como somente leitura ("congelado"), você não pode modificá-lo. No entanto, você pode usar o <xref:System.Windows.Freezable.Clone%2A> método para criar um clone modificável do objeto congelado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um clone modificável de um congelada <xref:System.Windows.Media.SolidColorBrush> objeto.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Para obter mais informações sobre <xref:System.Windows.Freezable> objetos, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>  
 [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
