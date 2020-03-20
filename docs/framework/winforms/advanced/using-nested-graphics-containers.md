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
ms.openlocfilehash: 460ebb37ee62691a1e282f756840121fd378ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182471"
---
# <a name="using-nested-graphics-containers"></a>Usando contêineres de elementos gráficos aninhados
O GDI+ fornece recipientes que você pode usar para substituir <xref:System.Drawing.Graphics> ou aumentar temporariamente parte do estado em um objeto. Você cria um recipiente <xref:System.Drawing.Graphics.BeginContainer%2A> chamando <xref:System.Drawing.Graphics> o método de um objeto. Você pode <xref:System.Drawing.Graphics.BeginContainer%2A> ligar repetidamente para formar recipientes aninhados. Cada chamada <xref:System.Drawing.Graphics.BeginContainer%2A> deve ser emparelhada <xref:System.Drawing.Graphics.EndContainer%2A>com uma chamada para .  
  
## <a name="transformations-in-nested-containers"></a>Transformações em contêineres aninhados  
 O exemplo a <xref:System.Drawing.Graphics> seguir cria um <xref:System.Drawing.Graphics> objeto e um contêiner dentro desse objeto. A transformação <xref:System.Drawing.Graphics> mundial do objeto é uma tradução de 100 unidades na direção x e 80 unidades na direção y. A transformação global do contêiner é uma rotação de 30 graus. O código faz a chamada `DrawRectangle(pen, -60, -30, 120, 60)` duas vezes. A primeira <xref:System.Drawing.Graphics.DrawRectangle%2A> chamada para é dentro do recipiente; ou seja, a chamada está <xref:System.Drawing.Graphics.BeginContainer%2A> entre <xref:System.Drawing.Graphics.EndContainer%2A>as chamadas para e . A segunda <xref:System.Drawing.Graphics.DrawRectangle%2A> chamada é depois <xref:System.Drawing.Graphics.EndContainer%2A>da chamada para .  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 No código anterior, o retângulo extraído de dentro do recipiente é transformado primeiro pela transformação mundial <xref:System.Drawing.Graphics> do recipiente (rotação) e, em seguida, pela transformação mundial do objeto (tradução). O retângulo extraído de fora do recipiente é transformado <xref:System.Drawing.Graphics> apenas pela transformação mundial do objeto (tradução). A ilustração a seguir mostra os dois retângulos:
  
 ![Ilustração que mostra recipientes aninhados.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>Recorte em contêineres aninhados  
 O exemplo a seguir demonstra como contêineres aninhados lidam com áreas de recorte. O código <xref:System.Drawing.Graphics> cria um objeto <xref:System.Drawing.Graphics> e um recipiente dentro desse objeto. A região de <xref:System.Drawing.Graphics> recorte do objeto é um retângulo, e a região de recorte do recipiente é uma elipse. O código faz duas <xref:System.Drawing.Graphics.DrawLine%2A> chamadas para o método. A primeira <xref:System.Drawing.Graphics.DrawLine%2A> chamada para é dentro do <xref:System.Drawing.Graphics.DrawLine%2A> contêiner, e a segunda <xref:System.Drawing.Graphics.EndContainer%2A>chamada para é fora do recipiente (após a chamada para ). A primeira linha é recortada pela interseção das duas áreas de recorte. A segunda linha é cortada apenas pela região <xref:System.Drawing.Graphics> de recorte retangular do objeto.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 A ilustração a seguir mostra as duas linhas cortadas:
  
 ![Ilustração que mostra um recipiente aninhado com linhas cortadas.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 Como os dois exemplos anteriores mostram, as transformações e áreas de recorte são cumulativas em contêineres aninhados. Se você definir as transformações mundiais do contêiner e do <xref:System.Drawing.Graphics> objeto, ambas as transformações se aplicarão a itens extraídos de dentro do recipiente. A transformação do recipiente será aplicada primeiro, <xref:System.Drawing.Graphics> e a transformação do objeto será aplicada em segundo lugar. Se você definir as regiões de <xref:System.Drawing.Graphics> recorte do recipiente e do objeto, os itens extraídos de dentro do recipiente serão cortados pelo cruzamento das duas regiões de recorte.  
  
## <a name="quality-settings-in-nested-containers"></a>Configurações de qualidade em contêineres aninhados  
 As configurações<xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.TextRenderingHint%2A>de qualidade (, e afins) em recipientes aninhados não são cumulativas; em vez disso, as configurações de qualidade do <xref:System.Drawing.Graphics> recipiente substituem temporariamente as configurações de qualidade de um objeto. Quando você cria um novo contêiner, as configurações de qualidade do contêiner são definidas com valores padrão. Por exemplo, suponha que você tenha um <xref:System.Drawing.Graphics> objeto com um modo de suavização de <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Quando você cria um contêiner, o modo de suavização dentro do contêiner é o modo de suavização padrão. Você tem a liberdade de definir o modo de suavização do contêiner e os itens desenhados de dentro do contêiner serão desenhados de acordo com o modo é definido por você. Os itens sorteados após <xref:System.Drawing.Graphics.EndContainer%2A> a chamada serão sorteados<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>de acordo com o modo <xref:System.Drawing.Graphics.BeginContainer%2A>de suavização ( ) que estava em vigor antes da chamada para .  
  
## <a name="several-layers-of-nested-containers"></a>Várias camadas de contêineres aninhados  
 Você não está limitado a <xref:System.Drawing.Graphics> um recipiente em um objeto. É possível criar uma sequência de contêineres, cada um deles aninhado no anterior e é possível especificar a transformação global, a área de recorte e as configurações de qualidade de cada um desses contêineres aninhados. Se você chamar um método de desenho de dentro do contêiner mais interno, as transformações serão aplicadas em ordem, começando pelo contêiner mais interno e terminando com mais externo. Itens desenhados de dentro do contêiner mais interno serão recortados pela interseção de todas as áreas de recorte.  
  
 O exemplo a <xref:System.Drawing.Graphics> seguir cria um objeto <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>e define sua dica de renderização de texto para . O código cria dois contêineres, um aninhado dentro do outro. A dica de renderização de <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>texto do recipiente externo está definida para <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>, e o indício de renderização de texto do recipiente interno é definido como . O código desenha três cordas: uma do recipiente interno, uma <xref:System.Drawing.Graphics> do recipiente externo e outra do próprio objeto.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 A ilustração a seguir mostra as três cadeias de caracteres. As cordas retiradas do recipiente <xref:System.Drawing.Graphics> interno e do objeto são suavizadas por antialiasing. A corda extraída do recipiente externo não é <xref:System.Drawing.Graphics.TextRenderingHint%2A> suavizada por <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>antialiasing porque a propriedade está definida como .  
  
 ![Ilustração que mostra as cordas extraídas de recipientes aninhados.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>Confira também

- <xref:System.Drawing.Graphics>
- [Gerenciando o Estado de um Objeto Gráfico](managing-the-state-of-a-graphics-object.md)
