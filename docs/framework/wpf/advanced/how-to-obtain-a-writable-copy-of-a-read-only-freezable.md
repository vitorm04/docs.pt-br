---
title: Como obter uma cópia gravável de um congelável somente leitura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 894a2e42ca3f5cbb159c3129227f4b03e71fc4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
