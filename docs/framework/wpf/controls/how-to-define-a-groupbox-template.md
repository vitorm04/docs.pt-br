---
title: Como definir um modelo de GroupBox
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a63a79b298a45b4efd6d1cbd439d208744358ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="112e9-102">Como definir um modelo de GroupBox</span><span class="sxs-lookup"><span data-stu-id="112e9-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="112e9-103">Este exemplo mostra como criar um modelo para um <xref:System.Windows.Controls.GroupBox> controle.</span><span class="sxs-lookup"><span data-stu-id="112e9-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="112e9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="112e9-104">Example</span></span>  
 <span data-ttu-id="112e9-105">O exemplo a seguir define uma <xref:System.Windows.Controls.GroupBox> modelo de controle usando um <xref:System.Windows.Controls.Grid> controle de layout.</span><span class="sxs-lookup"><span data-stu-id="112e9-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="112e9-106">O modelo usa uma <xref:System.Windows.Controls.BorderGapMaskConverter> para definir a borda do <xref:System.Windows.Controls.GroupBox> para que a borda não oculte o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> conteúdo.</span><span class="sxs-lookup"><span data-stu-id="112e9-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="112e9-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="112e9-107">See Also</span></span>  
 <xref:System.Windows.Controls.GroupBox>  
 [<span data-ttu-id="112e9-108">Tópicos de instruções sobre GroupBox</span><span class="sxs-lookup"><span data-stu-id="112e9-108">GroupBox How-to Topics</span></span>](http://msdn.microsoft.com/en-us/7692e155-a4c6-428c-b7e0-64b3740daca7)
