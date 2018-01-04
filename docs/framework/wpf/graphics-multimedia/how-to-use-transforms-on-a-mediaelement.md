---
title: "Como usar transformações em um MediaElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Transforms [WPF], using on MediaElements
- multimedia [WPF], using Transforms on MediaElements
- MediaElements [WPF], using Transforms on
ms.assetid: d89c95e3-27c5-4748-8a27-72e432674032
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a031eb48b4ba82d0200a617a1176692058174da3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-transforms-on-a-mediaelement"></a><span data-ttu-id="9886f-102">Como usar transformações em um MediaElement</span><span class="sxs-lookup"><span data-stu-id="9886f-102">How to: Use Transforms on a MediaElement</span></span>
<span data-ttu-id="9886f-103">Este exemplo mostra como usar um <xref:System.Windows.Media.RotateTransform> em um <xref:System.Windows.Controls.MediaElement>.</span><span class="sxs-lookup"><span data-stu-id="9886f-103">This example shows how to use a <xref:System.Windows.Media.RotateTransform> on a <xref:System.Windows.Controls.MediaElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9886f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9886f-104">Example</span></span>  
 <span data-ttu-id="9886f-105">Na seguinte marcação, o <xref:System.Windows.Controls.MediaElement> for girado usando um <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="9886f-105">In the following markup, the <xref:System.Windows.Controls.MediaElement> is rotated using a <xref:System.Windows.Media.RotateTransform>.</span></span>  
  
 [!code-xaml[MediaElement_snippet#MediaElementRotateTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snippet/CSharp/TransformExample.xaml#mediaelementrotatetransform)]
