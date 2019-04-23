---
title: 'Como: renderizar imagens com o GDI+'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: e038da545bb3f56cc757710bcaa93aa2c86bfa67
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342538"
---
# <a name="how-to-render-images-with-gdi"></a>Como: renderizar imagens com o GDI+
Você pode usar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para renderizar imagens que existem como arquivos em seus aplicativos. Fazer isso criando um novo objeto de um <xref:System.Drawing.Image> classe (como <xref:System.Drawing.Bitmap>), criando uma <xref:System.Drawing.Graphics> do objeto que se refere à superfície de desenho que deseja usar e, em seguida, chamar o <xref:System.Drawing.Graphics.DrawImage%2A> método da <xref:System.Drawing.Graphics> objeto. A imagem será pintada na superfície de desenho representada pela classe de elementos gráficos. Você pode usar o Editor de imagens para criar e editar arquivos de imagem no momento de design e renderizá-los com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] no tempo de execução. Para obter mais informações, consulte [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Para renderizar uma imagem com o GDI+  
  
1. Crie um objeto que representa a imagem que deseja exibir. Esse objeto deve ser um membro de uma classe que herda de <xref:System.Drawing.Image>, como <xref:System.Drawing.Bitmap> ou <xref:System.Drawing.Imaging.Metafile>. Um exemplo é exibido:  
  
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
  
2. Criar um <xref:System.Drawing.Graphics> objeto que representa a superfície de desenho que deseja usar. Para obter mais informações, confira [Como: Criar objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3. Chamar o <xref:System.Drawing.Graphics.DrawImage%2A> de seu objeto de elementos gráficos para renderizar a imagem. Especifique a imagem a ser desenhada e as coordenadas na qual ela deve ser desenhada.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Introdução à Programação de Elementos Gráficos](getting-started-with-graphics-programming.md)
- [Como: Criar objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md)
- [Canetas, Linhas e Retângulos no GDI+](pens-lines-and-rectangles-in-gdi.md)
- [Como: Desenhar texto em um formulário do Windows](how-to-draw-text-on-a-windows-form.md)
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Desenhando linhas ou figuras fechadas](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons)
