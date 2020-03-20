---
title: Como criar objetos gráficos para desenho
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
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142427"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="238fe-102">Como criar objetos gráficos para desenho</span><span class="sxs-lookup"><span data-stu-id="238fe-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="238fe-103">Antes de desenhar linhas e formas, renderizar texto ou exibir e manipular <xref:System.Drawing.Graphics> imagens com GDI+, você precisa criar um objeto.</span><span class="sxs-lookup"><span data-stu-id="238fe-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="238fe-104">O <xref:System.Drawing.Graphics> objeto representa uma superfície de desenho GDI+, e é o objeto que é usado para criar imagens gráficas.</span><span class="sxs-lookup"><span data-stu-id="238fe-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="238fe-105">Há duas etapas ao trabalhar com gráficos:</span><span class="sxs-lookup"><span data-stu-id="238fe-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="238fe-106">Criando <xref:System.Drawing.Graphics> um objeto.</span><span class="sxs-lookup"><span data-stu-id="238fe-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="238fe-107">Usando <xref:System.Drawing.Graphics> o objeto para desenhar linhas e formas, renderizar texto ou exibir e manipular imagens.</span><span class="sxs-lookup"><span data-stu-id="238fe-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="238fe-108">Criando um objeto gráfico</span><span class="sxs-lookup"><span data-stu-id="238fe-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="238fe-109">Um objeto gráfico pode ser criado de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="238fe-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="238fe-110">Para criar um objeto gráfico</span><span class="sxs-lookup"><span data-stu-id="238fe-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="238fe-111">Receba uma referência a um objeto <xref:System.Windows.Forms.PaintEventArgs> gráfico <xref:System.Windows.Forms.Control.Paint> como parte do caso de um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="238fe-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="238fe-112">Geralmente é assim que você obtém uma referência a um objeto gráfico ao criar código de pintura para um controle.</span><span class="sxs-lookup"><span data-stu-id="238fe-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="238fe-113">Da mesma forma, você também pode obter <xref:System.Drawing.Printing.PrintPageEventArgs> um objeto <xref:System.Drawing.Printing.PrintDocument.PrintPage> gráfico como <xref:System.Drawing.Printing.PrintDocument>propriedade do ao manipular o evento para um .</span><span class="sxs-lookup"><span data-stu-id="238fe-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="238fe-114">-ou-</span><span class="sxs-lookup"><span data-stu-id="238fe-114">-or-</span></span>  
  
- <span data-ttu-id="238fe-115">Chame <xref:System.Windows.Forms.Control.CreateGraphics%2A> o método de um controle ou <xref:System.Drawing.Graphics> formulário para obter uma referência a um objeto que representa a superfície de desenho desse controle ou forma.</span><span class="sxs-lookup"><span data-stu-id="238fe-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="238fe-116">Use esse método se quiser desenhar em um formulário ou controle que já exista.</span><span class="sxs-lookup"><span data-stu-id="238fe-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="238fe-117">-ou-</span><span class="sxs-lookup"><span data-stu-id="238fe-117">-or-</span></span>  
  
- <span data-ttu-id="238fe-118">Crie <xref:System.Drawing.Graphics> um objeto a partir <xref:System.Drawing.Image>de qualquer objeto que herde .</span><span class="sxs-lookup"><span data-stu-id="238fe-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="238fe-119">Essa abordagem é útil quando você quer alterar uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="238fe-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="238fe-120">As seções a seguir dão detalhes sobre cada um desses processos.</span><span class="sxs-lookup"><span data-stu-id="238fe-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="238fe-121">PaintEventArgs no manipulador de eventos de pintura</span><span class="sxs-lookup"><span data-stu-id="238fe-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="238fe-122">Ao programar <xref:System.Windows.Forms.PaintEventHandler> os controles <xref:System.Drawing.Printing.PrintDocument.PrintPage> ou <xref:System.Drawing.Printing.PrintDocument>para um , um objeto gráfico é <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs>fornecido como uma das propriedades de ou .</span><span class="sxs-lookup"><span data-stu-id="238fe-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="238fe-123">Para obter uma referência a um objeto Gráfico de PaintEventArgs no evento de pintura</span><span class="sxs-lookup"><span data-stu-id="238fe-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="238fe-124">Declare <xref:System.Drawing.Graphics> o objeto.</span><span class="sxs-lookup"><span data-stu-id="238fe-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="238fe-125">Atribuir a variável para <xref:System.Drawing.Graphics> se referir ao <xref:System.Windows.Forms.PaintEventArgs>objeto passado como parte do .</span><span class="sxs-lookup"><span data-stu-id="238fe-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="238fe-126">Inserir código para pintar o formulário ou o controle.</span><span class="sxs-lookup"><span data-stu-id="238fe-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="238fe-127">O exemplo a seguir <xref:System.Drawing.Graphics> mostra como <xref:System.Windows.Forms.PaintEventArgs> referenciar um objeto do <xref:System.Windows.Forms.Control.Paint> evento:</span><span class="sxs-lookup"><span data-stu-id="238fe-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="238fe-128">Método CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="238fe-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="238fe-129">Você também pode <xref:System.Windows.Forms.Control.CreateGraphics%2A> usar o método de um controle <xref:System.Drawing.Graphics> ou formulário para obter uma referência a um objeto que representa a superfície de desenho desse controle ou forma.</span><span class="sxs-lookup"><span data-stu-id="238fe-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="238fe-130">Para criar um objeto gráfico com o método CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="238fe-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="238fe-131">Chame <xref:System.Windows.Forms.Control.CreateGraphics%2A> o método do formulário ou controle sobre o qual você deseja renderizar gráficos.</span><span class="sxs-lookup"><span data-stu-id="238fe-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="238fe-132">Criar de um objeto de imagem</span><span class="sxs-lookup"><span data-stu-id="238fe-132">Create from an Image Object</span></span>  
 <span data-ttu-id="238fe-133">Além disso, você pode criar um objeto gráfico <xref:System.Drawing.Image> a partir de qualquer objeto que deriva da classe.</span><span class="sxs-lookup"><span data-stu-id="238fe-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="238fe-134">Para criar um objeto Gráfico de uma imagem</span><span class="sxs-lookup"><span data-stu-id="238fe-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="238fe-135">Ligue <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> para o método, fornecendo o nome da variável <xref:System.Drawing.Graphics> Imagem a partir da qual você deseja criar um objeto.</span><span class="sxs-lookup"><span data-stu-id="238fe-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="238fe-136">O exemplo a seguir <xref:System.Drawing.Bitmap> mostra como usar um objeto:</span><span class="sxs-lookup"><span data-stu-id="238fe-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="238fe-137">Você só <xref:System.Drawing.Graphics> pode criar objetos a partir de arquivos .bmp não indexados, como arquivos de 16 bits, 24 bits e 32 bits .bmp.</span><span class="sxs-lookup"><span data-stu-id="238fe-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="238fe-138">Cada pixel dos arquivos .bmp não indexados mantém uma cor, em contraste com pixels de arquivos .bmp indexados, que mantêm um índice para uma tabela de cores.</span><span class="sxs-lookup"><span data-stu-id="238fe-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="238fe-139">Desenhar e manipular imagens e formas</span><span class="sxs-lookup"><span data-stu-id="238fe-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="238fe-140">Depois de criado, <xref:System.Drawing.Graphics> um objeto pode ser usado para desenhar linhas e formas, renderizar texto ou exibir e manipular imagens.</span><span class="sxs-lookup"><span data-stu-id="238fe-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="238fe-141">Os principais objetos <xref:System.Drawing.Graphics> usados com o objeto são:</span><span class="sxs-lookup"><span data-stu-id="238fe-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="238fe-142">A <xref:System.Drawing.Pen> classe — usada para desenhar linhas, delinear formas ou renderizar outras representações geométricas.</span><span class="sxs-lookup"><span data-stu-id="238fe-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="238fe-143">A <xref:System.Drawing.Brush> classe — usada para preencher áreas de gráficos, como formas preenchidas, imagens ou texto.</span><span class="sxs-lookup"><span data-stu-id="238fe-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="238fe-144">A <xref:System.Drawing.Font> classe — fornece uma descrição de quais formas usar ao renderizar texto.</span><span class="sxs-lookup"><span data-stu-id="238fe-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="238fe-145">A <xref:System.Drawing.Color> estrutura representa as diferentes cores a serem exibidas.</span><span class="sxs-lookup"><span data-stu-id="238fe-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="238fe-146">Para usar o objeto Gráfico que você criou</span><span class="sxs-lookup"><span data-stu-id="238fe-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="238fe-147">Trabalhe com o objeto apropriado listado acima para desenhar o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="238fe-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="238fe-148">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="238fe-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="238fe-149">Para renderizar</span><span class="sxs-lookup"><span data-stu-id="238fe-149">To render</span></span>|<span data-ttu-id="238fe-150">Consulte</span><span class="sxs-lookup"><span data-stu-id="238fe-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="238fe-151">Linhas</span><span class="sxs-lookup"><span data-stu-id="238fe-151">Lines</span></span>|[<span data-ttu-id="238fe-152">Como desenhar uma linha em um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="238fe-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="238fe-153">Formas</span><span class="sxs-lookup"><span data-stu-id="238fe-153">Shapes</span></span>|[<span data-ttu-id="238fe-154">Como desenhar uma forma delineada</span><span class="sxs-lookup"><span data-stu-id="238fe-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="238fe-155">Texto</span><span class="sxs-lookup"><span data-stu-id="238fe-155">Text</span></span>|[<span data-ttu-id="238fe-156">Como desenhar texto em um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="238fe-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="238fe-157">Imagens</span><span class="sxs-lookup"><span data-stu-id="238fe-157">Images</span></span>|[<span data-ttu-id="238fe-158">Como renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="238fe-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="238fe-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="238fe-159">See also</span></span>

- [<span data-ttu-id="238fe-160">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="238fe-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="238fe-161">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="238fe-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="238fe-162">Linhas, curvas e formas</span><span class="sxs-lookup"><span data-stu-id="238fe-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="238fe-163">Como renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="238fe-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
