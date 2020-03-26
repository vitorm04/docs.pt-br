---
title: Três categorias de serviços gráficos
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: fa7391ef0f7170ddb9d9d24aa5a1a03635bf46e0
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291732"
---
# <a name="three-categories-of-graphics-services"></a>Três categorias de serviços gráficos
As ofertas de elementos gráficos no Windows Forms se enquadram nas três categorias amplas a seguir:  
  
- Gráficos vetoriais bidimensionais (2D)  
  
- Imagens  
  
- Tipografia  
  
## <a name="2d-vector-graphics"></a>Gráficos vetoriais 2D  
 Gráficos vetoriais bidimensionais, como linhas, curvas e figuras, são primitivos que são especificados por conjuntos de pontos em um sistema de coordenadas. Por exemplo, uma linha reta é especificada por seus dois pontos de extremidade e um retângulo é especificado por um ponto que indica o local de seu canto superior esquerdo e um par de números fornecendo sua largura e altura. Um demarcador simples é especificado por uma matriz de pontos conectados por linhas retas. Uma spline de Bézier é uma curva sofisticada especificada por quatro pontos de controle.  
  
 O GDI+ fornece classes e estruturas que armazenam informações sobre os próprios primitivos, classes que armazenam informações sobre como os primitivos serão desenhados e classes que realmente fazem o desenho. Por exemplo, <xref:System.Drawing.Rectangle> a estrutura armazena a localização e o tamanho de um retângulo; a <xref:System.Drawing.Pen> classe armazena informações sobre cor da linha, largura de linha e estilo de linha; e <xref:System.Drawing.Graphics> a classe tem métodos para desenhar linhas, retângulos, caminhos e outras figuras. Há também <xref:System.Drawing.Brush> várias classes que armazenam informações sobre como figuras fechadas e caminhos serão preenchidos com cores ou padrões.  
  
 Você pode gravar uma imagem de vetor, que é uma sequência de comandos gráficos, em um metarquivo. O GDI+ <xref:System.Drawing.Imaging.Metafile> fornece a classe para gravar, exibir e salvar metaarquivos. Com <xref:System.Drawing.Imaging.MetafileHeader> as <xref:System.Drawing.Imaging.MetaHeader> classes e classes, você pode inspecionar os dados armazenados em um cabeçalho de metaarquivo.  
  
## <a name="imaging"></a>Imagens  
 Determinados tipos de imagens são difíceis ou impossíveis de exibir com as técnicas de gráficos vetoriais. Por exemplo, as imagens nos botões da barra de ferramentas e as imagens que aparecem como ícones são difíceis de especificar como conjuntos de linhas e curvas. Uma fotografia digital de alta resolução de um estádio lotado é ainda mais difícil criar com técnicas de vetor. Imagens desse tipo são armazenadas como bitmaps, que são matrizes de números que representam as cores de pontos individuais na tela. O GDI+ <xref:System.Drawing.Bitmap> fornece a classe para exibir, manipular e salvar bitmaps.  
  
## <a name="typography"></a>Tipografia  
 Tipografia é a exibição do texto em uma variedade de fontes, tamanhos e estilos. O GDI+ oferece amplo suporte para essa tarefa complexa. Uma das novidades no GDI+ é a antialiasing de subpixel, que dá ao texto renderizado em uma tela LCD uma aparência mais suave.  
  
 Além disso, o Windows Forms oferece a opção de <xref:System.Windows.Forms.TextRenderer> desenhar texto com recursos GDI em sua classe.  
  
## <a name="see-also"></a>Confira também

- [Visão geral de elementos gráficos](graphics-overview-windows-forms.md)
- [Sobre o Código Gerenciado no GDI+](about-gdi-managed-code.md)
- [Usando Classes de Elementos Gráficos Gerenciadas](using-managed-graphics-classes.md)
