---
title: Como implementar um mecanismo de layout personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- layout engines [Windows Forms], custom
- TableLayoutPanel control [Windows Forms], layout engine
- layout engines [Windows Forms], implementing
- FlowLayoutPanel control [Windows Forms], layout engine
ms.assetid: f91aa91c-29f4-4089-95ca-5d48b774b00e
ms.openlocfilehash: 0444f0d03a36adf833c04167c6d7a3c302ab15dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531291"
---
# <a name="how-to-implement-a-custom-layout-engine"></a>Como implementar um mecanismo de layout personalizado
O exemplo de código a seguir demonstra como criar um mecanismo de layout personalizado que executa um layout de fluxo simples. Ele implementa um controle de painel chamado `DemoFlowPanel`, que substitui o <xref:System.Windows.Forms.Control.LayoutEngine%2A> propriedade para fornecer uma instância do `DemoFlowLayout` classe.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Layout.LayoutEngine>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=nameWithType>
