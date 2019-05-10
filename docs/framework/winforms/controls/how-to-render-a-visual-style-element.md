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
ms.openlocfilehash: a2b9524b6a3e3c77d3c68c4d9e138b8c0e2a9373
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662304"
---
# <a name="how-to-render-a-visual-style-element"></a><span data-ttu-id="dd84a-102">Como: Renderizar um elemento de estilo visual</span><span class="sxs-lookup"><span data-stu-id="dd84a-102">How to: Render a Visual Style Element</span></span>
<span data-ttu-id="dd84a-103">O <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace expõe <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> compatíveis com estilos visuais de elementos de (UI) de interface de objetos que representam o usuário do Windows.</span><span class="sxs-lookup"><span data-stu-id="dd84a-103">The <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace exposes <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> objects that represent the Windows user interface (UI) elements supported by visual styles.</span></span> <span data-ttu-id="dd84a-104">Este tópico demonstra como usar o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> classe para renderizar o <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> que representa o **fazer logoff** e **desligar** botões do menu Iniciar.</span><span class="sxs-lookup"><span data-stu-id="dd84a-104">This topic demonstrates how to use the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> class to render the <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> that represents the **Log Off** and **Shut Down** buttons of the Start menu.</span></span>  
  
### <a name="to-render-a-visual-style-element"></a><span data-ttu-id="dd84a-105">Para renderizar um elemento de estilo visual</span><span class="sxs-lookup"><span data-stu-id="dd84a-105">To render a visual style element</span></span>  
  
1. <span data-ttu-id="dd84a-106">Criar um <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> e defini-lo para o elemento que você deseja desenhar.</span><span class="sxs-lookup"><span data-stu-id="dd84a-106">Create a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> and set it to the element you want to draw.</span></span> <span data-ttu-id="dd84a-107">Observe o uso do <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> propriedade e o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> método; o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> construtor lançará uma exceção se os estilos visuais estiverem desabilitados ou um elemento estiver indefinido.</span><span class="sxs-lookup"><span data-stu-id="dd84a-107">Note the use of the <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> property and the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> method; the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> constructor will throw an exception if visual styles are disabled or an element is undefined.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2. <span data-ttu-id="dd84a-108">Chame o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> método para renderizar o elemento que o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> representa atualmente.</span><span class="sxs-lookup"><span data-stu-id="dd84a-108">Call the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> method to render the element that the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> currently represents.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dd84a-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="dd84a-109">Compiling the Code</span></span>  
 <span data-ttu-id="dd84a-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="dd84a-110">This example requires:</span></span>  
  
- <span data-ttu-id="dd84a-111">Um controle personalizado derivado de <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="dd84a-111">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
- <span data-ttu-id="dd84a-112">Um <xref:System.Windows.Forms.Form> que hospeda o controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="dd84a-112">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
- <span data-ttu-id="dd84a-113">Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span><span class="sxs-lookup"><span data-stu-id="dd84a-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd84a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd84a-114">See also</span></span>

- [<span data-ttu-id="dd84a-115">Renderizando controles com estilos visuais</span><span class="sxs-lookup"><span data-stu-id="dd84a-115">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)
