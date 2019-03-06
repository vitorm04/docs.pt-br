---
title: 'Como: Definir uma caneta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [WPF], defining
- creating [WPF], pens
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
ms.openlocfilehash: 1d69a40604dbf2f7a73c17279ae946faeb6c634a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365771"
---
# <a name="how-to-define-a-pen"></a>Como: Definir uma caneta
Este exemplo mostra como usar um <xref:System.Windows.Media.Pen> uma forma de descrever. Para criar um simples <xref:System.Windows.Media.Pen>, você precisa apenas especificar sua <xref:System.Windows.Media.Pen.Thickness%2A> e <xref:System.Windows.Media.Pen.Brush%2A>. Você pode criar canetas mais complexas, especificando um <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, e <xref:System.Windows.Media.Pen.EndLineCap%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.Pen> descrever uma forma definida por um <xref:System.Windows.Media.GeometryDrawing>.  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![Contornos produzidos por uma caneta](./media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")  
Um GeometryDrawing
