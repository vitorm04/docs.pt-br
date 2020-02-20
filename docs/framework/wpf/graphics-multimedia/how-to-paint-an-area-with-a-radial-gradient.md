---
title: Como pintar uma área com um gradiente radial
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 8a53d5d7247f82905816265f7c92b22f287591c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452747"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Como pintar uma área com um gradiente radial
Este exemplo mostra como usar a classe <xref:System.Windows.Media.RadialGradientBrush> para pintar uma área com um gradiente radial.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um <xref:System.Windows.Media.RadialGradientBrush> para pintar um retângulo com um gradiente radial que faz a transição de amarelo para vermelho para azul para verde-limão.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 A ilustração a seguir mostra o gradiente do exemplo anterior. As interrupções do gradiente foram realçadas.  
  
 ![Interrupções de gradiente em um gradiente radial](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> Os exemplos neste tópico usam o sistema de coordenadas padrão para definir pontos de controle. O sistema de coordenadas padrão é relativo a uma caixa delimitadora: 0 indica 0% da caixa delimitadora e 1 indica 100% da caixa delimitadora. Você pode alterar esse sistema de coordenadas definindo a propriedade <xref:System.Windows.Media.GradientBrush.MappingMode%2A> para o valor <xref:System.Windows.Media.BrushMappingMode.Absolute>. Um sistema de coordenadas absoluto não é relativo a uma caixa delimitadora. Os valores são interpretados diretamente no espaço local.  
  
 Para obter <xref:System.Windows.Media.RadialGradientBrush> exemplos adicionais, consulte o [exemplo de pincéis](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Para obter mais informações sobre gradientes e outros tipos de pincéis, veja [Visão geral de pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md).
