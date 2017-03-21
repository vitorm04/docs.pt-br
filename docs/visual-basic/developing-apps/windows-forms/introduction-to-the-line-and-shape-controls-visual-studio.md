---
title: "Introdução aos controles de linha e forma (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Line control, overview
- Shape control, overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5d168d01c1c0db122b2e0dbeac81df9f5eae461f
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Introdução aos controles de linha e forma (Visual Studio)
Os controles do Visual Basic Power Packs linha e forma são um conjunto de três controles gráficos que lhe permitem desenhar linhas e formas em formulários e contêineres. O <xref:Microsoft.VisualBasic.PowerPacks.LineShape>controle é usado para desenhar linhas horizontais, verticais e diagonais.</xref:Microsoft.VisualBasic.PowerPacks.LineShape> O <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>controle é usado para desenhar círculos e elipses e o <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>controle é usado para desenhar retângulos e quadrados.</xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
  
## <a name="line-and-shape-controls"></a>Controles de linha e forma  
 Controles de linha e forma encapsulam muitos dos métodos gráficos contidos no <xref:System.Drawing>namespace.</xref:System.Drawing> Isso permite que você desenhar linhas e formas em uma única etapa sem ter de criar objetos gráficos, canetas e pincéis. Técnicas de elementos gráficos complexos, como preenchimentos com gradiente podem ser feitas definindo apenas algumas propriedades.  
  
 Embora também seja possível desenhar linhas e formas usando métodos gráficos, há diversas vantagens em usar os controles de linha e forma:  
  
-   Métodos gráficos podem ser chamados somente em tempo de execução. Controles de linha e forma podem ser adicionados a um formulário em tempo de design. Isso permite que você veja sua aparência e posicioná-los; Eles também podem ser adicionados em tempo de execução.  
  
-   Controles de linha e forma podem ser selecionados em tempo de execução, fornecendo eventos, como <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click>e <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>.</xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A> </xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> As saídas de métodos gráficos não podem ser selecionadas e não fornecer eventos.  
  
-   Controles de linha e forma fornecem <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A>e <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A>métodos que permitem que você controle a ordem z em tempo de design e tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> </xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> A ordem z de métodos gráficos pode ser controlada apenas alterando a ordem de execução em tempo de execução.  
  
-   Controles de linha e forma são controles sem janelas. eles têm nenhum identificador de janela e, portanto, usar menos recursos do sistema.  
  
### <a name="object-model"></a>Modelo de objeto  
 Controles de linha e forma derivam de uma base de <xref:Microsoft.VisualBasic.PowerPacks.Shape>classe que define suas propriedades, métodos e eventos.</xref:Microsoft.VisualBasic.PowerPacks.Shape>  
  
 A ilustração a seguir mostra a hierarquia de objetos de linha e forma.  
  
 ![Um diagrama da hierarquia de objetos de linha e forma](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Hierarquia de objeto de linha e forma  
  
 Derivado <xref:Microsoft.VisualBasic.PowerPacks.LineShape>classe contém propriedades, métodos e eventos que são exclusivos para linhas.</xref:Microsoft.VisualBasic.PowerPacks.LineShape> Derivado <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>classe é a classe base para <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; ele contém propriedades, métodos e eventos comuns a todas as formas.</xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape> </xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> Você também pode derivar de <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>para criar seu próprio `Shape` controles.</xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>classes podem ser usadas para desenhar círculos, elipses, retângulos e retângulos com cantos arredondados.</xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
  
 Quando um controle de linha ou de forma é adicionado a um formulário ou contêiner, um invisível <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>objeto é criado.</xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> O <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>atua como uma tela para as formas dentro de cada controle de contêiner; cada <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>tem um correspondente <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection>que permite que você percorrer os controles de linha e forma.</xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> </xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> </xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> Você pode mover formas de um contêiner para outro usando recortar e colar ou arrastar e soltar. Quando a última forma é removida de um contêiner, o <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>é removida também.</xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>  
  
> [!NOTE]
>  Nem todos os controles de contêiner oferecer suporte os controles de linha e forma. Você não pode hospedar um controle de forma ou de linha em um <xref:System.Windows.Forms.TableLayoutPanel>ou <xref:System.Windows.Forms.FlowLayoutPanel>.</xref:System.Windows.Forms.FlowLayoutPanel> </xref:System.Windows.Forms.TableLayoutPanel>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks></xref:Microsoft.VisualBasic.PowerPacks>   
 [Como: desenhar linhas com o controle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)   
 [Como: desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)   
 [Como habilitar tabulações entre formas](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
