---
title: 'Como: Renderizar um elemento de estilo visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
ms.openlocfilehash: 57c2bc5722f77338225d70b514345344211656dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312391"
---
# <a name="how-to-render-a-visual-style-element"></a>Como: Renderizar um elemento de estilo visual
O <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace expõe <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> compatíveis com estilos visuais de elementos de (UI) de interface de objetos que representam o usuário do Windows. Este tópico demonstra como usar o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> classe para renderizar o <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> que representa o **fazer logoff** e **desligar** botões do menu Iniciar.  
  
### <a name="to-render-a-visual-style-element"></a>Para renderizar um elemento de estilo visual  
  
1. Criar um <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> e defini-lo para o elemento que você deseja desenhar. Observe o uso do <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> propriedade e o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> método; o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> construtor lançará uma exceção se os estilos visuais estiverem desabilitados ou um elemento estiver indefinido.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2. Chame o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> método para renderizar o elemento que o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> representa atualmente.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle personalizado derivado de <xref:System.Windows.Forms.Control> classe.  
  
-   Um <xref:System.Windows.Forms.Form> que hospeda o controle personalizado.  
  
-   Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.  
  
## <a name="see-also"></a>Consulte também

- [Renderizando controles com estilos visuais](rendering-controls-with-visual-styles.md)
