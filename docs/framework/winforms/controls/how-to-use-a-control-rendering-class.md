---
title: 'Como: Usar uma classe de renderização do controle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
ms.openlocfilehash: 7115c227cb24cf12a50073d0dc587524abf0cbb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163565"
---
# <a name="how-to-use-a-control-rendering-class"></a>Como: Usar uma classe de renderização do controle
Este exemplo demonstra como usar o <xref:System.Windows.Forms.ComboBoxRenderer> classe para renderizar a seta suspensa de uma combinação de controle de caixa. O exemplo consiste de <xref:System.Windows.Forms.Control.OnPaint%2A> método de um controle personalizado simple. O <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> propriedade é usada para determinar se os estilos visuais estão habilitados na área de cliente do windows do aplicativo. Se os estilos visuais estiverem ativos, em seguida, a <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> método processará a seta suspensa com estilos visuais; caso contrário, o <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> método processará a seta suspensa no estilo clássico do Windows.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle personalizado derivado de <xref:System.Windows.Forms.Control> classe.  
  
-   Um <xref:System.Windows.Forms.Form> que hospeda o controle personalizado.  
  
-   Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.  
  
## <a name="see-also"></a>Consulte também

- [Renderizando controles com estilos visuais](rendering-controls-with-visual-styles.md)
