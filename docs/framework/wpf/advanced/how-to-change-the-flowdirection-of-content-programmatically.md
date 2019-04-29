---
title: 'Como: Alterar o FlowDirection de conteúdo de forma programática'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
ms.openlocfilehash: ec159ed0efce8b5514788331e8715a55e7a8a638
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776552"
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a><span data-ttu-id="6f558-102">Como: Alterar o FlowDirection de conteúdo de forma programática</span><span class="sxs-lookup"><span data-stu-id="6f558-102">How to: Change the FlowDirection of Content Programmatically</span></span>
<span data-ttu-id="6f558-103">Este exemplo mostra como alterar programaticamente o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade de um <xref:System.Windows.Controls.FlowDocumentReader>.</span><span class="sxs-lookup"><span data-stu-id="6f558-103">This example shows how to programmatically change the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property of a <xref:System.Windows.Controls.FlowDocumentReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f558-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f558-104">Example</span></span>  
 <span data-ttu-id="6f558-105">Duas <xref:System.Windows.Controls.Button> elementos são criados, cada um representando um dos possíveis valores da <xref:System.Windows.FlowDirection>.</span><span class="sxs-lookup"><span data-stu-id="6f558-105">Two <xref:System.Windows.Controls.Button> elements are created, each representing one of the possible values of <xref:System.Windows.FlowDirection>.</span></span> <span data-ttu-id="6f558-106">Quando um botão é clicado, o valor da propriedade associada é aplicado ao conteúdo de um <xref:System.Windows.Controls.FlowDocumentReader> chamado `tf1`.</span><span class="sxs-lookup"><span data-stu-id="6f558-106">When a button is clicked, the associated property value is applied to the contents of a <xref:System.Windows.Controls.FlowDocumentReader> named `tf1`.</span></span>  <span data-ttu-id="6f558-107">O valor da propriedade também é escrito para uma <xref:System.Windows.Controls.TextBlock> chamado `txt1`.</span><span class="sxs-lookup"><span data-stu-id="6f558-107">The property value is also written to a <xref:System.Windows.Controls.TextBlock> named `txt1`.</span></span>  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a><span data-ttu-id="6f558-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f558-108">Example</span></span>  
 <span data-ttu-id="6f558-109">Os eventos associados com os cliques de botão definidos acima são tratados em um C# arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="6f558-109">The events associated with the button clicks defined above are handled in a C# code-behind file.</span></span>  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
