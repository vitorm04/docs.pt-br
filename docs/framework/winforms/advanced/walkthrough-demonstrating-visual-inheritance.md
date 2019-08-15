---
title: 'Passo a passo: demonstrando herança visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 6fd504269ae9afbfd02b58276582a644674e1e0f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040315"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="4763e-102">Passo a passo: demonstrando herança visual</span><span class="sxs-lookup"><span data-stu-id="4763e-102">Walkthrough: Demonstrating Visual Inheritance</span></span>

<span data-ttu-id="4763e-103">A herança visual permite que você veja os controles no formulário de base e adicione novos controles.</span><span class="sxs-lookup"><span data-stu-id="4763e-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="4763e-104">Neste passo a passo, você criará um formulário de base e o compilará em uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="4763e-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="4763e-105">Você importará esta biblioteca de classes em outro projeto e criará um novo formulário que herda do formulário de base.</span><span class="sxs-lookup"><span data-stu-id="4763e-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="4763e-106">Durante este passo a passo, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="4763e-106">During this walkthrough, you will learn how to:</span></span>

- <span data-ttu-id="4763e-107">Criar um projeto de biblioteca de classes que contém um formulário de base.</span><span class="sxs-lookup"><span data-stu-id="4763e-107">Create a class library project containing a base form.</span></span>

- <span data-ttu-id="4763e-108">Adicionar um botão com propriedades que as classes derivadas do formulário de base podem modificar.</span><span class="sxs-lookup"><span data-stu-id="4763e-108">Add a button with properties that derived classes of the base form can modify.</span></span>

- <span data-ttu-id="4763e-109">Adicionar um botão que não pode ser modificado por herdeiros do formulário de base.</span><span class="sxs-lookup"><span data-stu-id="4763e-109">Add a button that cannot be modified by inheritors of the base form.</span></span>

- <span data-ttu-id="4763e-110">Criar um projeto que contém um formulário que herda de `BaseForm`.</span><span class="sxs-lookup"><span data-stu-id="4763e-110">Create a project containing a form that inherits from `BaseForm`.</span></span>

<span data-ttu-id="4763e-111">Por fim, este passo a passo demonstrará a diferença entre controles particulares e protegidos em um formulário herdado.</span><span class="sxs-lookup"><span data-stu-id="4763e-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>

> [!CAUTION]
> <span data-ttu-id="4763e-112">Nem todos os controles dão suporte à herança visual de um formulário de base.</span><span class="sxs-lookup"><span data-stu-id="4763e-112">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="4763e-113">Os seguintes controles não dão suporte ao cenário descrito neste passo a passo:</span><span class="sxs-lookup"><span data-stu-id="4763e-113">The following controls do not support the scenario described in this walkthrough:</span></span>
>
>  <xref:System.Windows.Forms.WebBrowser>
>
>  <xref:System.Windows.Forms.ToolStrip>
>
>  <xref:System.Windows.Forms.ToolStripPanel>
>
>  <xref:System.Windows.Forms.TableLayoutPanel>
>
>  <xref:System.Windows.Forms.FlowLayoutPanel>
>
>  <xref:System.Windows.Forms.DataGridView>
>
>  <span data-ttu-id="4763e-114">Esses controles no formulário herdado sempre são somente leitura, independentemente dos modificadores que você usar (`private`, `protected` ou `public`).</span><span class="sxs-lookup"><span data-stu-id="4763e-114">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>

## <a name="create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="4763e-115">Criar um projeto de biblioteca de classes que contém um formulário base</span><span class="sxs-lookup"><span data-stu-id="4763e-115">Create a class library project containing a base form</span></span>

1. <span data-ttu-id="4763e-116">No Visual Studio, no menu **arquivo** , escolha **novo** > **projeto** para abrir a caixa de diálogo **novo projeto** .</span><span class="sxs-lookup"><span data-stu-id="4763e-116">In Visual Studio, from the **File** menu, choose **New** > **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="4763e-117">Crie um aplicativo dos Windows Forms chamado `BaseFormLibrary`.</span><span class="sxs-lookup"><span data-stu-id="4763e-117">Create a Windows Forms application named `BaseFormLibrary`.</span></span>

3. <span data-ttu-id="4763e-118">Para criar uma biblioteca de classes em vez de um aplicativo padrão dos Windows Forms, no **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do projeto **BaseFormLibrary** e, em seguida, selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="4763e-118">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>

4. <span data-ttu-id="4763e-119">Nas propriedades do projeto, altere o **Tipo de saída** de **Aplicativo do Windows** para **Biblioteca de Classes**.</span><span class="sxs-lookup"><span data-stu-id="4763e-119">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>

5. <span data-ttu-id="4763e-120">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto e os arquivos no local padrão.</span><span class="sxs-lookup"><span data-stu-id="4763e-120">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>

 <span data-ttu-id="4763e-121">Os dois procedimentos seguintes adicionam botões ao formulário de base.</span><span class="sxs-lookup"><span data-stu-id="4763e-121">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="4763e-122">Para demonstrar a herança visual, você dará aos botões diferentes níveis de acesso configurando suas propriedades `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="4763e-122">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="4763e-123">Adicionar um botão que os herdeiros do formulário base podem modificar</span><span class="sxs-lookup"><span data-stu-id="4763e-123">Add a button that inheritors of the base form can modify</span></span>

1. <span data-ttu-id="4763e-124">Abra **Form1** no designer.</span><span class="sxs-lookup"><span data-stu-id="4763e-124">Open **Form1** in the designer.</span></span>

2. <span data-ttu-id="4763e-125">Na guia **Todos os Windows Forms** da **Caixa de Ferramentas**, clique duas vezes em **Botão** para adicionar um botão ao formulário.</span><span class="sxs-lookup"><span data-stu-id="4763e-125">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="4763e-126">Use o mouse para posicionar e redimensionar o botão.</span><span class="sxs-lookup"><span data-stu-id="4763e-126">Use the mouse to position and resize the button.</span></span>

3. <span data-ttu-id="4763e-127">Na janela Propriedades, defina as seguintes propriedades do botão:</span><span class="sxs-lookup"><span data-stu-id="4763e-127">In the Properties window, set the following properties of the button:</span></span>

    - <span data-ttu-id="4763e-128">Defina a propriedade **Texto** como **Say Hello**.</span><span class="sxs-lookup"><span data-stu-id="4763e-128">Set the **Text** property to **Say Hello**.</span></span>

    - <span data-ttu-id="4763e-129">Defina a propriedade **(Nome)** como **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="4763e-129">Set the **(Name)** property to **btnProtected**.</span></span>

    - <span data-ttu-id="4763e-130">Defina a Propriedade modificadores como **protegida**.</span><span class="sxs-lookup"><span data-stu-id="4763e-130">Set the **Modifiers** property to **Protected**.</span></span> <span data-ttu-id="4763e-131">Isso possibilita que formulários que herdam de **Form1** modifiquem as propriedades de **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="4763e-131">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>

4. <span data-ttu-id="4763e-132">Clique duas vezes no botão **Say Hello** para adicionar um manipulador de eventos para o evento **Clique**.</span><span class="sxs-lookup"><span data-stu-id="4763e-132">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>

5. <span data-ttu-id="4763e-133">Adicione a seguinte linha de código ao manipulador de eventos:</span><span class="sxs-lookup"><span data-stu-id="4763e-133">Add the following line of code to the event handler:</span></span>

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="4763e-134">Adicionar um botão que não pode ser modificado por herdeiros do formulário base</span><span class="sxs-lookup"><span data-stu-id="4763e-134">Add a button that cannot be modified by inheritors of the base form</span></span>

1. <span data-ttu-id="4763e-135">Passe para o modo de exibição de Design clicando na guia **Form1.vb [Design], Form1.cs [Design] ou Form1.jsl [Design]** acima do editor de código ou pressionando F7.</span><span class="sxs-lookup"><span data-stu-id="4763e-135">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>

2. <span data-ttu-id="4763e-136">Adicione um segundo botão e defina suas propriedades da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4763e-136">Add a second button and set its properties as follows:</span></span>

    - <span data-ttu-id="4763e-137">Defina a propriedade **Texto** como **Say Goodbye**.</span><span class="sxs-lookup"><span data-stu-id="4763e-137">Set the **Text** property to **Say Goodbye**.</span></span>

    - <span data-ttu-id="4763e-138">Defina a propriedade **(Nome)** como **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="4763e-138">Set the **(Name)** property to **btnPrivate**.</span></span>

    - <span data-ttu-id="4763e-139">Defina a propriedade **(Nome)** como **Particular**.</span><span class="sxs-lookup"><span data-stu-id="4763e-139">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="4763e-140">Isso possibilita que formulários que herdam de **Form1** modifiquem as propriedades de **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="4763e-140">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>

3. <span data-ttu-id="4763e-141">Clique duas vezes no botão **Say Goodbye** para adicionar um manipulador de eventos para o evento **Clique**.</span><span class="sxs-lookup"><span data-stu-id="4763e-141">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="4763e-142">Coloque a seguinte linha de código no procedimento do evento:</span><span class="sxs-lookup"><span data-stu-id="4763e-142">Place the following line of code in the event procedure:</span></span>

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. <span data-ttu-id="4763e-143">Do menu **Compilação**, escolha **Compilar Biblioteca de BaseForm** para compilar a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="4763e-143">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>

     <span data-ttu-id="4763e-144">Após a biblioteca ter sido compilada, você pode criar um novo projeto que herda do formulário que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="4763e-144">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="4763e-145">Criar um projeto que contém um formulário herdado do formulário base</span><span class="sxs-lookup"><span data-stu-id="4763e-145">Create a project containing a form that inherits from the base form</span></span>

1. <span data-ttu-id="4763e-146">No menu **Arquivo**, escolha **Adicionar** e selecione **Novo Projeto** para abrir a caixa de diálogo **Adicionar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="4763e-146">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="4763e-147">Crie um aplicativo dos Windows Forms chamado `InheritanceTest`.</span><span class="sxs-lookup"><span data-stu-id="4763e-147">Create a Windows Forms application named `InheritanceTest`.</span></span>

## <a name="add-an-inherited-form"></a><span data-ttu-id="4763e-148">Adicionar um formulário herdado</span><span class="sxs-lookup"><span data-stu-id="4763e-148">Add an inherited form</span></span>

1. <span data-ttu-id="4763e-149">Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **InheritanceTest** , selecione **Adicionar**e, em seguida, selecione **novo item**.</span><span class="sxs-lookup"><span data-stu-id="4763e-149">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select **New Item**.</span></span>

2. <span data-ttu-id="4763e-150">Na caixa de diálogo **Adicionar Novo Item**, selecione a categoria **Windows Forms** (se você tiver uma lista de categorias) e selecione o modelo **Formulário Herdado**.</span><span class="sxs-lookup"><span data-stu-id="4763e-150">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>

3. <span data-ttu-id="4763e-151">Deixe o nome padrão `Form2` e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="4763e-151">Leave the default name of `Form2` and then click **Add**.</span></span>

4. <span data-ttu-id="4763e-152">Na caixa de diálogo **Selecionador de Herança**, selecione **Form1** do projeto **BaseFormLibrary** como o formulário do qual herdar e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="4763e-152">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>

     <span data-ttu-id="4763e-153">Isso cria um formulário no projeto **InheritanceTest** que deriva de formulário em **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="4763e-153">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>

5. <span data-ttu-id="4763e-154">Abra o formulário herdado (**Form2**) no designer clicando duas vezes nele, se ele ainda não estiver aberto.</span><span class="sxs-lookup"><span data-stu-id="4763e-154">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>

     <span data-ttu-id="4763e-155">No designer, os botões herdados têm um símbolo (</span><span class="sxs-lookup"><span data-stu-id="4763e-155">In the designer, the inherited buttons have a symbol (</span></span>![Captura de tela do símbolo de herança de Visual Basic.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)<span data-ttu-id="4763e-157">) no seu canto superior, indicando que eles são herdados.</span><span class="sxs-lookup"><span data-stu-id="4763e-157">) in their upper corner, indicating they are inherited.</span></span>

6. <span data-ttu-id="4763e-158">Selecione o botão **Say Hello** e observe as alças de redimensionamento.</span><span class="sxs-lookup"><span data-stu-id="4763e-158">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="4763e-159">Como esse botão é protegido, os herdeiros podem movê-lo, redimensioná-lo, alterar sua legenda e fazer outras modificações.</span><span class="sxs-lookup"><span data-stu-id="4763e-159">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>

7. <span data-ttu-id="4763e-160">Selecione o botão particular **Say Goodbye** e observe que ele não tem alças de redimensionamento.</span><span class="sxs-lookup"><span data-stu-id="4763e-160">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="4763e-161">Além disso, na janela **Propriedades**, as propriedades deste botão ficam cinza para indicar que não podem ser modificadas.</span><span class="sxs-lookup"><span data-stu-id="4763e-161">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>

8. <span data-ttu-id="4763e-162">Se você estiver usando o C#Visual:</span><span class="sxs-lookup"><span data-stu-id="4763e-162">If you are using Visual C#:</span></span>

    1. <span data-ttu-id="4763e-163">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1** no projeto **InheritanceTest** e selecione **Excluir**.</span><span class="sxs-lookup"><span data-stu-id="4763e-163">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="4763e-164">Na caixa de mensagem que aparece, clique em **OK** para confirmar a exclusão.</span><span class="sxs-lookup"><span data-stu-id="4763e-164">In the message box that appears, click **OK** to confirm the deletion.</span></span>

    2. <span data-ttu-id="4763e-165">Abra o arquivo Program.cs e altere a linha `Application.Run(new Form1());` para `Application.Run(new Form2());`.</span><span class="sxs-lookup"><span data-stu-id="4763e-165">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>

9. <span data-ttu-id="4763e-166">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **InheritanceTest** e selecione **Definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="4763e-166">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>

10. <span data-ttu-id="4763e-167">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **InheritanceTest** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="4763e-167">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>

11. <span data-ttu-id="4763e-168">Na página de propriedades de **InheritanceTest**, defina o **Objeto de Inicialização** para ser o formulário herdado (**Form2**).</span><span class="sxs-lookup"><span data-stu-id="4763e-168">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>

12. <span data-ttu-id="4763e-169">Pressione **F5** para executar o aplicativo e observe o comportamento do formulário herdado.</span><span class="sxs-lookup"><span data-stu-id="4763e-169">Press **F5** to run the application, and observe the behavior of the inherited form.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4763e-170">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4763e-170">Next steps</span></span>

<span data-ttu-id="4763e-171">A herança para controles de usuário funciona basicamente da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="4763e-171">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="4763e-172">Abra um novo projeto de biblioteca de classes e adicione um controle de usuário.</span><span class="sxs-lookup"><span data-stu-id="4763e-172">Open a new class library project and add a user control.</span></span> <span data-ttu-id="4763e-173">Coloque os controles constituintes nele e compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="4763e-173">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="4763e-174">Abra outro novo projeto de biblioteca de classes e adicione uma referência à biblioteca de classes compilada.</span><span class="sxs-lookup"><span data-stu-id="4763e-174">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="4763e-175">Além disso, tente adicionar um controle herdado (por meio da caixa de diálogo **Adicionar Novos Itens**) ao projeto e usar o **Selecionador de Herança**.</span><span class="sxs-lookup"><span data-stu-id="4763e-175">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="4763e-176">Adicione um controle de usuário e altere a `Inherits` instrução`:` (in C#Visual).</span><span class="sxs-lookup"><span data-stu-id="4763e-176">Add a user control, and change the `Inherits` (`:` in Visual C#) statement.</span></span> <span data-ttu-id="4763e-177">Para obter mais informações, confira [Como: Herdar](how-to-inherit-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4763e-177">For more information, see [How to: Inherit Windows Forms](how-to-inherit-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4763e-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4763e-178">See also</span></span>

- [<span data-ttu-id="4763e-179">Como: Herdar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4763e-179">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="4763e-180">Herança Visual dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4763e-180">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="4763e-181">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4763e-181">Windows Forms</span></span>](../index.md)
