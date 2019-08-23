---
title: 'Passo a passo: Criando objetos com com Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 39012ebdd8946f707fe459cb09bb2bbfc8e50088
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958276"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="32bd5-102">Passo a passo: Criando objetos com com Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32bd5-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="32bd5-103">Ao criar novos aplicativos ou componentes, é melhor criar assemblies de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32bd5-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="32bd5-104">No entanto, Visual Basic também facilita a exposição de um componente de .NET Framework para COM.</span><span class="sxs-lookup"><span data-stu-id="32bd5-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="32bd5-105">Isso permite que você forneça novos componentes para conjuntos de aplicativos anteriores que exigem componentes COM.</span><span class="sxs-lookup"><span data-stu-id="32bd5-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="32bd5-106">Este tutorial demonstra como usar Visual Basic para expor .NET Framework objetos como objetos COM, com e sem o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="32bd5-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="32bd5-107">A maneira mais fácil de expor objetos COM é usando o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="32bd5-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="32bd5-108">O modelo de classe COM cria uma nova classe e, em seguida, configura seu projeto para gerar a classe e a camada de interoperabilidade como um objeto COM e registrá-lo no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="32bd5-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32bd5-109">Embora você também possa expor uma classe criada em Visual Basic como um objeto COM para que o código não gerenciado use, ele não é um objeto COM verdadeiro e não pode ser usado por Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="32bd5-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="32bd5-110">Para obter mais informações, consulte interoperabilidade [com em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="32bd5-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="32bd5-111">Para criar um objeto COM usando o modelo de classe COM</span><span class="sxs-lookup"><span data-stu-id="32bd5-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="32bd5-112">Abra um novo projeto de aplicativo do Windows no menu **arquivo** clicando em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="32bd5-113">Na caixa de diálogo **novo projeto** , no campo **tipos de projeto** , verifique se Windows está selecionado.</span><span class="sxs-lookup"><span data-stu-id="32bd5-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="32bd5-114">Selecione **biblioteca de classes** na lista **modelos** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="32bd5-115">O novo projeto é exibido.</span><span class="sxs-lookup"><span data-stu-id="32bd5-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="32bd5-116">Selecione **Adicionar novo item** no menu **projeto** .</span><span class="sxs-lookup"><span data-stu-id="32bd5-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="32bd5-117">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="32bd5-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="32bd5-118">Selecione a **classe com** na lista **modelos** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="32bd5-119">Visual Basic adiciona uma nova classe e configura o novo projeto para interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="32bd5-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="32bd5-120">Adicione um código como propriedades, métodos e eventos à classe COM.</span><span class="sxs-lookup"><span data-stu-id="32bd5-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="32bd5-121">Selecione **criar ClassLibrary1** no menu **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="32bd5-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="32bd5-122">Visual Basic compila o assembly e registra o objeto com com o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="32bd5-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="32bd5-123">Criando objetos COM sem o modelo de classe COM</span><span class="sxs-lookup"><span data-stu-id="32bd5-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="32bd5-124">Você também pode criar uma classe COM manualmente em vez de usar o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="32bd5-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="32bd5-125">Esse procedimento é útil quando você está trabalhando na linha de comando ou quando deseja obter mais controle sobre como os objetos COM são definidos.</span><span class="sxs-lookup"><span data-stu-id="32bd5-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="32bd5-126">Para configurar seu projeto para gerar um objeto COM</span><span class="sxs-lookup"><span data-stu-id="32bd5-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="32bd5-127">Abra um novo projeto de aplicativo do Windows no menu **arquivo** clicando em **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="32bd5-128">Na caixa de diálogo **novo projeto** , no campo **tipos de projeto** , verifique se Windows está selecionado.</span><span class="sxs-lookup"><span data-stu-id="32bd5-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="32bd5-129">Selecione **biblioteca de classes** na lista **modelos** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="32bd5-130">O novo projeto é exibido.</span><span class="sxs-lookup"><span data-stu-id="32bd5-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="32bd5-131">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do seu projeto e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="32bd5-132">O **Designer de projeto** é exibido.</span><span class="sxs-lookup"><span data-stu-id="32bd5-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="32bd5-133">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="32bd5-134">Marque a caixa de seleção **registrar para interoperabilidade com** .</span><span class="sxs-lookup"><span data-stu-id="32bd5-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="32bd5-135">Para configurar o código em sua classe para criar um objeto COM</span><span class="sxs-lookup"><span data-stu-id="32bd5-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="32bd5-136">Em **Gerenciador de soluções**, clique duas vezes em **Class1. vb** para exibir seu código.</span><span class="sxs-lookup"><span data-stu-id="32bd5-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="32bd5-137">Renomeie a `ComClass1`classe como.</span><span class="sxs-lookup"><span data-stu-id="32bd5-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="32bd5-138">Adicione as constantes a seguir `ComClass1`a.</span><span class="sxs-lookup"><span data-stu-id="32bd5-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="32bd5-139">Eles armazenarão as constantes GUID (identificador global exclusivo) que os objetos COM devem ter.</span><span class="sxs-lookup"><span data-stu-id="32bd5-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="32bd5-140">No menu **Ferramentas**, clique em **Criar GUID**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="32bd5-141">Na caixa de diálogo **Criar GUID**, clique em **Formato do Registro** e clique em **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="32bd5-142">Clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="32bd5-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="32bd5-143">Substitua a cadeia de caracteres `ClassId` vazia do pelo GUID, removendo as chaves à esquerda e à direita.</span><span class="sxs-lookup"><span data-stu-id="32bd5-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="32bd5-144">Por exemplo, se o GUID fornecido pelo Guidgen for `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , seu código deverá aparecer da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="32bd5-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="32bd5-145">Repita as etapas anteriores para as `InterfaceId` constantes `EventsId` e, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="32bd5-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="32bd5-146">Certifique-se de que os GUIDs são novos e exclusivos; caso contrário, o componente COM pode entrar em conflito com outros componentes COM.</span><span class="sxs-lookup"><span data-stu-id="32bd5-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="32bd5-147">Adicione o `ComClass` atributo a `ComClass1`, especificando os GUIDs para a ID de classe, ID de interface e ID de eventos, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="32bd5-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="32bd5-148">As classes com devem ter um `Public Sub New()` Construtor sem parâmetros ou a classe não será registrada corretamente.</span><span class="sxs-lookup"><span data-stu-id="32bd5-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="32bd5-149">Adicione um construtor sem parâmetros à classe:</span><span class="sxs-lookup"><span data-stu-id="32bd5-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="32bd5-150">Adicione Propriedades, métodos e eventos à classe, encerrando-o com uma `End Class` instrução.</span><span class="sxs-lookup"><span data-stu-id="32bd5-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="32bd5-151">Selecione **Compilar solução** no menu **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="32bd5-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="32bd5-152">Visual Basic compila o assembly e registra o objeto com com o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="32bd5-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="32bd5-153">Os objetos COM que você gera com Visual Basic não podem ser usados por outros aplicativos Visual Basic porque não são objetos COM verdadeiros.</span><span class="sxs-lookup"><span data-stu-id="32bd5-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="32bd5-154">As tentativas de adicionar referências a esses objetos COM gerarão um erro.</span><span class="sxs-lookup"><span data-stu-id="32bd5-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="32bd5-155">Para obter detalhes, consulte interoperabilidade [com em aplicativos .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="32bd5-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bd5-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32bd5-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="32bd5-157">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="32bd5-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="32bd5-158">Passo a passo: implementação de herança com objetos COM</span><span class="sxs-lookup"><span data-stu-id="32bd5-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="32bd5-159">Diretiva #Region</span><span class="sxs-lookup"><span data-stu-id="32bd5-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="32bd5-160">Interoperabilidade COM em Aplicativos .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32bd5-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="32bd5-161">Solução de problemas de Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="32bd5-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
