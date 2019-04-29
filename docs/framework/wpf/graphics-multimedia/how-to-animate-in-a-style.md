---
title: Como animar em um estilo (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 5fb18a2d927746c3437ec01d2a19327be373cae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789279"
---
# <a name="how-to-animate-in-a-style"></a>Como animar em um estilo

Este exemplo mostra como animar propriedades em um estilo. Ao animar em um estilo, somente o elemento de estrutura para o qual o estilo está definido pode ser alvo diretamente. Para direcionar um objeto freezable, é preciso fazer a "marcação" de uma propriedade do elemento.

No exemplo a seguir, várias animações são definidas em um estilo e aplicadas a um <xref:System.Windows.Controls.Button>. Quando o usuário move o mouse sobre o botão, ele passa de opaco a parcialmente translúcido e repete o processo. Quando o usuário move o mouse para fora do botão, este fica completamente opaco. Quando o botão é clicado, sua cor da tela de fundo muda de laranja para branco e volta a cor original. Porque o <xref:System.Windows.Media.SolidColorBrush> usado para pintar o botão não pode ser alvo diretamente, ele é acessado marcando o botão <xref:System.Windows.Controls.Control.Background%2A> propriedade.

## <a name="example"></a>Exemplo

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Observe que ao animar dentro de um estilo, é possível segmentar objetos que não existem. Por exemplo, suponha que seu estilo usa um <xref:System.Windows.Media.SolidColorBrush> definir a propriedade de plano de fundo de um botão, mas em algum ponto, o estilo é substituído e o plano de fundo do botão é definido com um <xref:System.Windows.Media.LinearGradientBrush>.  Tentar animar o <xref:System.Windows.Media.SolidColorBrush> não lançará uma exceção; a animação simplesmente falhará silenciosamente.

Para obter mais informações sobre a sintaxe de storyboard, consulte o [visão geral de Storyboards](storyboards-overview.md). Para mais informações sobre animação, consulte [Visão Geral de Animação](animation-overview.md). Para mais informações sobre estilos, consulte [Estilos e Modelagem](../controls/styling-and-templating.md).
