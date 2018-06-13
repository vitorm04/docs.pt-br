---
title: Como associar dados a um InkCanvas
ms.date: 03/30/2017
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
ms.openlocfilehash: 4081ae7dd6854934804062cfce60d10106c1e1d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543164"
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a><span data-ttu-id="0814a-102">Como associar dados a um InkCanvas</span><span class="sxs-lookup"><span data-stu-id="0814a-102">How to: Data Bind to an InkCanvas</span></span>
## <a name="example"></a><span data-ttu-id="0814a-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0814a-103">Example</span></span>  
 <span data-ttu-id="0814a-104">O exemplo a seguir demonstra como associar o <xref:System.Windows.Controls.InkCanvas.Strokes%2A> propriedade de um <xref:System.Windows.Controls.InkCanvas> para outro <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="0814a-104">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property of an <xref:System.Windows.Controls.InkCanvas> to another <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 <span data-ttu-id="0814a-105">O exemplo a seguir demonstra como associar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedade para uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="0814a-105">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property to a data source.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 <span data-ttu-id="0814a-106">O exemplo a seguir declara duas <xref:System.Windows.Controls.InkCanvas> objetos em XAML e estabelece a associação de dados entre eles e outras fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="0814a-106">The following example declares two <xref:System.Windows.Controls.InkCanvas> objects in XAML and establishes data binding between them and other data sources.</span></span>  <span data-ttu-id="0814a-107">A primeira <xref:System.Windows.Controls.InkCanvas>, chamado `ic`, está associado a duas fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="0814a-107">The first <xref:System.Windows.Controls.InkCanvas>, called `ic`, is bound to two data sources.</span></span>  <span data-ttu-id="0814a-108">O <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> e <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedades `ic` estão associados a <xref:System.Windows.Controls.ListBox> objetos, que por sua vez são associados a matrizes definidas em XAML.</span><span class="sxs-lookup"><span data-stu-id="0814a-108">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> and <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties on `ic` are bound to <xref:System.Windows.Controls.ListBox> objects, which are in turn bound to arrays defined in the XAML.</span></span>  <span data-ttu-id="0814a-109">O <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, e <xref:System.Windows.Controls.InkCanvas.Strokes%2A> propriedades do segundo <xref:System.Windows.Controls.InkCanvas> são vinculados ao primeiro <xref:System.Windows.Controls.InkCanvas>, `ic`.</span><span class="sxs-lookup"><span data-stu-id="0814a-109">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, and <xref:System.Windows.Controls.InkCanvas.Strokes%2A> properties of the second <xref:System.Windows.Controls.InkCanvas> are bound to the first <xref:System.Windows.Controls.InkCanvas>, `ic`.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
