---
title: 'Como: Definir margens de elementos e controles'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
ms.openlocfilehash: 3263810806b6b4bbec15eadfd1f1da3a57d12698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052359"
---
# <a name="how-to-set-margins-of-elements-and-controls"></a><span data-ttu-id="936fd-102">Como: Definir margens de elementos e controles</span><span class="sxs-lookup"><span data-stu-id="936fd-102">How to: Set Margins of Elements and Controls</span></span>
<span data-ttu-id="936fd-103">Este exemplo descreve como definir o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade alterando qualquer valor de propriedade existente para a margem no code-behind.</span><span class="sxs-lookup"><span data-stu-id="936fd-103">This example describes how to set the <xref:System.Windows.FrameworkElement.Margin%2A> property, by changing any existing property value for the margin in code-behind.</span></span> <span data-ttu-id="936fd-104">O <xref:System.Windows.FrameworkElement.Margin%2A> é uma propriedade do <xref:System.Windows.FrameworkElement> elemento base e, portanto, é herdada por uma variedade de controles e outros elementos.</span><span class="sxs-lookup"><span data-stu-id="936fd-104">The <xref:System.Windows.FrameworkElement.Margin%2A> property is a property of the <xref:System.Windows.FrameworkElement> base element, and is thus inherited by a variety of controls and other elements.</span></span>  
  
 <span data-ttu-id="936fd-105">Este exemplo é escrito em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], com um code-behind do arquivo que o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] refere-se a.</span><span class="sxs-lookup"><span data-stu-id="936fd-105">This example is written in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], with a code-behind file that the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] refers to.</span></span> <span data-ttu-id="936fd-106">O code-behind é mostrado em ambos um C# e uma versão do Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="936fd-106">The code-behind is shown in both a C# and a Microsoft Visual Basic version.</span></span>  
  
## <a name="example"></a><span data-ttu-id="936fd-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="936fd-107">Example</span></span>  
 [!code-xaml[FEMarginProgrammatic#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
