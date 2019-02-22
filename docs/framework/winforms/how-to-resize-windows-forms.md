---
title: 'Como: Redimensionar Formulários do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 57a75cf07e3487c5a115e57c068b412c33538bce
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664530"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="56fb5-102">Como: Redimensionar Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="56fb5-102">How to: Resize Windows Forms</span></span>
<span data-ttu-id="56fb5-103">Você pode especificar o tamanho do seu Windows Forms de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="56fb5-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="56fb5-104">Você pode alterar a altura e a largura do formulário programaticamente, definindo um novo valor para o <xref:System.Windows.Forms.Form.Size%2A> propriedade, ou ajustar a <xref:System.Windows.Forms.Control.Height%2A> ou <xref:System.Windows.Forms.Control.Width%2A> propriedades individualmente.</span><span class="sxs-lookup"><span data-stu-id="56fb5-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="56fb5-105">Se você estiver usando o Visual Studio, você pode alterar o tamanho usando o Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="56fb5-105">If you are using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="56fb5-106">Consulte também [como: Redimensionar Formulários do Windows usando o Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="56fb5-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>  
  
### <a name="to-resize-a-form-programmatically"></a><span data-ttu-id="56fb5-107">Redimensionar um formulário com programação</span><span class="sxs-lookup"><span data-stu-id="56fb5-107">To resize a form programmatically</span></span>  
  
-   <span data-ttu-id="56fb5-108">Definir o tamanho de um formulário em tempo de execução, definindo o <xref:System.Windows.Forms.Form.Size%2A> propriedade do formulário.</span><span class="sxs-lookup"><span data-stu-id="56fb5-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>  
  
     <span data-ttu-id="56fb5-109">O exemplo de código a seguir mostra o tamanho do formulário definido como 100 x 100 pixels.</span><span class="sxs-lookup"><span data-stu-id="56fb5-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a><span data-ttu-id="56fb5-110">Alterar a altura e a largura do formulário com programação</span><span class="sxs-lookup"><span data-stu-id="56fb5-110">To change form width and height programmatically</span></span>  
  
-   <span data-ttu-id="56fb5-111">Após o <xref:System.Windows.Forms.Form.Size%2A> é definido, alterar a altura ou a largura usando o <xref:System.Windows.Forms.Control.Width%2A> ou <xref:System.Windows.Forms.Control.Height%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="56fb5-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="56fb5-112">O exemplo de código a seguir mostra a largura do formulário definida para 300 pixels da borda esquerda do formulário, enquanto a altura permanece constante.</span><span class="sxs-lookup"><span data-stu-id="56fb5-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     <span data-ttu-id="56fb5-113">-ou-</span><span class="sxs-lookup"><span data-stu-id="56fb5-113">-or-</span></span>  
  
     <span data-ttu-id="56fb5-114">Alteração <xref:System.Drawing.Size.Width%2A> ou <xref:System.Drawing.Size.Height%2A> definindo o <xref:System.Windows.Forms.Form.Size%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="56fb5-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>  
  
     <span data-ttu-id="56fb5-115">No entanto, como mostra o exemplo de código a seguir, essa abordagem é mais complicada do que apenas configurando <xref:System.Windows.Forms.Control.Width%2A> ou <xref:System.Windows.Forms.Control.Height%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="56fb5-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a><span data-ttu-id="56fb5-116">Alterar o tamanho do formulário em incrementos com programação</span><span class="sxs-lookup"><span data-stu-id="56fb5-116">To change form size by increments programmatically</span></span>  
  
-   <span data-ttu-id="56fb5-117">Para aumentar o tamanho do formulário, defina as <xref:System.Drawing.Size.Width%2A> e <xref:System.Drawing.Size.Height%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="56fb5-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="56fb5-118">O exemplo de código a seguir mostra a largura do formulário definida para 200 pixels mais larga do que a configuração atual.</span><span class="sxs-lookup"><span data-stu-id="56fb5-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>  
  
    ```vb  
    Form1.Width += 200  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="56fb5-119">Sempre use a <xref:System.Drawing.Size.Height%2A> ou <xref:System.Drawing.Size.Width%2A> propriedade para alterar uma dimensão de um formulário, a menos que você está definindo as dimensões de altura e largura ao mesmo tempo, definindo o <xref:System.Windows.Forms.Form.Size%2A> propriedade para um novo <xref:System.Drawing.Size> estrutura.</span><span class="sxs-lookup"><span data-stu-id="56fb5-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="56fb5-120">O <xref:System.Windows.Forms.Form.Size%2A> propriedade retorna um <xref:System.Drawing.Size> estrutura, que é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="56fb5-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="56fb5-121">Não é possível atribuir um novo valor para a propriedade de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="56fb5-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="56fb5-122">Portanto, o código a seguir não será compilado.</span><span class="sxs-lookup"><span data-stu-id="56fb5-122">Therefore, the following code example will not compile.</span></span>  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="56fb5-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56fb5-123">See also</span></span>
- [<span data-ttu-id="56fb5-124">Guia de introdução ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="56fb5-124">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
- [<span data-ttu-id="56fb5-125">Aprimorando aplicativos do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="56fb5-125">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)
