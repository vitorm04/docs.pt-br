---
title: 'Como: Reconhecer gestos de aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
ms.openlocfilehash: 68a7c8cd4b8ed935d005fabff37a7b44c1b98012
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506700"
---
# <a name="how-to-recognize-application-gestures"></a><span data-ttu-id="ac9c7-102">Como: Reconhecer gestos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ac9c7-102">How To: Recognize Application Gestures</span></span>
<span data-ttu-id="ac9c7-103">O exemplo a seguir demonstra como apagar tinta quando um usuário faz uma <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gestos em um <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-103">The following example demonstrates how to erase ink when a user makes a <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesture on an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="ac9c7-104">Este exemplo pressupõe um <xref:System.Windows.Controls.InkCanvas>, chamado `inkCanvas1`, é declarado no arquivo XAML.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-104">This example assumes an <xref:System.Windows.Controls.InkCanvas>, called `inkCanvas1`, is declared in the XAML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac9c7-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac9c7-105">Example</span></span>  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ac9c7-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac9c7-106">See also</span></span>
- <xref:System.Windows.Ink.ApplicationGesture>
- <xref:System.Windows.Controls.InkCanvas>
- <xref:System.Windows.Controls.InkCanvas.Gesture>
