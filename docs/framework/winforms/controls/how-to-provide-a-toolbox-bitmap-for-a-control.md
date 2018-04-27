---
title: Como fornecer um bitmap da caixa de ferramentas para um controle
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d34cbb88805d9c034df61aba89ebd7bb224b1da
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="a419b-102">Como fornecer um bitmap da caixa de ferramentas para um controle</span><span class="sxs-lookup"><span data-stu-id="a419b-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="a419b-103">Se você deseja ter um ícone especial para o seu controle aparecem no **caixa de ferramentas**, você pode especificar uma imagem específica usando o <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a419b-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="a419b-104">Esta classe é um *atributo*, um tipo especial de classe que você pode anexar a outras classes.</span><span class="sxs-lookup"><span data-stu-id="a419b-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="a419b-105">Para obter mais informações sobre atributos, consulte [não está em compilação: Visão geral de atributos no Visual Basic](http://msdn.microsoft.com/library/0d0cff64-892d-4f57-83bd-bef388553d4f) do Visual Basic e [atributos](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) para Visual c#.</span><span class="sxs-lookup"><span data-stu-id="a419b-105">For more information about attributes, see [NOT IN BUILD: Attributes Overview in Visual Basic](http://msdn.microsoft.com/library/0d0cff64-892d-4f57-83bd-bef388553d4f) for Visual Basic and [Attributes](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) for Visual C#.</span></span>  
  
 <span data-ttu-id="a419b-106">Usando o <xref:System.Drawing.ToolboxBitmapAttribute>, você pode especificar uma cadeia de caracteres que indica o caminho e nome de arquivo para um bitmap de 16 por 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="a419b-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="a419b-107">O bitmap aparece ao lado de seu controle quando adicionado à **Caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a419b-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="a419b-108">Você também pode especificar um <xref:System.Type>, caso em que o bitmap associado com o tipo é carregado.</span><span class="sxs-lookup"><span data-stu-id="a419b-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="a419b-109">Se você especificar ambos um <xref:System.Type> e uma cadeia de caracteres, o controle de pesquisa para um recurso de imagem com o nome especificado pelo parâmetro de cadeia de caracteres no assembly que contém o tipo especificado pelo <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a419b-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="a419b-110">Especificar um bitmap da caixa de ferramentas para seu controle</span><span class="sxs-lookup"><span data-stu-id="a419b-110">To specify a Toolbox bitmap for your control</span></span>  
  
1.  <span data-ttu-id="a419b-111">Adicionar o <xref:System.Drawing.ToolboxBitmapAttribute> à declaração de classe do controle antes do `Class` palavra-chave do visual Basic e acima da declaração de classe para o Visual c#.</span><span class="sxs-lookup"><span data-stu-id="a419b-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
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
  
2.  <span data-ttu-id="a419b-112">Recompile o projeto.</span><span class="sxs-lookup"><span data-stu-id="a419b-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a419b-113">O bitmap não aparece na caixa de ferramentas para controles e componentes gerados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a419b-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="a419b-114">Para ver o bitmap, recarregue o controle usando a caixa de diálogo **Escolher Itens da Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a419b-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="a419b-115">Para mais informações, consulte [Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="a419b-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a419b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a419b-116">See Also</span></span>  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [<span data-ttu-id="a419b-117">Passo a passo: preenchendo automaticamente a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="a419b-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="a419b-118">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="a419b-118">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="a419b-119">Atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a419b-119">Attributes (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="a419b-120">Atributos</span><span class="sxs-lookup"><span data-stu-id="a419b-120">Attributes</span></span>](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
