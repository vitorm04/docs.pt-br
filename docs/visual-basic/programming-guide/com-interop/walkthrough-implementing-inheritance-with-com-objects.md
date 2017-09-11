---
title: "Passo a passo: Implementando a herança com objetos COM (Visual Basic) | Documentos do Microsoft"
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
- inheritance, COM reusability
- base classes, COM reusability
- inheritance, walkthroughs
- derived classes, COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
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
ms.openlocfilehash: 0e816d1728678467d930de524b894d175f9b0c0a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="5a379-102">Instruções passo a passo: implementando a herança com objetos COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a379-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="5a379-103">Você pode derivar classes do Visual Basic do `Public` classes em objetos COM, mesmo aqueles criados em versões anteriores do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a379-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="5a379-104">As propriedades e métodos de classes herdadas de objetos podem ser substituídos ou sobrecarregados apenas como propriedades e métodos de qualquer outra classe base podem ser substituídos ou sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="5a379-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="5a379-105">Herança de objetos é útil quando você tem uma biblioteca de classe existente que você não deseja recompilar.</span><span class="sxs-lookup"><span data-stu-id="5a379-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="5a379-106">O procedimento a seguir mostra como usar o Visual Basic 6.0 para criar um objeto COM que contém uma classe e então usá-lo como uma classe base.</span><span class="sxs-lookup"><span data-stu-id="5a379-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="5a379-107">Para criar o objeto COM é usado neste passo a passo</span><span class="sxs-lookup"><span data-stu-id="5a379-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="5a379-108">No Visual Basic 6.0, abra um novo projeto de DLL do ActiveX.</span><span class="sxs-lookup"><span data-stu-id="5a379-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="5a379-109">Um projeto chamado `Project1` é criado.</span><span class="sxs-lookup"><span data-stu-id="5a379-109">A project named `Project1` is created.</span></span> <span data-ttu-id="5a379-110">Ele tem uma classe chamada `Class1`.</span><span class="sxs-lookup"><span data-stu-id="5a379-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="5a379-111">No **Explorador de projeto**, clique com botão direito **Projeto1**e, em seguida, clique em **Projeto1 propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5a379-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="5a379-112">O **propriedades do projeto** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="5a379-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="5a379-113">No **geral** guia do **propriedades do projeto** caixa de diálogo, altere o nome do projeto digitando `ComObject1` no **nome do projeto** campo.</span><span class="sxs-lookup"><span data-stu-id="5a379-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="5a379-114">No **Explorador de projeto**, clique com botão direito `Class1`e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5a379-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="5a379-115">O **propriedades** janela para a classe é exibida.</span><span class="sxs-lookup"><span data-stu-id="5a379-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="5a379-116">Alterar o `Name` propriedade `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="5a379-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="5a379-117">No **Explorador de projeto**, clique com botão direito `MathFunctions`e, em seguida, clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="5a379-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="5a379-118">O **Editor de códigos** é exibida.</span><span class="sxs-lookup"><span data-stu-id="5a379-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="5a379-119">Adicione uma variável local para armazenar o valor da propriedade:</span><span class="sxs-lookup"><span data-stu-id="5a379-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="5a379-120">Adicionar propriedade `Let` e propriedade `Get` procedimentos de propriedade:</span><span class="sxs-lookup"><span data-stu-id="5a379-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
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
  
9. <span data-ttu-id="5a379-121">Adicione uma função:</span><span class="sxs-lookup"><span data-stu-id="5a379-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="5a379-122">Criar e registrar o objeto COM clicando em **ComObject1.dll fazer** sobre o **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="5a379-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a379-123">Embora você também pode expor uma classe criada com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] como um objeto COM, ele não é uma verdadeiro COM objeto e não pode ser usado neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="5a379-123">Although you can also expose a class created with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="5a379-124">Para obter detalhes, consulte [interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="5a379-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="5a379-125">Assemblies de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5a379-125">Interop Assemblies</span></span>  
 <span data-ttu-id="5a379-126">O procedimento a seguir, você criará um assembly de interoperabilidade, que atua como uma ponte entre o código gerenciado e código não gerenciado (como um objeto COM) [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] usa.</span><span class="sxs-lookup"><span data-stu-id="5a379-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] uses.</span></span> <span data-ttu-id="5a379-127">O assembly de interoperabilidade que [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cria identificadores de muitos dos detalhes de como trabalhar com objetos, como *marshaling de interoperabilidade*, o processo de compactação parâmetros e valores de retorno em dados equivalentes tipos como eles se movem para e de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="5a379-127">The interop assembly that [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="5a379-128">A referência a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] aplicativo apontar para o assembly de interoperabilidade, não o objeto COM real.</span><span class="sxs-lookup"><span data-stu-id="5a379-128">The reference in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="5a379-129">Para usar um objeto COM o Visual Basic 2005 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5a379-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="5a379-130">Abra um novo [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projeto aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="5a379-130">Open a new [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="5a379-131">Sobre o **projeto** menu, clique em **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="5a379-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="5a379-132">O **adicionar referência** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="5a379-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="5a379-133">Sobre o **COM** guia, clique duas vezes `ComObject1` no **nome do componente** lista e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="5a379-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="5a379-134">No menu **Projeto**, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="5a379-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="5a379-135">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="5a379-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="5a379-136">No **modelos** painel, clique em **classe**.</span><span class="sxs-lookup"><span data-stu-id="5a379-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="5a379-137">O nome de arquivo padrão, `Class1.vb`, aparece no **nome** campo.</span><span class="sxs-lookup"><span data-stu-id="5a379-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="5a379-138">Alterar esse campo para MathClass.vb e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="5a379-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="5a379-139">Isso cria uma classe chamada `MathClass`e exibe seu código.</span><span class="sxs-lookup"><span data-stu-id="5a379-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="5a379-140">Adicione o seguinte código à parte superior do `MathClass` para herdar da classe COM.</span><span class="sxs-lookup"><span data-stu-id="5a379-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     <span data-ttu-id="5a379-141">[!code-vb[VbVbalrInterop&#31;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5a379-141">[!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]</span></span>  
  
7.  <span data-ttu-id="5a379-142">Sobrecarregar o método público da classe base, adicionando o seguinte código ao `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="5a379-142">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     <span data-ttu-id="5a379-143">[!code-vb[32 VbVbalrInterop](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5a379-143">[!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]</span></span>  
  
8.  <span data-ttu-id="5a379-144">Estender a classe herdada, adicionando o seguinte código ao `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="5a379-144">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     <span data-ttu-id="5a379-145">[!code-vb[33 VbVbalrInterop](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="5a379-145">[!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]</span></span>  
  
 <span data-ttu-id="5a379-146">A nova classe herda as propriedades da classe base do objeto COM, sobrecarrega um método e define um novo método para estender a classe.</span><span class="sxs-lookup"><span data-stu-id="5a379-146">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="5a379-147">Para testar a classe herdada</span><span class="sxs-lookup"><span data-stu-id="5a379-147">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="5a379-148">Adicionar um botão para o formulário de inicialização e, em seguida, clique duas vezes nele para exibir seu código.</span><span class="sxs-lookup"><span data-stu-id="5a379-148">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="5a379-149">O botão `Click` procedimento de manipulador de eventos, adicione o seguinte código para criar uma instância de `MathClass` e chamar os métodos sobrecarregados:</span><span class="sxs-lookup"><span data-stu-id="5a379-149">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     <span data-ttu-id="5a379-150">[!code-vb[VbVbalrInterop&#34;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="5a379-150">[!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]</span></span>  
  
3.  <span data-ttu-id="5a379-151">Execute o projeto pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="5a379-151">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="5a379-152">Quando você clica no botão no formulário, o `AddNumbers` método é chamado pela primeira vez com `Short` números, tipo de dados e [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] escolhe o método apropriado da classe base.</span><span class="sxs-lookup"><span data-stu-id="5a379-152">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chooses the appropriate method from the base class.</span></span> <span data-ttu-id="5a379-153">A segunda chamada para `AddNumbers` é direcionado para o método de sobrecarga de `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="5a379-153">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="5a379-154">A terceira chamada chama o `SubtractNumbers` método, que estende a classe.</span><span class="sxs-lookup"><span data-stu-id="5a379-154">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="5a379-155">A propriedade na classe base é definida e o valor é exibido.</span><span class="sxs-lookup"><span data-stu-id="5a379-155">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5a379-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5a379-156">Next Steps</span></span>  
 <span data-ttu-id="5a379-157">Você talvez tenha observado que sobrecarregados `AddNumbers` função parece ter os mesmos dados de tipo que o método herdado da classe base do objeto COM.</span><span class="sxs-lookup"><span data-stu-id="5a379-157">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="5a379-158">Isso ocorre porque os argumentos e os parâmetros do método da classe base são definidos como inteiros de 16 bits no Visual Basic 6.0, mas eles são expostos como inteiros de 16 bits do tipo `Short` em versões posteriores do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a379-158">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="5a379-159">A nova função aceita inteiros de 32 bits e sobrecargas de função da classe base.</span><span class="sxs-lookup"><span data-stu-id="5a379-159">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="5a379-160">Ao trabalhar com objetos COM, certifique-se de que você verifique os tipos de dados e tamanho de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5a379-160">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="5a379-161">Por exemplo, quando você estiver usando um objeto COM que aceita um objeto de coleção do Visual Basic 6.0 como um argumento, você não pode fornecer uma coleção de uma versão posterior do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a379-161">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="5a379-162">Propriedades e métodos herdados de classes COM podem ser substituídos, que significa que você pode declarar uma propriedade local ou um método que substitui uma propriedade ou método herdado de uma classe COM base.</span><span class="sxs-lookup"><span data-stu-id="5a379-162">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="5a379-163">As regras de substituição COM as propriedades herdadas são semelhantes às regras de substituição de outras propriedades e métodos com as seguintes exceções:</span><span class="sxs-lookup"><span data-stu-id="5a379-163">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="5a379-164">Se você substituir qualquer propriedade ou método herdado de uma classe COM, você deve substituir todas as outras propriedades e métodos herdados.</span><span class="sxs-lookup"><span data-stu-id="5a379-164">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="5a379-165">Propriedades que usam `ByRef` parâmetros não podem ser substituídos.</span><span class="sxs-lookup"><span data-stu-id="5a379-165">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a379-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a379-166">See Also</span></span>  
 <span data-ttu-id="5a379-167">[Interoperabilidade COM em aplicativos do .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span><span class="sxs-lookup"><span data-stu-id="5a379-167">[COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span></span>  
<span data-ttu-id="5a379-168"> [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5a379-168"> [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) </span></span>  
<span data-ttu-id="5a379-169"> [Tipo de Dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="5a379-169"> [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)</span></span>
