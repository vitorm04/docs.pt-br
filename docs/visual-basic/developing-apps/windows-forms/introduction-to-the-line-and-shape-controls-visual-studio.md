---
title: "Introdu&#231;&#227;o aos controles de linha e forma (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Controle de linha, visão geral"
  - "linhas, desenho"
  - "Controle de forma, visão geral"
  - "formas, desenho"
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Introdu&#231;&#227;o aos controles de linha e forma (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os controles de linha de Power Packs Visual Basic e forma são um conjunto de três controles gráficos que lhe permitem desenhar linhas e formas em formulários e contêineres.  O <xref:Microsoft.VisualBasic.PowerPacks.LineShape> controle é usado para desenhar linhas horizontais, verticais e diagonais.  O <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> controle é usado para desenhar círculos e elipses e o <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controle é usado para desenhar retângulos e quadrados.  
  
## Linha e controles de forma  
 Controles de linha e forma encapsulam muitos dos métodos que estão contidos em elementos gráficos do <xref:System.Drawing> espaço para nome.  Isso permite que você desenhe linhas e formas numa única etapa sem precisar criar objetos gráficos, pincéis e canetas.  Técnicas de elementos gráficos complexos, como preenchimentos de gradiente podem ser feitas definindo\-se apenas algumas propriedades.  
  
 Embora também seja possível desenhar linhas e formas usando métodos gráficos, existem diversas vantagens em usar os controles de linha e forma:  
  
-   Métodos gráficos podem ser chamados apenas em tempo de execução.  Os controles de linha e forma podem ser adicionados a um formulário em tempo de design.  Isso permite que você pode ver sua aparência e posicioná\-los; Eles também podem ser adicionados em tempo de execução.  
  
-   Controles de linha e forma são selecionáveis em tempo de execução, fornecendo eventos como <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> e <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>.  As saídas de métodos gráficos não são selecionáveis e não fornecem eventos.  
  
-   Os controles de linha e forma fornecem <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> e <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> métodos que permitem controlar a ordem z em tempo de design e em tempo de execução.  A ordem z de métodos gráficos pode ser controlada somente alterando a ordem de execução em tempo de execução.  
  
-   Os controles de linha e forma são controles sem janelas. eles têm alças nenhuma janela e, portanto, usam menos recursos do sistema.  
  
### Modelo de objeto  
 Controles de linha e forma derivam de uma base de <xref:Microsoft.VisualBasic.PowerPacks.Shape> classe que define suas propriedades compartilhadas, métodos e eventos.  
  
 A ilustração a seguir mostra a hierarquia de objeto de linha e forma.  
  
 ![Um diagrama da hierarquia de objetos de linha e forma](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Hierarquia de objetos de linha e forma  
  
 O derivado <xref:Microsoft.VisualBasic.PowerPacks.LineShape> classe contém propriedades, métodos e eventos que são exclusivos de linhas.  O derivado <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> classe é a classe base para <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; Ele contém as propriedades, métodos e eventos comuns a todas as formas.  Você também pode derivar de <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> para criar seu próprio `Shape` controles.  
  
 O <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> e <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> classes podem ser usadas para desenhar círculos, elipses, retângulos e retângulos com cantos arredondados.  
  
 Quando um controle de linha ou forma é adicionado a um formulário ou recipiente, um invisível <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> objeto é criado.  O <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> age como uma tela para as formas dentro de cada controle de recipiente. cada <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> tem um correspondente <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> que lhe permite fazer uma iteração através dos controles de linha e forma.  Você pode mover as formas de um recipiente para outro por meio de recortar e colar ou arrastando e soltando.  Quando a última forma é removida de um recipiente, o <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> é removido também.  
  
> [!NOTE]
>  Nem todos os controles de contêiner oferecem suporte os controles de linha e forma.  Você não pode hospedar um controle de linha ou forma em um <xref:System.Windows.Forms.TableLayoutPanel> ou um <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks>   
 [Como desenhar linhas com o controle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)   
 [Como desenhar formas com os controles OvalShape e RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)   
 [Como habilitar tabulações entre formas](../Topic/How%20to:%20Enable%20Tabbing%20Between%20Shapes%20\(Visual%20Studio\).md)