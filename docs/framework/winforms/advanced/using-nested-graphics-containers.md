---
title: Usando contêineres de elementos gráficos aninhados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: ba6bba84100a0ddcc87894710a6d3099ab0ccff5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529055"
---
# <a name="using-nested-graphics-containers"></a>Usando contêineres de elementos gráficos aninhados
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Fornece contêineres que você pode usar para substituir temporariamente ou aumentar a parte do estado de um <xref:System.Drawing.Graphics> objeto. Criar um contêiner chamando o <xref:System.Drawing.Graphics.BeginContainer%2A> método de um <xref:System.Drawing.Graphics> objeto. Você pode chamar <xref:System.Drawing.Graphics.BeginContainer%2A> repetidamente para formar contêineres aninhados. Cada chamada para <xref:System.Drawing.Graphics.BeginContainer%2A> devem estar combinados com uma chamada para <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>Transformações em contêineres aninhados  
 O exemplo a seguir cria um <xref:System.Drawing.Graphics> objeto e um contêiner dentro desse <xref:System.Drawing.Graphics> objeto. A transformação global do <xref:System.Drawing.Graphics> objeto é um unidades de tradução 100 na direção x e 80 na direção y. A transformação global do contêiner é uma rotação de 30 graus. O código faz a chamada `DrawRectangle(pen, -60, -30, 120, 60)` duas vezes. A primeira chamada para <xref:System.Drawing.Graphics.DrawRectangle%2A> está dentro do contêiner; ou seja, a chamada é entre as chamadas para <xref:System.Drawing.Graphics.BeginContainer%2A> e <xref:System.Drawing.Graphics.EndContainer%2A>. A segunda chamada para <xref:System.Drawing.Graphics.DrawRectangle%2A> após a chamada para <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 No código anterior, o retângulo extraído de dentro do contêiner é transformado primeiro pela transformação world do contêiner (rotação) e, em seguida, pela transformação do mundo de <xref:System.Drawing.Graphics> objeto (tradução). O retângulo tirado do contêiner é transformado apenas pela transformação world do <xref:System.Drawing.Graphics> objeto (tradução). A ilustração a seguir mostra os dois retângulos.  
  
 ![Contêineres aninhados](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## <a name="clipping-in-nested-containers"></a>Recorte em contêineres aninhados  
 O exemplo a seguir demonstra como contêineres aninhados lidam com áreas de recorte. O código cria um <xref:System.Drawing.Graphics> objeto e um contêiner dentro desse <xref:System.Drawing.Graphics> objeto. A região de recorte do <xref:System.Drawing.Graphics> objeto é um retângulo e da região de recorte do contêiner é uma elipse. O código faz duas chamadas para o <xref:System.Drawing.Graphics.DrawLine%2A> método. A primeira chamada para <xref:System.Drawing.Graphics.DrawLine%2A> está dentro do contêiner e a segunda chamada para <xref:System.Drawing.Graphics.DrawLine%2A> está fora do contêiner (após a chamada a <xref:System.Drawing.Graphics.EndContainer%2A>). A primeira linha é recortada pela interseção das duas áreas de recorte. A segunda linha é recortada somente por da região de recorte retangular do <xref:System.Drawing.Graphics> objeto.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 A ilustração a seguir mostra as duas linhas recortadas.  
  
 ![Contêiner aninhado](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 Como os dois exemplos anteriores mostram, as transformações e áreas de recorte são cumulativas em contêineres aninhados. Se você definir as transformações de mundo do contêiner e o <xref:System.Drawing.Graphics> do objeto, ambas as transformações serão aplicadas aos itens extraídas de dentro do contêiner. A transformação do contêiner será aplicado primeiro e a transformação do <xref:System.Drawing.Graphics> objeto será aplicado segundo. Se você definir as regiões de recorte do contêiner e o <xref:System.Drawing.Graphics> do objeto, itens extraídas de dentro do contêiner serão recortados pela interseção das regiões de corte de dois.  
  
## <a name="quality-settings-in-nested-containers"></a>Configurações de qualidade em contêineres aninhados  
 Configurações de qualidade (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>e assim por diante) em contêineres aninhados não são cumulativos; em vez disso, as configurações de qualidade do contêiner substituem temporariamente as configurações de qualidade de um <xref:System.Drawing.Graphics> objeto. Quando você cria um novo contêiner, as configurações de qualidade do contêiner são definidas com valores padrão. Por exemplo, suponha que você tenha um <xref:System.Drawing.Graphics> objeto com um modo de suavização de <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Quando você cria um contêiner, o modo de suavização dentro do contêiner é o modo de suavização padrão. Você tem a liberdade de definir o modo de suavização do contêiner e os itens desenhados de dentro do contêiner serão desenhados de acordo com o modo é definido por você. Itens desenhados após a chamada a <xref:System.Drawing.Graphics.EndContainer%2A> será desenhada de acordo com o modo (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) que estava em vigor antes da chamada para <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Várias camadas de contêineres aninhados  
 Você não está limitado a um contêiner em uma <xref:System.Drawing.Graphics> objeto. É possível criar uma sequência de contêineres, cada um deles aninhado no anterior e é possível especificar a transformação global, a área de recorte e as configurações de qualidade de cada um desses contêineres aninhados. Se você chamar um método de desenho de dentro do contêiner mais interno, as transformações serão aplicadas em ordem, começando pelo contêiner mais interno e terminando com mais externo. Itens desenhados de dentro do contêiner mais interno serão recortados pela interseção de todas as áreas de recorte.  
  
 O exemplo a seguir cria um <xref:System.Drawing.Graphics> do objeto e define sua dica de renderização de texto como <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. O código cria dois contêineres, um aninhado dentro do outro. A dica de renderização de texto do contêiner externo está definida como <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, e a dica de renderização de texto do contêiner interno é definida como <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. O código desenha três cadeias de caracteres: entre o contêiner interno, um contêiner externo e um do <xref:System.Drawing.Graphics> objeto propriamente dito.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 A ilustração a seguir mostra as três cadeias de caracteres. As cadeias de caracteres desenhadas do contêiner interno e do <xref:System.Drawing.Graphics> objeto são amenizados pelo suavização. A cadeia de caracteres extraída de contêiner externo não é suavizada por suavização porque o <xref:System.Drawing.Graphics.TextRenderingHint%2A> está definida como <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Contêineres aninhados](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Graphics>  
 [Gerenciando o Estado de um Objeto Gráfico](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)
