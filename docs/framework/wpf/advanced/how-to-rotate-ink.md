---
title: 'Como: Girar tinta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], rotating
- rotating ink [WPF]
ms.assetid: fac36cc9-dd01-41ca-9bde-9d33e3790bbe
ms.openlocfilehash: 31f5d0ffb6f0fdcdaef13bc44653f8c7938ac7f3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378789"
---
# <a name="how-to-rotate-ink"></a><span data-ttu-id="f0cfc-102">Como: Girar tinta</span><span class="sxs-lookup"><span data-stu-id="f0cfc-102">How to: Rotate Ink</span></span>
## <a name="example"></a><span data-ttu-id="f0cfc-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0cfc-103">Example</span></span>  
 <span data-ttu-id="f0cfc-104">O exemplo a seguir copia a tinta de um <xref:System.Windows.Controls.InkCanvas> para um <xref:System.Windows.Controls.Canvas> que contém um <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="f0cfc-104">The following example copies the ink from an <xref:System.Windows.Controls.InkCanvas> to a <xref:System.Windows.Controls.Canvas> that contains an <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="f0cfc-105">Quando o aplicativo copia a tinta, ela também rotacionará a tinta 90 graus no sentido horário.</span><span class="sxs-lookup"><span data-stu-id="f0cfc-105">When the application copies the ink, it also rotates the ink 90 degrees clockwise.</span></span>  
  
 [!code-xaml[HowToRotateInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[HowToRotateInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="f0cfc-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0cfc-106">Example</span></span>  
 <span data-ttu-id="f0cfc-107">O exemplo a seguir é um personalizado <xref:System.Windows.Documents.Adorner> que gira os traços em um <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="f0cfc-107">The following example is a custom <xref:System.Windows.Documents.Adorner> that rotates the strokes on an <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[AdornerForStrokes#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/RotatingAdornerForStrokes.cs#1)]
 [!code-vb[AdornerForStrokes#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/RotatingAdornerForStrokes.vb#1)]  
  
 <span data-ttu-id="f0cfc-108">O exemplo a seguir é um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo que define um <xref:System.Windows.Controls.InkPresenter> e a preenche com tinta.</span><span class="sxs-lookup"><span data-stu-id="f0cfc-108">The following example is a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file that defines an <xref:System.Windows.Controls.InkPresenter> and populates it with ink.</span></span> <span data-ttu-id="f0cfc-109">O `Window_Loaded` manipulador de eventos adiciona o adorno personalizado para o <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="f0cfc-109">The `Window_Loaded` event handler adds the custom adorner to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-xaml[AdornerForStrokes#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[AdornerForStrokes#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml.cs#3)]
 [!code-vb[AdornerForStrokes#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/Window1.xaml.vb#3)]
