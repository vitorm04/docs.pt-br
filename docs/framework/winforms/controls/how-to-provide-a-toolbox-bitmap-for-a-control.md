---
title: 'Como: Fornecer um bitmap da caixa de ferramentas para um controle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 7c26e00acd4278ced53ad29c748ac076e0215a23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337702"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="ca69d-102">Como: Fornecer um bitmap da caixa de ferramentas para um controle</span><span class="sxs-lookup"><span data-stu-id="ca69d-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="ca69d-103">Se você quiser ter um ícone especial para o seu controle apareça na **caixa de ferramentas**, você pode especificar uma imagem específica usando o <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ca69d-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="ca69d-104">Esta classe é um *atributo*, um tipo especial de classe que você pode anexar a outras classes.</span><span class="sxs-lookup"><span data-stu-id="ca69d-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="ca69d-105">Para obter mais informações sobre atributos, consulte [visão geral de atributos (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) para o Visual Basic ou [atributos (c#)](../../../csharp/programming-guide/concepts/attributes/index.md) para c#.</span><span class="sxs-lookup"><span data-stu-id="ca69d-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>  
  
 <span data-ttu-id="ca69d-106">Usando o <xref:System.Drawing.ToolboxBitmapAttribute>, você pode especificar uma cadeia de caracteres que indica o nome de arquivo e caminho para um bitmap de 16 por 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="ca69d-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="ca69d-107">O bitmap aparece ao lado de seu controle quando adicionado à **Caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="ca69d-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="ca69d-108">Você também pode especificar um <xref:System.Type>, caso em que o bitmap associado a esse tipo é carregado.</span><span class="sxs-lookup"><span data-stu-id="ca69d-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="ca69d-109">Se você especificar uma <xref:System.Type> e uma cadeia de caracteres, o controle procurará por um recurso de imagem com o nome especificado pelo parâmetro de cadeia de caracteres no assembly que contém o tipo especificado pelo <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ca69d-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="ca69d-110">Especificar um bitmap da caixa de ferramentas para seu controle</span><span class="sxs-lookup"><span data-stu-id="ca69d-110">To specify a Toolbox bitmap for your control</span></span>  
  
1. <span data-ttu-id="ca69d-111">Adicione a <xref:System.Drawing.ToolboxBitmapAttribute> à declaração de classe do seu controle antes do `Class` palavra-chave para o visual Basic e acima da declaração de classe do Visual c#.</span><span class="sxs-lookup"><span data-stu-id="ca69d-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2. <span data-ttu-id="ca69d-112">Recompile o projeto.</span><span class="sxs-lookup"><span data-stu-id="ca69d-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ca69d-113">O bitmap não aparece na caixa de ferramentas para controles e componentes gerados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ca69d-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="ca69d-114">Para ver o bitmap, recarregue o controle usando a caixa de diálogo **Escolher Itens da Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="ca69d-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="ca69d-115">Para obter mais informações, confira [Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="ca69d-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca69d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca69d-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="ca69d-117">Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="ca69d-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="ca69d-118">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="ca69d-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="ca69d-119">Visão geral de atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca69d-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="ca69d-120">Atributos (C#)</span><span class="sxs-lookup"><span data-stu-id="ca69d-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
