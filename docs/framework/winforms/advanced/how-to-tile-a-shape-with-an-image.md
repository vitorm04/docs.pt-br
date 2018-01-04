---
title: "Como preencher uma forma com instâncias de uma imagem organizadas lado a lado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8726322e9443042b76c28e7b4b22ebc51c871bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-tile-a-shape-with-an-image"></a>Como preencher uma forma com instâncias de uma imagem organizadas lado a lado
Da mesma forma que blocos podem ser colocados lado a lado para recobrir um piso, imagens retangulares podem ser colocadas umas ao lado das outras para preencher (organizar lado a lado) uma forma. Para organizar o interior de uma forma lado a lado, use um pincel de textura. Quando você cria um <xref:System.Drawing.TextureBrush> do objeto, um dos argumentos que você passa para o construtor é um <xref:System.Drawing.Image> objeto. Quando você usa o pincel de textura para pintar o interior de uma forma, ela será preenchida com repetidas cópias dessa imagem.  
  
 A propriedade de modo de quebra automática do <xref:System.Drawing.TextureBrush> objeto determina como a imagem é orientado por conforme ele é repetido em uma grade retangular. Você pode fazer todos os blocos na grade terem a mesma orientação ou fazer com que a imagem fique invertida de uma posição de grade para a próxima. A inversão pode ser horizontal, vertical ou ambas. Os exemplos a seguir demonstram organização lado a lado com tipos diferentes de inversão.  
  
### <a name="to-tile-an-image"></a>Organizar uma imagem lado a lado  
  
-   Este exemplo usa a imagem de 75 × 75 a seguir para organização lado a lado em um retângulo de 200 × 200.  
  
 ![Bloco 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")  
  
-   A ilustração a seguir mostra como o retângulo é organizado lado a lado com a imagem. Observe que todos os blocos têm a mesma orientação; não há nenhum inversão.  
  
 ![Bloco 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>Inverter uma imagem horizontalmente com organização lado a lado  
  
-   Este exemplo usa a mesma imagem de 75 × 75 para preencher um retângulo 200 × 200. O modo de encapsulamento é definido para inverter a imagem horizontalmente. A ilustração a seguir mostra como o retângulo é organizado lado a lado com a imagem. Observe que, ao mudar de um bloco para o próximo em uma determinada linha, a imagem é invertida horizontalmente.  
  
 ![Bloco 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>Inverter uma imagem verticalmente com organização lado a lado  
  
-   Este exemplo usa a mesma imagem de 75 × 75 para preencher um retângulo 200 × 200. O modo de encapsulamento é definido para inverter a imagem verticalmente.  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>Inverter uma imagem horizontalmente e verticalmente com organização lado a lado  
  
-   Este exemplo usa a mesma imagem de 75 × 75 para organizar lado a lado um retângulo de 200 × 200. O modo de encapsulamento é definido para inverter a imagem tanto horizontalmente quanto verticalmente. A ilustração a seguir mostra como o retângulo é organizado lado a lado pela imagem. Observe que, ao mudar de um bloco para o próximo em uma determinada linha, a imagem é invertida horizontalmente e, ao mudar de um bloco para o próximo em uma determinada coluna, a imagem é invertida verticalmente.  
  
 ![Bloco 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Consulte também  
 [Usando um pincel para preencher formas](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
