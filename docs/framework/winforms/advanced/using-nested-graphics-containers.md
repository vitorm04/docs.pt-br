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
ms.openlocfilehash: 4533fbba62c36714f55cd8bd55fde7a1c8f6c9e6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505049"
---
# <a name="using-nested-graphics-containers"></a>Usando contêineres de elementos gráficos aninhados
GDI+ fornece contêineres que você pode usar para substituir ou aumentar a parte do estado no temporariamente um <xref:System.Drawing.Graphics> objeto. Criar um contêiner chamando o <xref:System.Drawing.Graphics.BeginContainer%2A> método de um <xref:System.Drawing.Graphics> objeto. Você pode chamar <xref:System.Drawing.Graphics.BeginContainer%2A> repetidamente para formar contêineres aninhados. Cada chamada para <xref:System.Drawing.Graphics.BeginContainer%2A> deve ser emparelhado com uma chamada para <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>Transformações em contêineres aninhados  
 O exemplo a seguir cria uma <xref:System.Drawing.Graphics> objeto e um contêiner dentro desse <xref:System.Drawing.Graphics> objeto. A transformação global do <xref:System.Drawing.Graphics> objeto é uma translação 100 unidades na direção x e 80 unidades na direção y. A transformação global do contêiner é uma rotação de 30 graus. O código faz a chamada `DrawRectangle(pen, -60, -30, 120, 60)` duas vezes. A primeira chamada para <xref:System.Drawing.Graphics.DrawRectangle%2A> está dentro do contêiner; ou seja, a chamada está entre as chamadas para <xref:System.Drawing.Graphics.BeginContainer%2A> e <xref:System.Drawing.Graphics.EndContainer%2A>. A segunda chamada para <xref:System.Drawing.Graphics.DrawRectangle%2A> após a chamada para <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 No código anterior, o retângulo desenhado de dentro do contêiner é transformado primeiro pela transformação global do contêiner (rotação) e, em seguida, pela transformação global do <xref:System.Drawing.Graphics> objeto (conversão). O retângulo desenhado de fora do contêiner é transformado apenas pela transformação global do <xref:System.Drawing.Graphics> objeto (conversão). A ilustração a seguir mostra os dois retângulos: 
  
 ![Ilustração que mostra contêineres aninhados.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>Recorte em contêineres aninhados  
 O exemplo a seguir demonstra como contêineres aninhados lidam com áreas de recorte. O código cria uma <xref:System.Drawing.Graphics> objeto e um contêiner dentro desse <xref:System.Drawing.Graphics> objeto. A região de recorte do <xref:System.Drawing.Graphics> objeto é um retângulo e a região de recorte do contêiner é uma elipse. O código faz duas chamadas para o <xref:System.Drawing.Graphics.DrawLine%2A> método. A primeira chamada para <xref:System.Drawing.Graphics.DrawLine%2A> está dentro do contêiner e a segunda chamada para <xref:System.Drawing.Graphics.DrawLine%2A> está fora do contêiner (após a chamada para <xref:System.Drawing.Graphics.EndContainer%2A>). A primeira linha é recortada pela interseção das duas áreas de recorte. A segunda linha é recortada apenas pela região de recorte retangular do <xref:System.Drawing.Graphics> objeto.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 A ilustração a seguir mostra as duas linhas recortadas:
  
 ![Ilustração que mostra um contêiner aninhado com linhas recortadas.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 Como os dois exemplos anteriores mostram, as transformações e áreas de recorte são cumulativas em contêineres aninhados. Se você definir as transformações globais do contêiner e o <xref:System.Drawing.Graphics> do objeto, as duas transformações se aplicarão a itens desenhados de dentro do contêiner. A transformação do contêiner será aplicado primeiro e a transformação do <xref:System.Drawing.Graphics> objeto será aplicado depois. Se você definir as regiões de recorte do contêiner e o <xref:System.Drawing.Graphics> do objeto, itens desenhados de dentro do contêiner serão recortados pela interseção das duas áreas de recorte.  
  
## <a name="quality-settings-in-nested-containers"></a>Configurações de qualidade em contêineres aninhados  
 Configurações de qualidade (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>e assim por diante) em contêineres aninhados não são cumulativos; em vez disso, as configurações de qualidade do contêiner substituem temporariamente as configurações de qualidade de uma <xref:System.Drawing.Graphics> objeto. Quando você cria um novo contêiner, as configurações de qualidade do contêiner são definidas com valores padrão. Por exemplo, suponha que você tenha um <xref:System.Drawing.Graphics> objeto com um modo de suavização de <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Quando você cria um contêiner, o modo de suavização dentro do contêiner é o modo de suavização padrão. Você tem a liberdade de definir o modo de suavização do contêiner e os itens desenhados de dentro do contêiner serão desenhados de acordo com o modo é definido por você. Itens desenhados após a chamada para <xref:System.Drawing.Graphics.EndContainer%2A> serão desenhados de acordo com o modo de suavização (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) que estava em vigor antes da chamada para <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Várias camadas de contêineres aninhados  
 Você não está limitado a um contêiner em um <xref:System.Drawing.Graphics> objeto. É possível criar uma sequência de contêineres, cada um deles aninhado no anterior e é possível especificar a transformação global, a área de recorte e as configurações de qualidade de cada um desses contêineres aninhados. Se você chamar um método de desenho de dentro do contêiner mais interno, as transformações serão aplicadas em ordem, começando pelo contêiner mais interno e terminando com mais externo. Itens desenhados de dentro do contêiner mais interno serão recortados pela interseção de todas as áreas de recorte.  
  
 O exemplo a seguir cria uma <xref:System.Drawing.Graphics> do objeto e define sua dica de renderização de texto como <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. O código cria dois contêineres, um aninhado dentro do outro. A dica de renderização de texto do contêiner externo é definida como <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, e a dica de renderização de texto do contêiner interno é definida como <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. O código desenha três cadeias de caracteres: uma do contêiner interno, uma do contêiner externo e uma do <xref:System.Drawing.Graphics> objeto propriamente dito.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 A ilustração a seguir mostra as três cadeias de caracteres. As cadeias de caracteres desenhadas do contêiner interno e do <xref:System.Drawing.Graphics> objeto são suavizadas pela suavização. A cadeia de caracteres desenhada do contêiner externo não é suavizada pela suavização porque o <xref:System.Drawing.Graphics.TextRenderingHint%2A> estiver definida como <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Ilustração que mostra as cadeias de caracteres extraídas contêineres aninhados.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Graphics>
- [Gerenciando o Estado de um Objeto Gráfico](managing-the-state-of-a-graphics-object.md)
