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
ms.openlocfilehash: d1e7e6eac775ca779fb68605adcc9bc2b9915e49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182450"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Gerenciando o estado de um objeto gráfico
A <xref:System.Drawing.Graphics> classe está no coração do GDI+. Para desenhar qualquer coisa, você obtém <xref:System.Drawing.Graphics> um objeto, <xref:System.Drawing.Graphics.DrawLine%2A> <xref:System.Drawing.Graphics.DrawImage%2A>define <xref:System.Drawing.Graphics.DrawString%2A>suas propriedades e chama seus métodos, e afins).  
  
 O exemplo a <xref:System.Drawing.Graphics.DrawRectangle%2A> seguir <xref:System.Drawing.Graphics> chama o método de um objeto. O primeiro argumento <xref:System.Drawing.Graphics.DrawRectangle%2A> passado para <xref:System.Drawing.Pen> o método é um objeto.  
  
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
 Um <xref:System.Drawing.Graphics> objeto faz mais do que <xref:System.Drawing.Graphics.DrawLine%2A> fornecer <xref:System.Drawing.Graphics.DrawRectangle%2A>métodos de desenho, como e . Um <xref:System.Drawing.Graphics> objeto também mantém o estado gráfico, que pode ser dividido nas seguintes categorias:  
  
- Configurações de qualidade  
  
- Transformações  
  
- Área de recorte  
  
### <a name="quality-settings"></a>Configurações de Qualidade  
 Um <xref:System.Drawing.Graphics> objeto tem várias propriedades que influenciam a qualidade dos itens que são desenhados. Por exemplo, você <xref:System.Drawing.Graphics.TextRenderingHint%2A> pode definir a propriedade para especificar o tipo de antialiasing (se houver) aplicado ao texto. Outras propriedades que <xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.CompositingMode%2A>influenciam <xref:System.Drawing.Graphics.InterpolationMode%2A>a qualidade são, e <xref:System.Drawing.Graphics.CompositingQuality%2A>.  
  
 O exemplo a seguir desenha duas elipses, <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> uma com o modo <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>de suavização definido e outra com o modo de suavização definido para:  
  
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
 Um <xref:System.Drawing.Graphics> objeto mantém duas transformações (mundo e página) que são <xref:System.Drawing.Graphics> aplicadas a todos os itens desenhados por esse objeto. Qualquer transformação afim pode ser armazenada na transformação global. Transformações afins incluem colocação em escala, rotação, reflexão, distorção e translação. A transformação de página pode ser usada para colocação em escala e para alterar unidades (por exemplo, pixels em polegadas). Para obter mais informações, consulte [Sistemas de Coordenadas e Transformações](coordinate-systems-and-transformations.md).  
  
 O exemplo a seguir define o <xref:System.Drawing.Graphics> mundo e as transformações de página de um objeto. A transformação global é definida com uma rotação de 30 graus. A transformação da página é definida para <xref:System.Drawing.Graphics.DrawEllipse%2A> que as coordenadas passadas para a segunda sejam tratadas como milímetros em vez de pixels. O código faz duas <xref:System.Drawing.Graphics.DrawEllipse%2A> chamadas idênticas ao método. A transformação mundial é <xref:System.Drawing.Graphics.DrawEllipse%2A> aplicada à primeira chamada, e ambas as transformações <xref:System.Drawing.Graphics.DrawEllipse%2A> (mundo e página) são aplicadas à segunda chamada.  
  
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
  
 ![Ilustração que mostra duas elipses: rotação e largura da caneta.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Área de recorte  
 Um <xref:System.Drawing.Graphics> objeto mantém uma região de recorte que <xref:System.Drawing.Graphics> se aplica a todos os itens desenhados por esse objeto. Você pode definir a região <xref:System.Drawing.Graphics.SetClip%2A> de recorte chamando o método.  
  
 O exemplo a seguir cria uma região em forma de mais (+), formando a união de dois retângulos. Essa região é designada como a <xref:System.Drawing.Graphics> região de recorte de um objeto. Em seguida, o código desenha duas linhas restritas ao interior da área de recorte.  
  
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
  
 A ilustração a seguir mostra as linhas cortadas:  
  
 ![Diagrama que mostra a região do clipe limitado.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Confira também

- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Usando Contêineres de Elementos Gráficos Aninhados](using-nested-graphics-containers.md)
