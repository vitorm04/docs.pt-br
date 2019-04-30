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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967109"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="1afa7-102">Como: renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="1afa7-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="1afa7-103">Você pode usar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para renderizar imagens que existem como arquivos em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1afa7-103">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render images that exist as files in your applications.</span></span> <span data-ttu-id="1afa7-104">Fazer isso criando um novo objeto de um <xref:System.Drawing.Image> classe (como <xref:System.Drawing.Bitmap>), criando uma <xref:System.Drawing.Graphics> do objeto que se refere à superfície de desenho que deseja usar e, em seguida, chamar o <xref:System.Drawing.Graphics.DrawImage%2A> método da <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="1afa7-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="1afa7-105">A imagem será pintada na superfície de desenho representada pela classe de elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="1afa7-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="1afa7-106">Você pode usar o Editor de imagens para criar e editar arquivos de imagem no momento de design e renderizá-los com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1afa7-106">You can use the Image Editor to create and edit image files at design time, and render them with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] at run time.</span></span> <span data-ttu-id="1afa7-107">Para obter mais informações, consulte [Editor de imagens para ícones](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="1afa7-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="1afa7-108">Para renderizar uma imagem com o GDI+</span><span class="sxs-lookup"><span data-stu-id="1afa7-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="1afa7-109">Crie um objeto que representa a imagem que deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="1afa7-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="1afa7-110">Esse objeto deve ser um membro de uma classe que herda de <xref:System.Drawing.Image>, como <xref:System.Drawing.Bitmap> ou <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="1afa7-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="1afa7-111">Um exemplo é exibido:</span><span class="sxs-lookup"><span data-stu-id="1afa7-111">An example is shown:</span></span>  
  
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
  
2. <span data-ttu-id="1afa7-112">Criar um <xref:System.Drawing.Graphics> objeto que representa a superfície de desenho que deseja usar.</span><span class="sxs-lookup"><span data-stu-id="1afa7-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="1afa7-113">Para obter mais informações, confira [Como: Criar objetos gráficos para desenho](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="1afa7-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
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
  
3. <span data-ttu-id="1afa7-114">Chamar o <xref:System.Drawing.Graphics.DrawImage%2A> de seu objeto de elementos gráficos para renderizar a imagem.</span><span class="sxs-lookup"><span data-stu-id="1afa7-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="1afa7-115">Especifique a imagem a ser desenhada e as coordenadas na qual ela deve ser desenhada.</span><span class="sxs-lookup"><span data-stu-id="1afa7-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1afa7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1afa7-116">See also</span></span>

- [<span data-ttu-id="1afa7-117">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="1afa7-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="1afa7-118">Como: Criar objetos gráficos para desenho</span><span class="sxs-lookup"><span data-stu-id="1afa7-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="1afa7-119">Canetas, Linhas e Retângulos no GDI+</span><span class="sxs-lookup"><span data-stu-id="1afa7-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="1afa7-120">Como: Desenhar texto em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="1afa7-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="1afa7-121">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1afa7-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="1afa7-122">Desenhando linhas ou figuras fechadas</span><span class="sxs-lookup"><span data-stu-id="1afa7-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="1afa7-123">Editor de imagens para ícones</span><span class="sxs-lookup"><span data-stu-id="1afa7-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
