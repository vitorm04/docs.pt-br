---
title: Como localizar um elemento pelo nome
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c51f22cb663b77ddcbbc280ab9d93c5e0eb7405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-an-element-by-its-name"></a><span data-ttu-id="a04f6-102">Como localizar um elemento pelo nome</span><span class="sxs-lookup"><span data-stu-id="a04f6-102">How to: Find an Element by Its Name</span></span>
<span data-ttu-id="a04f6-103">Este exemplo descreve como usar o <xref:System.Windows.FrameworkElement.FindName%2A> método para encontrar um elemento por seu <xref:System.Windows.FrameworkElement.Name%2A> valor.</span><span class="sxs-lookup"><span data-stu-id="a04f6-103">This example describes how to use the <xref:System.Windows.FrameworkElement.FindName%2A> method to find an element by its <xref:System.Windows.FrameworkElement.Name%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a04f6-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04f6-104">Example</span></span>  
 <span data-ttu-id="a04f6-105">Neste exemplo, o método para localizar um elemento específico por seu nome é gravada como o manipulador de eventos de um botão.</span><span class="sxs-lookup"><span data-stu-id="a04f6-105">In this example, the method to find a particular element by its name is written as the event handler of a button.</span></span> <span data-ttu-id="a04f6-106">`stackPanel`é o <xref:System.Windows.FrameworkElement.Name%2A> da raiz <xref:System.Windows.FrameworkElement> está sendo pesquisada, e o método exemplo então visualmente indica o elemento encontrado convertendo-o como <xref:System.Windows.Controls.TextBlock> e alterar um do <xref:System.Windows.Controls.TextBlock> visível [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] propriedades.</span><span class="sxs-lookup"><span data-stu-id="a04f6-106">`stackPanel` is the <xref:System.Windows.FrameworkElement.Name%2A> of the root <xref:System.Windows.FrameworkElement> being searched, and the example method then visually indicates the found element by casting it as <xref:System.Windows.Controls.TextBlock> and changing one of the <xref:System.Windows.Controls.TextBlock> visible [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] properties.</span></span>  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
