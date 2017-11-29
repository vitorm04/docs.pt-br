---
title: "Instruções passo a passo: criando objetos COM com o Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff7d3868a2e3ddaba06ebc6f98c8eacfc7299366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="fb3a9-102">Instruções passo a passo: criando objetos COM com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb3a9-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="fb3a9-103">Ao criar novos aplicativos ou componentes, é melhor criar assemblies do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="fb3a9-104">No entanto, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] também facilita a expor um componente do .NET Framework para COM.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-104">However, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="fb3a9-105">Isso permite que você fornecer novos componentes anteriores aplicativo conjuntos que requerem componentes COM.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="fb3a9-106">Este passo a passo demonstra como usar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] para expor [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objetos como objetos COM, com e sem o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-106">This walkthrough demonstrates how to use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="fb3a9-107">A maneira mais fácil expor objetos COM é usando o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="fb3a9-108">O modelo de classe COM cria uma nova classe e, em seguida, configura seu projeto para gerar a camada de classe e interoperabilidade como um objeto COM e registrá-lo com o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb3a9-109">Embora você também pode expor uma classe criada em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] como um objeto COM para código não gerenciado usar, ele não é um objeto COM true e não pode ser usado por [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb3a9-109">Although you can also expose a class created in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="fb3a9-110">Para obter mais informações, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="fb3a9-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="fb3a9-111">Para criar um objeto COM usando o modelo de classe COM</span><span class="sxs-lookup"><span data-stu-id="fb3a9-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="fb3a9-112">Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="fb3a9-113">No **novo projeto** caixa de diálogo do **tipos de projeto** campo, verifique se o Windows está selecionado.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="fb3a9-114">Selecione **biblioteca de classes** do **modelos** lista e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="fb3a9-115">O novo projeto é exibido.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="fb3a9-116">Selecione **Adicionar Novo Item** do **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="fb3a9-117">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="fb3a9-118">Selecione **classe COM** do **modelos** lista e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="fb3a9-119">Adiciona uma nova classe e configura o novo projeto para interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-119"> adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="fb3a9-120">Adicione código como propriedades, métodos e eventos para a classe COM.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="fb3a9-121">Selecione **criar ClassLibrary1** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="fb3a9-122">cria o assembly e registra o objeto COM o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-122"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="fb3a9-123">Criando objetos sem o modelo de classe COM</span><span class="sxs-lookup"><span data-stu-id="fb3a9-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="fb3a9-124">Você também pode criar uma classe COM manualmente, em vez de usar o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="fb3a9-125">Esse procedimento é útil quando você estiver trabalhando na linha de comando ou quando você quiser mais controle sobre como os objetos são definidos.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="fb3a9-126">Para configurar seu projeto para gerar um objeto COM</span><span class="sxs-lookup"><span data-stu-id="fb3a9-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="fb3a9-127">Abra um novo projeto de aplicativo do Windows a partir de **arquivo** menu clicando **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="fb3a9-128">No **novo projeto** caixa de diálogo do **tipos de projeto** campo, verifique se o Windows está selecionado.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="fb3a9-129">Selecione **biblioteca de classes** do **modelos** lista e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="fb3a9-130">O novo projeto é exibido.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="fb3a9-131">Em **Solution Explorer**, clique com o botão direito e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="fb3a9-132">O **Project Designer** é exibido.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="fb3a9-133">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="fb3a9-134">Selecione o **registrar para interoperabilidade COM** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="fb3a9-135">Para configurar o código em sua classe para criar um objeto COM</span><span class="sxs-lookup"><span data-stu-id="fb3a9-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="fb3a9-136">Em **Solution Explorer**, clique duas vezes em **Class1** para exibir seu código.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="fb3a9-137">Renomeie a classe para `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="fb3a9-138">Adicione as seguintes constantes para `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="fb3a9-139">Eles armazenará as constantes de identificador globalmente exclusivo (GUID) que os objetos COM devem ter.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  <span data-ttu-id="fb3a9-140">No menu **Ferramentas**, clique em **Criar GUID**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="fb3a9-141">Na caixa de diálogo **Criar GUID**, clique em **Formato do Registro** e clique em **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="fb3a9-142">Clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-142">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="fb3a9-143">Substitua a cadeia de caracteres vazia para o `ClassId` com o GUID, chaves removendo à esquerda e à direita.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="fb3a9-144">Por exemplo, se o GUID fornecido pelo Guidgen é `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , em seguida, seu código deve aparecer da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  <span data-ttu-id="fb3a9-145">Repita as etapas anteriores para o `InterfaceId` e `EventsId` constantes, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="fb3a9-146">Certifique-se de que os GUIDs são novos e exclusivos; Caso contrário, o componente COM pode entrar em conflito com outros componentes COM.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="fb3a9-147">Adicionar o `ComClass` atributo `ComClass1`, especificando os GUIDs para a identificação de classe, a ID de Interface e a ID de eventos, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="fb3a9-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  <span data-ttu-id="fb3a9-148">Classes COM devem ter um sem parâmetros `Public Sub New()` construtor, ou a classe não registrará corretamente.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="fb3a9-149">Adicione um construtor sem parâmetros à classe:</span><span class="sxs-lookup"><span data-stu-id="fb3a9-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. <span data-ttu-id="fb3a9-150">Adicionar propriedades, métodos e eventos à classe, terminando com um `End Class` instrução.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="fb3a9-151">Selecione **compilar solução** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-151">Select **Build Solution** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="fb3a9-152">cria o assembly e registra o objeto COM o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-152"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb3a9-153">Os objetos COM que você gerar com [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não pode ser usado por outros [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aplicativos porque eles não são objetos true.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-153">The COM objects you generate with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot be used by other [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] applications because they are not true COM objects.</span></span> <span data-ttu-id="fb3a9-154">Tenta adicionar referências a esses objetos COM irá gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="fb3a9-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="fb3a9-155">Para obter detalhes, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="fb3a9-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3a9-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb3a9-156">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [<span data-ttu-id="fb3a9-157">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="fb3a9-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="fb3a9-158">Instruções passo a passo: implementando a herança com objetos COM</span><span class="sxs-lookup"><span data-stu-id="fb3a9-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="fb3a9-159">Diretiva #Region</span><span class="sxs-lookup"><span data-stu-id="fb3a9-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="fb3a9-160">Interoperabilidade COM em Aplicativos .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb3a9-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="fb3a9-161">Solução de problemas de Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="fb3a9-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
