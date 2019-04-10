---
title: 'Como: Definir um modelo de GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: dd53af87ec2d12b2ed0dcf2b23374d76e8f631a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225710"
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="71ee8-102">Como: Definir um modelo de GroupBox</span><span class="sxs-lookup"><span data-stu-id="71ee8-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="71ee8-103">Este exemplo mostra como criar um modelo para um <xref:System.Windows.Controls.GroupBox> controle.</span><span class="sxs-lookup"><span data-stu-id="71ee8-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71ee8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71ee8-104">Example</span></span>  
 <span data-ttu-id="71ee8-105">O exemplo a seguir define uma <xref:System.Windows.Controls.GroupBox> modelo de controle usando um <xref:System.Windows.Controls.Grid> controle de layout.</span><span class="sxs-lookup"><span data-stu-id="71ee8-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="71ee8-106">O modelo usa um <xref:System.Windows.Controls.BorderGapMaskConverter> para definir a borda da <xref:System.Windows.Controls.GroupBox> para que a borda não oculte o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> conteúdo.</span><span class="sxs-lookup"><span data-stu-id="71ee8-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="71ee8-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71ee8-107">See also</span></span>

- <xref:System.Windows.Controls.GroupBox>
- [<span data-ttu-id="71ee8-108">Como: Criar uma caixa de grupo</span><span class="sxs-lookup"><span data-stu-id="71ee8-108">How to: Create a GroupBox</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))
