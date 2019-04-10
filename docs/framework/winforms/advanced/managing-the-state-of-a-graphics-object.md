---
title: Gerenciando o estado de um objeto gráfico
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: 8fc92bf84def50bed54a054ae634a8a08c8835c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212447"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Gerenciando o estado de um objeto gráfico
O <xref:System.Drawing.Graphics> classe é o cerne da [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Para desenhar qualquer coisa, você deve obter um <xref:System.Drawing.Graphics> do objeto, defina suas propriedades e chamar seus métodos <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>e assim por diante).  
  
 A exemplo a seguir chama o <xref:System.Drawing.Graphics.DrawRectangle%2A> método de um <xref:System.Drawing.Graphics> objeto. O primeiro argumento passado para o <xref:System.Drawing.Graphics.DrawRectangle%2A> método é um <xref:System.Drawing.Pen> objeto.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a>Estado gráfico  
 Um <xref:System.Drawing.Graphics> objeto mais do que fornecer métodos de desenho, como <xref:System.Drawing.Graphics.DrawLine%2A> e <xref:System.Drawing.Graphics.DrawRectangle%2A>. Um <xref:System.Drawing.Graphics> objeto também mantém o estado dos gráficos, que pode ser dividido nas seguintes categorias:  
  
-   Configurações de qualidade  
  
-   Transformações  
  
-   Área de recorte  
  
### <a name="quality-settings"></a>Configurações de Qualidade  
 Um <xref:System.Drawing.Graphics> objeto tem várias propriedades que influenciam a qualidade dos itens que são desenhadas. Por exemplo, você pode definir o <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriedade para especificar o tipo de suavização (se houver) aplicado ao texto. Outras propriedades que influenciam a qualidade são <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, e <xref:System.Drawing.Graphics.InterpolationMode%2A>.  
  
 O exemplo a seguir desenha duas elipses, uma com o modo de suavização definido como <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> e outra com o modo de suavização definido como <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a>Transformações  
 Um <xref:System.Drawing.Graphics> objeto mantém duas transformações (global e página) que são aplicadas a todos os itens desenhados por esse <xref:System.Drawing.Graphics> objeto. Qualquer transformação afim pode ser armazenada na transformação global. Transformações afins incluem colocação em escala, rotação, reflexão, distorção e translação. A transformação de página pode ser usada para colocação em escala e para alterar unidades (por exemplo, pixels em polegadas). Para obter mais informações, consulte [Sistemas de Coordenadas e Transformações](coordinate-systems-and-transformations.md).  
  
 O exemplo a seguir define as transformações global e de página de um <xref:System.Drawing.Graphics> objeto. A transformação global é definida com uma rotação de 30 graus. A transformação de página é definida para que as coordenadas passadas para o segundo <xref:System.Drawing.Graphics.DrawEllipse%2A> serão tratadas como milímetros em vez de pixels. O código faz duas chamadas idênticas para o <xref:System.Drawing.Graphics.DrawEllipse%2A> método. A transformação global é aplicada ao primeiro <xref:System.Drawing.Graphics.DrawEllipse%2A> de chamada e as duas transformações (global e página) são aplicadas à segunda <xref:System.Drawing.Graphics.DrawEllipse%2A> chamar.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 A ilustração a seguir mostra as duas elipses. Observe que a rotação de 30 graus é sobre a origem do sistema de coordenadas (canto superior esquerdo da área de cliente), e não sobre os centros das elipses. Observe também que a largura da caneta de 1 significa 1 pixel para a primeira elipse e 1 milímetro para a segunda elipse.  
  
 ![Ilustração que mostra duas elipses: largura de rotação e caneta.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Área de recorte  
 Um <xref:System.Drawing.Graphics> objeto mantém uma região de recorte que se aplica a todos os itens desenhados por esse <xref:System.Drawing.Graphics> objeto. Você pode definir a região de recorte chamando o <xref:System.Drawing.Graphics.SetClip%2A> método.  
  
 O exemplo a seguir cria uma região em forma de mais (+), formando a união de dois retângulos. Essa área é designada como a região de recorte de um <xref:System.Drawing.Graphics> objeto. Em seguida, o código desenha duas linhas restritas ao interior da área de recorte.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 A ilustração a seguir mostra as linhas recortadas:  
  
 ![Diagrama que mostra a região de recorte limitada.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Consulte também

- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Usando contêineres de elementos gráficos aninhados](using-nested-graphics-containers.md)
