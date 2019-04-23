---
title: 'Como: Obter uma cópia gravável de um congelável somente leitura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 910c5dada6ca82f68992722e4df6b35f9f7497c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206467"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>Como: Obter uma cópia gravável de um congelável somente leitura
Este exemplo mostra como usar o <xref:System.Windows.Freezable.Clone%2A> método para criar uma cópia gravável de somente leitura <xref:System.Windows.Freezable>.  
  
 Após um <xref:System.Windows.Freezable> objeto é marcado como somente leitura ("congelado"), você não pode modificá-lo. No entanto, você pode usar o <xref:System.Windows.Freezable.Clone%2A> método para criar um clone modificável do objeto congelado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um clone modificável de um congelado <xref:System.Windows.Media.SolidColorBrush> objeto.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Para obter mais informações sobre <xref:System.Windows.Freezable> objetos, consulte a [visão geral de objetos congeláveis](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [Visão geral de objetos congeláveis](freezable-objects-overview.md)
- [Tópicos de instruções](base-elements-how-to-topics.md)
