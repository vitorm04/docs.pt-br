---
title: 'Como: Controlar o preenchimento de uma forma composta'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 89f69d392e8838af99538c759a2f06453e1bcd60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855904"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Como: Controlar o preenchimento de uma forma composta

A <xref:System.Windows.Media.GeometryGroup.FillRule%2A> propriedade de um <xref:System.Windows.Media.GeometryGroup> ou um <xref:System.Windows.Media.PathGeometry>, especifica uma "regra" que a forma composta usa para determinar se um determinado ponto faz parte da geometria. Há dois valores possíveis para <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> e <xref:System.Windows.Media.FillRule.Nonzero>. As seções a seguir descreverão como usar essas duas regras.

**EvenOdd:** Essa regra determina se um ponto está na região de preenchimento desenhando um raio a partir desse ponto para infinito em qualquer direção e contando o número de segmentos de caminho dentro de uma determinada forma que o raio cruza. Se esse número for ímpar, o ponto estará dentro, se for par, o ponto estará fora.

Por exemplo, o XAML a seguir cria uma forma composta composta por uma série de anéis concêntricos (destino) <xref:System.Windows.Media.GeometryGroup.FillRule%2A> com um <xref:System.Windows.Media.FillRule.EvenOdd>definido como.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]

A ilustração a seguir mostra a forma criada no exemplo anterior.

![Um círculo composto por uma série de anéis concêntricos com cores alternadas.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)

Na ilustração anterior, observe que o centro e o terceiro anel não estão preenchidos. Isso ocorre porque um raio desenhado de qualquer ponto dentro de qualquer um desses dois anéis passa por um número par de segmentos. Consulte a ilustração a seguir:

![Diagrama que mostra os raios EvenOdd desenhados no círculo.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)

**NonZero:** Essa regra determina se um ponto está na região de preenchimento do caminho, desenhando um raio a partir desse ponto para infinito em qualquer direção e, em seguida, examinando os locais onde um segmento da forma cruza o raio. Começando com uma contagem de zero, adicione um sempre que um segmento cruzar o raio da esquerda para a direita e subtraia um sempre que um segmento de caminho cruzar o raio da direita para a esquerda. Após a contagem de cruzamentos, se o resultado for zero, o ponto estará fora do caminho. Caso contrário, ele estará dentro.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]

Usando o exemplo anterior, um valor de <xref:System.Windows.Media.FillRule.Nonzero> para <xref:System.Windows.Media.GeometryGroup.FillRule%2A> fornece a seguinte ilustração como resultado:

![Um círculo composto por um anel concêntrico de série, todos preenchidos com a mesma cor.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)

Como podemos ver, todos os anéis estão preenchidos. Isso acontece porque todos os segmentos estão indo na mesma direção, assim, um raio desenhado de qualquer ponto cruzará um ou mais segmentos e a soma dos cruzamentos não será igual a zero. Por exemplo, na ilustração a seguir, as setas vermelhas representam a direção em que os segmentos são desenhados e a seta branca representa um raio arbitrário em execução a partir de um ponto no anel mais interno. Iniciando com um valor de zero, para cada segmento que o raio cruza, um valor de um é adicionado, já que o segmento cruza o raio da esquerda para a direita.

![Diagrama mostrando o valor da propriedade FillRule igual a zero.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)

Para demonstrar melhor o comportamento da <xref:System.Windows.Media.FillRule.Nonzero> regra, é necessária uma forma mais complexa com segmentos executados em direções diferentes. O código XAML abaixo cria uma forma semelhante à do exemplo anterior, exceto que ela é criada com <xref:System.Windows.Media.PathGeometry> um, em <xref:System.Windows.Media.EllipseGeometry> vez disso, cria quatro arcos concêntricos em vez de círculos concêntricos totalmente fechados.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]

A ilustração a seguir mostra a forma criada no exemplo anterior.

![Um círculo composto de uma série de anéis concêntricos com cores alternadas com o terceiro arco não preenchido.](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)

Observe que o terceiro arco partindo do centro não está preenchido. A ilustração a seguir mostra por que isso é. Na ilustração, as setas vermelhas representam a direção em que os segmentos são desenhados. As duas setas brancas representam dois raios arbitrários que se movem para fora de um ponto na região "não preenchida". Como podemos ver na ilustração, a soma dos valores de um determinado raio que cruza os segmentos no seu caminho é zero. Conforme definido acima, uma soma zero significa que o ponto não faz parte da geometria (não faz parte do preenchimento), enquanto uma soma que *não* é zero, incluindo um valor negativo, faz parte da geometria.

![Diagrama mostrando raios arbitrários que cruzam segmentos.](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)

> [!NOTE]
> Para os fins do <xref:System.Windows.Media.FillRule>, todas as formas são consideradas fechadas. Se houver uma lacuna em um segmento, desenhe uma linha imaginária para fechá-la. No exemplo acima, existem pequenas lacunas nos anéis. Devido a isso, seria possível erar que um raio que passasse pela lacuna gerasse um resultado diferente que um raio indo para outra direção. Abaixo está uma ilustração ampliada de uma dessas lacunas e o "segmento imaginário" (segmento que é desenhado para fins de aplicação do <xref:System.Windows.Media.FillRule>) que a fecha.

![Diagrama mostrando segmentos FillRule que estão sempre fechados.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)

## <a name="example"></a>Exemplo

## <a name="see-also"></a>Consulte também

- [Criar uma forma composta](how-to-create-a-composite-shape.md)
- [Visão geral de geometria](geometry-overview.md)
