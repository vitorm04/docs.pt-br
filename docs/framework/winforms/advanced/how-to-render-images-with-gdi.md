---
title: Como renderizar imagens com o GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: fffe1f1052d7323d234985b7e752866f2e89657d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182509"
---
# <a name="how-to-render-images-with-gdi"></a>Como renderizar imagens com o GDI+
Você pode usar o GDI+ para renderizar imagens que existem como arquivos em seus aplicativos. Você faz isso criando um <xref:System.Drawing.Image> novo objeto <xref:System.Drawing.Bitmap>de uma <xref:System.Drawing.Graphics> classe (como), criando um objeto que se <xref:System.Drawing.Graphics.DrawImage%2A> refere <xref:System.Drawing.Graphics> à superfície de desenho que você deseja usar e chamando o método do objeto. A imagem será pintada na superfície de desenho representada pela classe de elementos gráficos. Você pode usar o Editor de imagens para criar e editar arquivos de imagem na hora do design e renderiza-los com GDI+ em tempo de execução. Para obter mais informações, consulte [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Para renderizar uma imagem com o GDI+  
  
1. Crie um objeto que representa a imagem que deseja exibir. Este objeto deve ser um membro de <xref:System.Drawing.Image>uma <xref:System.Drawing.Bitmap> classe <xref:System.Drawing.Imaging.Metafile>que herda, como ou . Um exemplo é exibido:  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2. Crie <xref:System.Drawing.Graphics> um objeto que represente a superfície de desenho que você deseja usar. Para obter mais informações, consulte, [Como criar objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md).  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3. Chame <xref:System.Drawing.Graphics.DrawImage%2A> o objeto gráfico para renderizar a imagem. Especifique a imagem a ser desenhada e as coordenadas na qual ela deve ser desenhada.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>Confira também

- [Introdução à Programação de Elementos Gráficos](getting-started-with-graphics-programming.md)
- [Como Criar Objetos Gráficos para Desenho](how-to-create-graphics-objects-for-drawing.md)
- [Canetas, Linhas e Retângulos no GDI+](pens-lines-and-rectangles-in-gdi.md)
- [Como desenhar texto em um formulário do Windows Forms](how-to-draw-text-on-a-windows-form.md)
- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Desenhando linhas ou figuras fechadas](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons)
