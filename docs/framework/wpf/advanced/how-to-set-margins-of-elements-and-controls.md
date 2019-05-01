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
# <a name="how-to-set-margins-of-elements-and-controls"></a>Como: Definir margens de elementos e controles
Este exemplo descreve como definir o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade alterando qualquer valor de propriedade existente para a margem no code-behind. O <xref:System.Windows.FrameworkElement.Margin%2A> é uma propriedade do <xref:System.Windows.FrameworkElement> elemento base e, portanto, é herdada por uma variedade de controles e outros elementos.  
  
 Este exemplo é escrito em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], com um code-behind do arquivo que o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] refere-se a. O code-behind é mostrado em ambos um C# e uma versão do Microsoft Visual Basic.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[FEMarginProgrammatic#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
