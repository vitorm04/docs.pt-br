---
title: 'Como: Determinar se um congelável está congelado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 005bb27803830a2e38a7b143d2c4cff669ad1da6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362507"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>Como: Determinar se um congelável está congelado
Este exemplo mostra como determinar se um <xref:System.Windows.Freezable> objeto é congelado. Se você tentar modificar um congelado <xref:System.Windows.Freezable> do objeto, ele gerará um <xref:System.InvalidOperationException>. Para evitar gerar essa exceção, use o <xref:System.Windows.Freezable.IsFrozen%2A> propriedade do <xref:System.Windows.Freezable> objeto para determinar se ele está congelado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir congela um <xref:System.Windows.Media.SolidColorBrush> e, em seguida, testa-o usando o <xref:System.Windows.Freezable.IsFrozen%2A> propriedade para determinar se ele está congelado.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Para obter mais informações sobre <xref:System.Windows.Freezable> objetos, consulte a [visão geral de objetos congeláveis](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [Visão geral de objetos congeláveis](freezable-objects-overview.md)
- [Tópicos de instruções](base-elements-how-to-topics.md)
