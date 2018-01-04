---
title: Como renderizar imagens com o GDI+
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
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a6edc48c93f83611bdc2be5b7398ab0abe843407
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-render-images-with-gdi"></a>Como renderizar imagens com o GDI+
Você pode usar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para renderizar imagens que existem como arquivos em seus aplicativos. Isso é feito criando um novo objeto de um <xref:System.Drawing.Image> classe (como <xref:System.Drawing.Bitmap>), criando um <xref:System.Drawing.Graphics> do objeto que se refere à superfície de desenho que você deseja usar e, em seguida, chamar o <xref:System.Drawing.Graphics.DrawImage%2A> método do <xref:System.Drawing.Graphics> objeto. A imagem será pintada na superfície de desenho representada pela classe de elementos gráficos. Você pode usar o Editor de imagens para criar e editar arquivos de imagem no momento de design e renderizá-los com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] no tempo de execução. Para obter mais informações, consulte [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Para renderizar uma imagem com o GDI+  
  
1.  Crie um objeto que representa a imagem que deseja exibir. Este objeto deve ser um membro de uma classe que herda de <xref:System.Drawing.Image>, como <xref:System.Drawing.Bitmap> ou <xref:System.Drawing.Imaging.Metafile>. Um exemplo é exibido:  
  
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
  
2.  Criar um <xref:System.Drawing.Graphics> objeto que representa a superfície de desenho que você deseja usar. Para obter mais informações, consulte, [Como criar objetos gráficos para desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3.  Chamar o <xref:System.Drawing.Graphics.DrawImage%2A> de seu objeto de gráfico para processar a imagem. Especifique a imagem a ser desenhada e as coordenadas na qual ela deve ser desenhada.  
  
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
 [Introdução à Programação de Elementos Gráficos](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Como Criar Objetos Gráficos para Desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Canetas, Linhas e Retângulos no GDI+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [Como desenhar texto em um Windows Forms](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Desenhando linhas ou figuras fechadas](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons)
