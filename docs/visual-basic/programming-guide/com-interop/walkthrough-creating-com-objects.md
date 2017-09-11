---
title: 'Passo a passo: Criando objetos COM o Visual Basic | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- COM interop, creating COM objects
- COM objects, creating
- COM interop, walkthroughs
- object creation, COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 859a8fc7440eecc0cadbfa8ea236dad7cae99247
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="0bd0a-102">Instruções passo a passo: criando objetos COM com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bd0a-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="0bd0a-103">Ao criar novos aplicativos ou componentes, é melhor criar assemblies do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="0bd0a-104">No entanto, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] também facilita a expor um componente do .NET Framework para COM.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-104">However, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="0bd0a-105">Isso permite que você fornecer novos componentes anteriores aplicativo conjuntos que requerem componentes COM.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="0bd0a-106">Este passo a passo demonstra como usar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para expor [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] objetos como objetos COM, com e sem o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-106">This walkthrough demonstrates how to use [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to expose [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="0bd0a-107">A maneira mais fácil expor objetos COM é usando o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="0bd0a-108">O modelo de classe COM cria uma nova classe e, em seguida, configura seu projeto para gerar a camada de classe e interoperabilidade como um objeto COM e registrá-lo com o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bd0a-109">Embora você também pode expor uma classe criada em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] como um objeto COM para código não gerenciado usar, ele não é uma verdadeiro COM objeto e não pode ser usado por [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="0bd0a-109">Although you can also expose a class created in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="0bd0a-110">Para obter mais informações, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="0bd0a-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="0bd0a-111">Para criar um objeto COM usando o modelo de classe COM</span><span class="sxs-lookup"><span data-stu-id="0bd0a-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="0bd0a-112">Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="0bd0a-113">No **novo projeto** caixa de diálogo sob o **tipos de projeto** campo, verifique que o Windows está selecionado.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="0bd0a-114">Selecione **biblioteca de classes** do **modelos** lista e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="0bd0a-115">O novo projeto é exibido.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="0bd0a-116">Selecione **Adicionar Novo Item** do **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="0bd0a-117">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="0bd0a-118">Selecione **classe COM** do **modelos** lista e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="0bd0a-119">Adiciona uma nova classe e configura o novo projeto para interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-119"> adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="0bd0a-120">Adicione código como propriedades, métodos e eventos à classe COM.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="0bd0a-121">Selecione **criar ClassLibrary1** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="0bd0a-122">cria o assembly e registra o objeto COM o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-122"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="0bd0a-123">Criando objetos sem o modelo de classe COM</span><span class="sxs-lookup"><span data-stu-id="0bd0a-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="0bd0a-124">Você também pode criar uma classe COM manualmente em vez de usar o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="0bd0a-125">Esse procedimento é útil quando você está trabalhando na linha de comando ou quando você deseja maior controle sobre como os objetos são definidos.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="0bd0a-126">Para configurar seu projeto para gerar um objeto COM</span><span class="sxs-lookup"><span data-stu-id="0bd0a-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="0bd0a-127">Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="0bd0a-128">No **novo projeto** caixa de diálogo sob o **tipos de projeto** campo, verifique que o Windows está selecionado.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="0bd0a-129">Selecione **biblioteca de classes** do **modelos** lista e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="0bd0a-130">O novo projeto é exibido.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="0bd0a-131">Em **Solution Explorer**, clique em seu projeto e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="0bd0a-132">O **Project Designer** é exibida.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="0bd0a-133">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="0bd0a-134">Selecione o **Register for COM Interop** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="0bd0a-135">Para configurar o código em sua classe para criar um objeto COM</span><span class="sxs-lookup"><span data-stu-id="0bd0a-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="0bd0a-136">Em **Solution Explorer**, clique duas vezes em **Class1. vb** para exibir seu código.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="0bd0a-137">Renomeie a classe para `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="0bd0a-138">Adicione as seguintes constantes para `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="0bd0a-139">Eles armazenará as constantes de identificador globalmente exclusivo (GUID) que os objetos COM são necessários.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     <span data-ttu-id="0bd0a-140">[!code-vb[VbVbalrInterop n º&2;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0bd0a-140">[!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]</span></span>  
  
4.  <span data-ttu-id="0bd0a-141">Sobre o **ferramentas** menu, clique em **criar Guid**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-141">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="0bd0a-142">No **criar GUID** caixa de diálogo, clique em **formato do registro** e, em seguida, clique em **cópia**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-142">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="0bd0a-143">Clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-143">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="0bd0a-144">Substitua a cadeia de caracteres vazia para o `ClassId` com o GUID, removendo à esquerda e à direita chaves.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-144">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="0bd0a-145">Por exemplo, se o GUID fornecido pelo Guidgen é `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , em seguida, seu código deve aparecer da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-145">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     <span data-ttu-id="0bd0a-146">[!code-vb[VbVbalrInterop n º&3;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0bd0a-146">[!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]</span></span>  
  
6.  <span data-ttu-id="0bd0a-147">Repita as etapas anteriores para o `InterfaceId` e `EventsId` constantes, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-147">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     <span data-ttu-id="0bd0a-148">[!code-vb[VbVbalrInterop n º&4;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="0bd0a-148">[!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bd0a-149">Certifique-se de que os GUIDs são novas e exclusivas; Caso contrário, o componente COM pode entrar em conflito com outros componentes COM.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-149">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="0bd0a-150">Adicionar o `ComClass` atributo `ComClass1`, especificando os GUIDs para a identificação de classe, Interface ID e identificação de eventos como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0bd0a-150">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     <span data-ttu-id="0bd0a-151">[!code-vb[VbVbalrInterop n º&5;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="0bd0a-151">[!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]</span></span>  
  
8.  <span data-ttu-id="0bd0a-152">Classes COM devem ter um sem parâmetros `Public Sub New()` construtor, ou a classe não registrará corretamente.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-152">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="0bd0a-153">Adicione um construtor sem parâmetros à classe:</span><span class="sxs-lookup"><span data-stu-id="0bd0a-153">Add a parameterless constructor to the class:</span></span>  
  
     <span data-ttu-id="0bd0a-154">[!code-vb[VbVbalrInterop n º&6;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="0bd0a-154">[!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]</span></span>  
  
9. <span data-ttu-id="0bd0a-155">Adicione propriedades, métodos e eventos à classe, terminando com um `End Class` instrução.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-155">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="0bd0a-156">Selecione **Build Solution** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-156">Select **Build Solution** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="0bd0a-157">cria o assembly e registra o objeto COM o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-157"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bd0a-158">Os objetos COM que você gerar com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não pode ser usado por outros [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] aplicativos porque eles não são objetos true.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-158">The COM objects you generate with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot be used by other [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] applications because they are not true COM objects.</span></span> <span data-ttu-id="0bd0a-159">Tenta adicionar referências a esses objetos COM irá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="0bd0a-159">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="0bd0a-160">Para obter detalhes, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="0bd0a-160">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd0a-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bd0a-161">See Also</span></span>  
 <span data-ttu-id="0bd0a-162"><xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute></span><span class="sxs-lookup"><span data-stu-id="0bd0a-162"><xref:Microsoft.VisualBasic.ComClassAttribute></span></span>   
<span data-ttu-id="0bd0a-163"> [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bd0a-163"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="0bd0a-164"> [Passo a passo: Implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="0bd0a-164"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="0bd0a-165"> [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md) </span><span class="sxs-lookup"><span data-stu-id="0bd0a-165"> [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) </span></span>  
<span data-ttu-id="0bd0a-166"> [Interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span><span class="sxs-lookup"><span data-stu-id="0bd0a-166"> [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span></span>  
<span data-ttu-id="0bd0a-167"> [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span><span class="sxs-lookup"><span data-stu-id="0bd0a-167"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span></span>
