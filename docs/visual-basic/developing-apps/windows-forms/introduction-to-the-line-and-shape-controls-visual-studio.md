---
title: Introdução aos controles de linha e forma (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
ms.openlocfilehash: 3623c2363f39150fd4bb202ba61ebd51df383ca8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699916"
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Introdução aos controles de linha e forma (Visual Studio)
Os controles do Visual Basic Power Packs linha e forma são um conjunto de três controles gráficos que lhe permitem desenhar linhas e formas em formulários e contêineres. O <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controle é usado para desenhar linhas horizontais, verticais e diagonais. O <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> controle é usado para desenhar círculos e elipses e o <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controle é usado para desenhar retângulos e quadrados.  
  
## <a name="line-and-shape-controls"></a>Controles de linha e forma  
 Controles de linha e forma encapsulam vários dos métodos gráficos contidos no <xref:System.Drawing> namespace. Isso permite que você desenhar linhas e formas em uma única etapa sem ter de criar objetos gráficos, canetas e pincéis. Técnicas gráficas complexas, como preenchimentos com gradiente podem ser feitas definindo-se apenas algumas propriedades.  
  
 Embora também seja possível desenhar linhas e formas, usando métodos gráficos, há diversas vantagens em usar os controles de linha e forma:  
  
-   Métodos gráficos podem ser chamados somente em tempo de execução. Controles de linha e forma podem ser adicionados a um formulário em tempo de design. Isso permite que você veja sua aparência e posicioná-los; Eles também podem ser adicionados em tempo de execução.  
  
-   Controles de linha e forma são selecionáveis no tempo de execução, fornecendo a eventos, como <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> e <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>. As saídas dos métodos gráficos não são selecionáveis e não fornecem eventos.  
  
-   Controles de linha e forma fornecem <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> e <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> métodos que permitem que você controle a ordem z em tempo de design e em tempo de execução. A ordem z dos métodos gráficos pode ser controlada apenas alterando sua ordem de execução em tempo de execução.  
  
-   Controles de linha e forma são controles sem janelas; eles têm nenhum identificador de janela e, portanto, usar menos recursos do sistema.  
  
### <a name="object-model"></a>Modelo de objeto  
 Controles de linha e forma derivam de uma base de <xref:Microsoft.VisualBasic.PowerPacks.Shape> classe que define suas propriedades, métodos e eventos.  
  
 A ilustração a seguir mostra a hierarquia de objeto de linha e forma.  
  
 ![Um diagrama da hierarquia de objetos de linha e forma](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Hierarquia de objetos de linha e forma  
  
 A derivada <xref:Microsoft.VisualBasic.PowerPacks.LineShape> classe contém propriedades, métodos e eventos que são exclusivos para linhas. Derivado <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> é a classe base para <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; ele contém propriedades, métodos e eventos comuns a todas as formas. Você também pode derivar de <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> para criar seus próprios `Shape` controles.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> classes podem ser usadas para desenhar retângulos com cantos arredondados, elipses, retângulos e círculos.  
  
 Quando um controle de linha ou forma é adicionado a um formulário ou contêiner, um invisível <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> objeto é criado. O <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> atua como uma tela para as formas dentro de cada controle de contêiner; cada <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> tem um correspondente <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> que permite que você percorrer os controles de linha e forma. Você pode mover formas de um contêiner para outro usando recortar e colar ou arrastar e soltar. Quando a última forma é removida de um contêiner, o <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> será removida também.  
  
> [!NOTE]
>  Nem todos os controles de contêiner dão suporte os controles de linha e forma. Não é possível hospedar um controle de linha ou forma em um <xref:System.Windows.Forms.TableLayoutPanel> ou um <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.PowerPacks>
- [Como: Desenhar linhas com o controle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [Como: Desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [Como: Habilitar tabulações entre formas](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
