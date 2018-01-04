---
title: Usando um pincel de gradiente para preencher formas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a84a68f9082d00559938c2710b6574690fa6ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>Usando um pincel de gradiente para preencher formas
Você pode usar um pincel de gradiente para preencher uma forma com uma cor que muda gradualmente. Por exemplo, é possível usar um gradiente horizontal para preencher uma forma com uma cor que muda gradualmente à medida que você move da borda esquerda da forma para a borda direita. Imagine um retângulo com uma borda esquerda preta (representada pelos componentes vermelho, verde e azul 0, 0, 0) e uma borda direita vermelha (representada por 255, 0, 0). Se o retângulo tem 256 pixels de largura, o componente vermelho de um determinado pixel será maior do que o componente vermelho do pixel à esquerda. O pixel mais à esquerda em uma linha tem componentes de cor (0, 0, 0), o segundo pixel tem (1, 0, 0), o terceiro pixel tem (2, 0, 0) e assim por diante, até chegar ao pixel mais à direita, que tem componentes de cor (255, 0, 0). Esses valores de cor interpolados compõem o gradiente de cores.  
  
 Um gradiente linear muda de cor ao mover na horizontal, vertical ou em paralelo para uma linha inclinada especificada. Um gradiente de demarcador muda de cor ao mover sobre o interior e o limite de um demarcador. É possível personalizar gradientes de demarcador para obter uma grande variedade de efeitos.  
  
 A ilustração a seguir mostra um retângulo preenchido com um pincel gradiente linear e uma elipse preenchida com um pincel gradiente de demarcador.  
  
 ![Gradiente](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como Criar um Gradiente Linear](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 Mostra como criar um gradiente linear usando a <xref:System.Drawing.Drawing2D.LinearGradientBrush> classe.  
  
 [Como Criar um Gradiente de Caminho](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 Descreve como criar um gradiente de caminho usando o <xref:System.Drawing.Drawing2D.PathGradientBrush> classe.  
  
 [Como Aplicar Correção Gama a um Gradiente](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 Explica como usar correção gama com um pincel de gradiente.  
  
## <a name="reference"></a>Referência  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 Contém uma descrição dessa classe e tem links para todos os seus membros.  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 Contém uma descrição dessa classe e tem links para todos os seus membros.
