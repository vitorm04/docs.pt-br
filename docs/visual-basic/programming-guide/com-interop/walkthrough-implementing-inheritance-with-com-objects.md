---
title: 'Passo a passo: Implementando a herança com objetos COM (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 0b3977e73e3b2aa9e80e2dab08d15035283b8387
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334140"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="ed932-102">Passo a passo: Implementando a herança com objetos COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed932-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="ed932-103">Você pode derivar classes de Visual Basic de `Public` classes em objetos COM, mesmo aqueles criados em versões anteriores do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ed932-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="ed932-104">As propriedades e métodos das classes herdadas de objetos COM a podem ser substituídos ou sobrecarregados assim como as propriedades e métodos de qualquer outra classe base podem ser substituídos ou sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="ed932-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="ed932-105">Herança de objetos COM é útil quando você tiver uma biblioteca de classe existente que você não deseja recompilar.</span><span class="sxs-lookup"><span data-stu-id="ed932-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="ed932-106">O procedimento a seguir mostra como usar o Visual Basic 6.0 para criar um objeto COM que contém uma classe e, em seguida, usá-lo como uma classe base.</span><span class="sxs-lookup"><span data-stu-id="ed932-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="ed932-107">Para criar o objeto COM que é usado neste passo a passo</span><span class="sxs-lookup"><span data-stu-id="ed932-107">To build the COM object that is used in this walkthrough</span></span>  
  
1. <span data-ttu-id="ed932-108">No Visual Basic 6.0, abra um novo projeto de DLL do ActiveX.</span><span class="sxs-lookup"><span data-stu-id="ed932-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="ed932-109">Um projeto chamado `Project1` é criado.</span><span class="sxs-lookup"><span data-stu-id="ed932-109">A project named `Project1` is created.</span></span> <span data-ttu-id="ed932-110">Ele tem uma classe chamada `Class1`.</span><span class="sxs-lookup"><span data-stu-id="ed932-110">It has a class named `Class1`.</span></span>  
  
2. <span data-ttu-id="ed932-111">No **Explorador de projeto**, clique com botão direito **Projeto1**e, em seguida, clique em **Projeto1 propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ed932-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="ed932-112">O **propriedades do projeto** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="ed932-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3. <span data-ttu-id="ed932-113">No **gerais** guia da **propriedades do projeto** caixa de diálogo, altere o nome do projeto, digitando `ComObject1` no **nome do projeto** campo.</span><span class="sxs-lookup"><span data-stu-id="ed932-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4. <span data-ttu-id="ed932-114">No **Explorador de projeto**, clique com botão direito `Class1`e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ed932-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="ed932-115">O **propriedades** janela para a classe é exibida.</span><span class="sxs-lookup"><span data-stu-id="ed932-115">The **Properties** window for the class is displayed.</span></span>  
  
5. <span data-ttu-id="ed932-116">Alterar o `Name` propriedade para `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="ed932-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6. <span data-ttu-id="ed932-117">No **Explorador de projeto**, clique com botão direito `MathFunctions`e, em seguida, clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="ed932-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="ed932-118">O **Editor de códigos** é exibida.</span><span class="sxs-lookup"><span data-stu-id="ed932-118">The **Code Editor** is displayed.</span></span>  
  
7. <span data-ttu-id="ed932-119">Adicione uma variável local para armazenar o valor da propriedade:</span><span class="sxs-lookup"><span data-stu-id="ed932-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8. <span data-ttu-id="ed932-120">Adicionar propriedade `Let` e a propriedade `Get` procedimentos de propriedade:</span><span class="sxs-lookup"><span data-stu-id="ed932-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. <span data-ttu-id="ed932-121">Adicione uma função:</span><span class="sxs-lookup"><span data-stu-id="ed932-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="ed932-122">Criar e registrar o objeto COM, clicando em **tornar ComObject1.dll** sobre o **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="ed932-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ed932-123">Embora você também pode expor uma classe criada com o Visual Basic como um objeto COM, ele não é um objeto COM real e não pode ser usado neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ed932-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="ed932-124">Para obter detalhes, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="ed932-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="ed932-125">Assemblies de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ed932-125">Interop Assemblies</span></span>  
 <span data-ttu-id="ed932-126">O procedimento a seguir, você criará um assembly de interoperabilidade, que atua como uma ponte entre o código não gerenciado (por exemplo, um objeto COM) e o código gerenciado que usa o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ed932-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="ed932-127">O assembly de interoperabilidade do Visual Basic cria lida com muitos dos detalhes de como trabalhar com objetos COM, como *marshaling de interoperabilidade*, o processo de compactação parâmetros e valores de retorno em dados equivalentes tipos quando eles passam a e de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="ed932-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="ed932-128">A referência no aplicativo Visual Basic aponta para o assembly de interoperabilidade, não o objeto COM real.</span><span class="sxs-lookup"><span data-stu-id="ed932-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="ed932-129">Usar um objeto COM o Visual Basic 2005 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="ed932-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1. <span data-ttu-id="ed932-130">Abra um novo projeto de aplicativo do Windows Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ed932-130">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="ed932-131">No menu **Projeto**, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="ed932-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="ed932-132">A caixa de diálogo **Adicionar Referência** é exibida.</span><span class="sxs-lookup"><span data-stu-id="ed932-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3. <span data-ttu-id="ed932-133">Sobre o **COM** guia, clique duas vezes `ComObject1` no **nome do componente** lista e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="ed932-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4. <span data-ttu-id="ed932-134">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="ed932-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="ed932-135">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="ed932-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5. <span data-ttu-id="ed932-136">No **modelos** painel, clique em **classe**.</span><span class="sxs-lookup"><span data-stu-id="ed932-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="ed932-137">O nome de arquivo padrão, `Class1.vb`, é exibida na **nome** campo.</span><span class="sxs-lookup"><span data-stu-id="ed932-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="ed932-138">Altere este campo para MathClass.vb e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ed932-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="ed932-139">Isso cria uma classe chamada `MathClass`e exibe seu código.</span><span class="sxs-lookup"><span data-stu-id="ed932-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6. <span data-ttu-id="ed932-140">Adicione o seguinte código na parte superior do `MathClass` herdar da classe COM.</span><span class="sxs-lookup"><span data-stu-id="ed932-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]  
  
7. <span data-ttu-id="ed932-141">Sobrecarregar o método público da classe base, adicionando o seguinte código ao `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="ed932-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]  
  
8. <span data-ttu-id="ed932-142">Estender a classe herdada adicionando o seguinte código ao `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="ed932-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]  
  
 <span data-ttu-id="ed932-143">A nova classe herda as propriedades da classe base no objeto COM, sobrecarrega um método e define um novo método para estender a classe.</span><span class="sxs-lookup"><span data-stu-id="ed932-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="ed932-144">Para testar a classe herdada</span><span class="sxs-lookup"><span data-stu-id="ed932-144">To test the inherited class</span></span>  
  
1. <span data-ttu-id="ed932-145">Adicione um botão ao seu formulário de inicialização e, em seguida, clique duas vezes nele para exibir seu código.</span><span class="sxs-lookup"><span data-stu-id="ed932-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2. <span data-ttu-id="ed932-146">O botão `Click` procedimento do manipulador de eventos, adicione o seguinte código para criar uma instância de `MathClass` e chamar os métodos sobrecarregados:</span><span class="sxs-lookup"><span data-stu-id="ed932-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]  
  
3. <span data-ttu-id="ed932-147">Execute o projeto pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="ed932-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="ed932-148">Quando você clica no botão no formulário, o `AddNumbers` método é chamado pela primeira vez com `Short` números, tipo de dados e o Visual Basic escolhe o método apropriado da classe base.</span><span class="sxs-lookup"><span data-stu-id="ed932-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="ed932-149">A segunda chamada para `AddNumbers` é direcionado para o método de sobrecarga de `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="ed932-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="ed932-150">A terceira chamada chama o `SubtractNumbers` método, que estende a classe.</span><span class="sxs-lookup"><span data-stu-id="ed932-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="ed932-151">A propriedade na classe base é definida, e o valor é exibido.</span><span class="sxs-lookup"><span data-stu-id="ed932-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ed932-152">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ed932-152">Next Steps</span></span>  
 <span data-ttu-id="ed932-153">Você deve ter observado que sobrecarregado `AddNumbers` função parece ter os mesmos dados de tipo que o método herdado da classe base do objeto COM.</span><span class="sxs-lookup"><span data-stu-id="ed932-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="ed932-154">Isso ocorre porque os argumentos e os parâmetros de método da classe base são definidos como inteiros de 16 bits no Visual Basic 6.0, mas eles são expostos como inteiros de 16 bits do tipo `Short` em versões posteriores do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ed932-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="ed932-155">A nova função aceita inteiros de 32 bits e sobrecargas de função da classe base.</span><span class="sxs-lookup"><span data-stu-id="ed932-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="ed932-156">Ao trabalhar com objetos COM, certifique-se de que você verifique os tipos de dados e tamanho dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ed932-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="ed932-157">Por exemplo, quando você estiver usando um objeto COM que aceita um objeto de coleção do Visual Basic 6.0 como um argumento, você não pode fornecer uma coleção de uma versão posterior do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ed932-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="ed932-158">As propriedades e métodos herdados de classes COM podem ser substituídos, que significa que você pode declarar uma propriedade local ou um método que substitui uma propriedade ou método herdado de uma classe base do COM.</span><span class="sxs-lookup"><span data-stu-id="ed932-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="ed932-159">As regras para a substituição COM as propriedades herdadas são semelhantes às regras para a substituição de outras propriedades e métodos com as seguintes exceções:</span><span class="sxs-lookup"><span data-stu-id="ed932-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="ed932-160">Se você substituir qualquer propriedade ou método herdado de uma classe COM, você deve substituir todas as outras propriedades herdadas e métodos.</span><span class="sxs-lookup"><span data-stu-id="ed932-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="ed932-161">As propriedades que usam `ByRef` parâmetros não podem ser substituídos.</span><span class="sxs-lookup"><span data-stu-id="ed932-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed932-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed932-162">See also</span></span>

- [<span data-ttu-id="ed932-163">Interoperabilidade COM em Aplicativos .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ed932-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="ed932-164">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="ed932-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="ed932-165">Tipo de Dados Short</span><span class="sxs-lookup"><span data-stu-id="ed932-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
