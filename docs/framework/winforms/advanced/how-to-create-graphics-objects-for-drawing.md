---
title: Como criar objetos gráficos para desenho
description: Aprenda agora a criar um objeto gráfico de que você precisa para desenhar linhas e formas, renderizar texto ou exibir e manipular imagens com o GDI+.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 1a0884c1e9956dc6f4608e32372deeea24ef4670
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903201"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="fb66f-103">Como criar objetos gráficos para desenho</span><span class="sxs-lookup"><span data-stu-id="fb66f-103">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="fb66f-104">Antes de poder desenhar linhas e formas, renderizar texto ou exibir e manipular imagens com o GDI+, você precisa criar um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="fb66f-104">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="fb66f-105">O <xref:System.Drawing.Graphics> objeto representa uma superfície de desenho de GDI+ e é o objeto usado para criar imagens gráficas.</span><span class="sxs-lookup"><span data-stu-id="fb66f-105">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="fb66f-106">Há duas etapas ao trabalhar com gráficos:</span><span class="sxs-lookup"><span data-stu-id="fb66f-106">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="fb66f-107">Criando um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="fb66f-107">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="fb66f-108">Usando o <xref:System.Drawing.Graphics> objeto para desenhar linhas e formas, renderizar texto ou exibir e manipular imagens.</span><span class="sxs-lookup"><span data-stu-id="fb66f-108">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="fb66f-109">Criando um objeto gráfico</span><span class="sxs-lookup"><span data-stu-id="fb66f-109">Creating a Graphics Object</span></span>  
 <span data-ttu-id="fb66f-110">Um objeto gráfico pode ser criado de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="fb66f-110">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="fb66f-111">Para criar um objeto gráfico</span><span class="sxs-lookup"><span data-stu-id="fb66f-111">To create a graphics object</span></span>  
  
- <span data-ttu-id="fb66f-112">Receber uma referência a um objeto de gráfico como parte do <xref:System.Windows.Forms.PaintEventArgs> no <xref:System.Windows.Forms.Control.Paint> caso de um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="fb66f-112">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="fb66f-113">Geralmente é assim que você obtém uma referência a um objeto gráfico ao criar código de pintura para um controle.</span><span class="sxs-lookup"><span data-stu-id="fb66f-113">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="fb66f-114">Da mesma forma, você também pode obter um objeto gráfico como uma propriedade do <xref:System.Drawing.Printing.PrintPageEventArgs> ao manipular o <xref:System.Drawing.Printing.PrintDocument.PrintPage> evento para um <xref:System.Drawing.Printing.PrintDocument> .</span><span class="sxs-lookup"><span data-stu-id="fb66f-114">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="fb66f-115">-ou-</span><span class="sxs-lookup"><span data-stu-id="fb66f-115">-or-</span></span>  
  
- <span data-ttu-id="fb66f-116">Chame o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método de um controle ou formulário para obter uma referência a um <xref:System.Drawing.Graphics> objeto que representa a superfície de desenho desse controle ou formulário.</span><span class="sxs-lookup"><span data-stu-id="fb66f-116">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="fb66f-117">Use esse método se quiser desenhar em um formulário ou controle que já exista.</span><span class="sxs-lookup"><span data-stu-id="fb66f-117">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="fb66f-118">-ou-</span><span class="sxs-lookup"><span data-stu-id="fb66f-118">-or-</span></span>  
  
- <span data-ttu-id="fb66f-119">Crie um <xref:System.Drawing.Graphics> objeto de qualquer objeto que herde de <xref:System.Drawing.Image> .</span><span class="sxs-lookup"><span data-stu-id="fb66f-119">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="fb66f-120">Essa abordagem é útil quando você quer alterar uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="fb66f-120">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="fb66f-121">As seções a seguir dão detalhes sobre cada um desses processos.</span><span class="sxs-lookup"><span data-stu-id="fb66f-121">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="fb66f-122">PaintEventArgs no manipulador de eventos de pintura</span><span class="sxs-lookup"><span data-stu-id="fb66f-122">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="fb66f-123">Ao programar <xref:System.Windows.Forms.PaintEventHandler> para controles ou <xref:System.Drawing.Printing.PrintDocument.PrintPage> para para <xref:System.Drawing.Printing.PrintDocument> , um objeto de gráfico é fornecido como uma das propriedades de <xref:System.Windows.Forms.PaintEventArgs> ou <xref:System.Drawing.Printing.PrintPageEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="fb66f-123">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="fb66f-124">Para obter uma referência a um objeto Gráfico de PaintEventArgs no evento de pintura</span><span class="sxs-lookup"><span data-stu-id="fb66f-124">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="fb66f-125">Declare o <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="fb66f-125">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="fb66f-126">Atribua a variável para se referir ao <xref:System.Drawing.Graphics> objeto passado como parte do <xref:System.Windows.Forms.PaintEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="fb66f-126">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="fb66f-127">Inserir código para pintar o formulário ou o controle.</span><span class="sxs-lookup"><span data-stu-id="fb66f-127">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="fb66f-128">O exemplo a seguir mostra como fazer referência a um <xref:System.Drawing.Graphics> objeto do <xref:System.Windows.Forms.PaintEventArgs> no <xref:System.Windows.Forms.Control.Paint> evento:</span><span class="sxs-lookup"><span data-stu-id="fb66f-128">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,
       System.Windows.Forms.PaintEventArgs pe)
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a><span data-ttu-id="fb66f-129">Método CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="fb66f-129">CreateGraphics Method</span></span>  
 <span data-ttu-id="fb66f-130">Você também pode usar o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método de um controle ou formulário para obter uma referência a um <xref:System.Drawing.Graphics> objeto que representa a superfície de desenho desse controle ou formulário.</span><span class="sxs-lookup"><span data-stu-id="fb66f-130">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="fb66f-131">Para criar um objeto gráfico com o método CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="fb66f-131">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="fb66f-132">Chame o <xref:System.Windows.Forms.Control.CreateGraphics%2A> método do formulário ou controle no qual você deseja renderizar gráficos.</span><span class="sxs-lookup"><span data-stu-id="fb66f-132">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="fb66f-133">Criar de um objeto de imagem</span><span class="sxs-lookup"><span data-stu-id="fb66f-133">Create from an Image Object</span></span>  
 <span data-ttu-id="fb66f-134">Além disso, você pode criar um objeto gráfico a partir de qualquer objeto derivado da <xref:System.Drawing.Image> classe.</span><span class="sxs-lookup"><span data-stu-id="fb66f-134">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="fb66f-135">Para criar um objeto Gráfico de uma imagem</span><span class="sxs-lookup"><span data-stu-id="fb66f-135">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="fb66f-136">Chame o <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> método, fornecendo o nome da variável de imagem da qual você deseja criar um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="fb66f-136">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="fb66f-137">O exemplo a seguir mostra como usar um <xref:System.Drawing.Bitmap> objeto:</span><span class="sxs-lookup"><span data-stu-id="fb66f-137">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
> <span data-ttu-id="fb66f-138">Você só pode criar <xref:System.Drawing.Graphics> objetos de arquivos. bmp não indexados, como arquivos. bmp de 16 bits, 24 bits e 32 bits.</span><span class="sxs-lookup"><span data-stu-id="fb66f-138">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="fb66f-139">Cada pixel dos arquivos .bmp não indexados mantém uma cor, em contraste com pixels de arquivos .bmp indexados, que mantêm um índice para uma tabela de cores.</span><span class="sxs-lookup"><span data-stu-id="fb66f-139">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="fb66f-140">Desenhar e manipular imagens e formas</span><span class="sxs-lookup"><span data-stu-id="fb66f-140">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="fb66f-141">Depois de criado, um <xref:System.Drawing.Graphics> objeto pode ser usado para desenhar linhas e formas, renderizar texto ou exibir e manipular imagens.</span><span class="sxs-lookup"><span data-stu-id="fb66f-141">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="fb66f-142">Os objetos principais usados com o <xref:System.Drawing.Graphics> objeto são:</span><span class="sxs-lookup"><span data-stu-id="fb66f-142">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="fb66f-143">A <xref:System.Drawing.Pen> classe — usada para desenhar linhas, estruturar formas ou renderizar outras representações geométricas.</span><span class="sxs-lookup"><span data-stu-id="fb66f-143">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="fb66f-144">A <xref:System.Drawing.Brush> classe — usada para preencher áreas de elementos gráficos, como formas preenchidas, imagens ou texto.</span><span class="sxs-lookup"><span data-stu-id="fb66f-144">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="fb66f-145">A <xref:System.Drawing.Font> classe — fornece uma descrição de quais formas usar ao renderizar texto.</span><span class="sxs-lookup"><span data-stu-id="fb66f-145">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="fb66f-146">A <xref:System.Drawing.Color> estrutura — representa as diferentes cores a serem exibidas.</span><span class="sxs-lookup"><span data-stu-id="fb66f-146">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="fb66f-147">Para usar o objeto Gráfico que você criou</span><span class="sxs-lookup"><span data-stu-id="fb66f-147">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="fb66f-148">Trabalhe com o objeto apropriado listado acima para desenhar o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="fb66f-148">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="fb66f-149">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="fb66f-149">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="fb66f-150">Para renderizar</span><span class="sxs-lookup"><span data-stu-id="fb66f-150">To render</span></span>|<span data-ttu-id="fb66f-151">Consulte</span><span class="sxs-lookup"><span data-stu-id="fb66f-151">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="fb66f-152">Linhas</span><span class="sxs-lookup"><span data-stu-id="fb66f-152">Lines</span></span>|[<span data-ttu-id="fb66f-153">Como desenhar uma linha em um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb66f-153">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="fb66f-154">Formas</span><span class="sxs-lookup"><span data-stu-id="fb66f-154">Shapes</span></span>|[<span data-ttu-id="fb66f-155">Como desenhar uma forma delineada</span><span class="sxs-lookup"><span data-stu-id="fb66f-155">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="fb66f-156">Texto</span><span class="sxs-lookup"><span data-stu-id="fb66f-156">Text</span></span>|[<span data-ttu-id="fb66f-157">Como desenhar texto em um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb66f-157">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="fb66f-158">Imagens</span><span class="sxs-lookup"><span data-stu-id="fb66f-158">Images</span></span>|[<span data-ttu-id="fb66f-159">Como renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="fb66f-159">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="fb66f-160">Veja também</span><span class="sxs-lookup"><span data-stu-id="fb66f-160">See also</span></span>

- [<span data-ttu-id="fb66f-161">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="fb66f-161">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="fb66f-162">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb66f-162">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="fb66f-163">Linhas, curvas e formas</span><span class="sxs-lookup"><span data-stu-id="fb66f-163">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="fb66f-164">Como renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="fb66f-164">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
