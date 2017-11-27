---
title: Como definir margens de elementos e controles
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
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 965e2061d6457084e4f316d27e29865109f62e34
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-margins-of-elements-and-controls"></a><span data-ttu-id="2a175-102">Como definir margens de elementos e controles</span><span class="sxs-lookup"><span data-stu-id="2a175-102">How to: Set Margins of Elements and Controls</span></span>
<span data-ttu-id="2a175-103">Este exemplo descreve como definir o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade alterando qualquer valor de propriedade existente para a margem no code-behind.</span><span class="sxs-lookup"><span data-stu-id="2a175-103">This example describes how to set the <xref:System.Windows.FrameworkElement.Margin%2A> property, by changing any existing property value for the margin in code-behind.</span></span> <span data-ttu-id="2a175-104">O <xref:System.Windows.FrameworkElement.Margin%2A> é uma propriedade do <xref:System.Windows.FrameworkElement> elemento base e, portanto, é herdada por uma variedade de controles e outros elementos.</span><span class="sxs-lookup"><span data-stu-id="2a175-104">The <xref:System.Windows.FrameworkElement.Margin%2A> property is a property of the <xref:System.Windows.FrameworkElement> base element, and is thus inherited by a variety of controls and other elements.</span></span>  
  
 <span data-ttu-id="2a175-105">Este exemplo é escrito em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], com um valor de code-behind do arquivo que o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] refere-se a.</span><span class="sxs-lookup"><span data-stu-id="2a175-105">This example is written in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], with a code-behind file that the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] refers to.</span></span> <span data-ttu-id="2a175-106">Code-behind é mostrado em ambas um [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] e um [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] versão.</span><span class="sxs-lookup"><span data-stu-id="2a175-106">The code-behind is shown in both a [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] and a [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] version.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a175-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a175-107">Example</span></span>  
 [!code-xaml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
