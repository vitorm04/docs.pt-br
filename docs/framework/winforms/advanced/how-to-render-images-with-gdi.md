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
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="2c43a-102">Como renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="2c43a-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="2c43a-103">Você pode usar o GDI+ para renderizar imagens que existem como arquivos em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2c43a-103">You can use GDI+ to render images that exist as files in your applications.</span></span> <span data-ttu-id="2c43a-104">Você faz isso criando um <xref:System.Drawing.Image> novo objeto <xref:System.Drawing.Bitmap>de uma <xref:System.Drawing.Graphics> classe (como), criando um objeto que se <xref:System.Drawing.Graphics.DrawImage%2A> refere <xref:System.Drawing.Graphics> à superfície de desenho que você deseja usar e chamando o método do objeto.</span><span class="sxs-lookup"><span data-stu-id="2c43a-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="2c43a-105">A imagem será pintada na superfície de desenho representada pela classe de elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="2c43a-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="2c43a-106">Você pode usar o Editor de imagens para criar e editar arquivos de imagem na hora do design e renderiza-los com GDI+ em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2c43a-106">You can use the Image Editor to create and edit image files at design time, and render them with GDI+ at run time.</span></span> <span data-ttu-id="2c43a-107">Para obter mais informações, consulte [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="2c43a-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="2c43a-108">Para renderizar uma imagem com o GDI+</span><span class="sxs-lookup"><span data-stu-id="2c43a-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="2c43a-109">Crie um objeto que representa a imagem que deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="2c43a-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="2c43a-110">Este objeto deve ser um membro de <xref:System.Drawing.Image>uma <xref:System.Drawing.Bitmap> classe <xref:System.Drawing.Imaging.Metafile>que herda, como ou .</span><span class="sxs-lookup"><span data-stu-id="2c43a-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="2c43a-111">Um exemplo é exibido:</span><span class="sxs-lookup"><span data-stu-id="2c43a-111">An example is shown:</span></span>  
  
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
  
2. <span data-ttu-id="2c43a-112">Crie <xref:System.Drawing.Graphics> um objeto que represente a superfície de desenho que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="2c43a-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="2c43a-113">Para obter mais informações, consulte, [Como criar objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="2c43a-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
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
  
3. <span data-ttu-id="2c43a-114">Chame <xref:System.Drawing.Graphics.DrawImage%2A> o objeto gráfico para renderizar a imagem.</span><span class="sxs-lookup"><span data-stu-id="2c43a-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="2c43a-115">Especifique a imagem a ser desenhada e as coordenadas na qual ela deve ser desenhada.</span><span class="sxs-lookup"><span data-stu-id="2c43a-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2c43a-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="2c43a-116">See also</span></span>

- [<span data-ttu-id="2c43a-117">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="2c43a-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="2c43a-118">Como Criar Objetos Gráficos para Desenho</span><span class="sxs-lookup"><span data-stu-id="2c43a-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="2c43a-119">Canetas, Linhas e Retângulos no GDI+</span><span class="sxs-lookup"><span data-stu-id="2c43a-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="2c43a-120">Como desenhar texto em um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c43a-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="2c43a-121">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c43a-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="2c43a-122">Desenhando linhas ou figuras fechadas</span><span class="sxs-lookup"><span data-stu-id="2c43a-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="2c43a-123">Editor de imagens para ícones</span><span class="sxs-lookup"><span data-stu-id="2c43a-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
