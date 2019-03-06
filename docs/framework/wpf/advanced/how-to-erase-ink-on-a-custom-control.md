---
title: 'Como: Apagar tinta em um controle personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
ms.openlocfilehash: 60e2af64cb0c5b313f4f1201cab70da6a88f61e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365887"
---
# <a name="how-to-erase-ink-on-a-custom-control"></a><span data-ttu-id="7b4bd-102">Como: Apagar tinta em um controle personalizado</span><span class="sxs-lookup"><span data-stu-id="7b4bd-102">How to: Erase Ink on a Custom Control</span></span>
<span data-ttu-id="7b4bd-103">O <xref:System.Windows.Ink.IncrementalStrokeHitTester> determina se o traço desenhado atualmente intersecciona outro traço.</span><span class="sxs-lookup"><span data-stu-id="7b4bd-103">The <xref:System.Windows.Ink.IncrementalStrokeHitTester> determines whether the currently drawn stroke intersects another stroke.</span></span>  <span data-ttu-id="7b4bd-104">Isso é útil para criar um controle que permite que um usuário apagar partes de um traço, a maneira como um usuário pode em uma <xref:System.Windows.Controls.InkCanvas> quando o <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> é definido como <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span><span class="sxs-lookup"><span data-stu-id="7b4bd-104">This is useful for creating a control that enables a user to erase parts of a stroke, the way a user can on an <xref:System.Windows.Controls.InkCanvas> when the <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> is set to <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b4bd-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b4bd-105">Example</span></span>  
 <span data-ttu-id="7b4bd-106">O exemplo a seguir cria um controle personalizado que permite que o usuário apagar parte de traços.</span><span class="sxs-lookup"><span data-stu-id="7b4bd-106">The following example creates a custom control that enables the user to erase parts of strokes.</span></span>  <span data-ttu-id="7b4bd-107">Este exemplo cria um controle que contém a tinta quando ele é inicializado.</span><span class="sxs-lookup"><span data-stu-id="7b4bd-107">This example creates a control that contains ink when it is initialized.</span></span>  <span data-ttu-id="7b4bd-108">Para criar um controle que coleta tinta, consulte [criando um controle de entrada de tinta](creating-an-ink-input-control.md).</span><span class="sxs-lookup"><span data-stu-id="7b4bd-108">To create a control that collects ink, see [Creating an Ink Input Control](creating-an-ink-input-control.md).</span></span>  
  
 [!code-csharp[HowToEraseInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
