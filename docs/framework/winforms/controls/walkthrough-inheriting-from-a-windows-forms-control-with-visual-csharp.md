---
title: 'Passo a passo: Herdando um controle do Windows Forms com Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
ms.openlocfilehash: c06639ef2f2ced8bd128adea636efe8be1715764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931017"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="eb074-102">Passo a passo: Herdar de um controle de Windows Forms com o Visual C\#</span><span class="sxs-lookup"><span data-stu-id="eb074-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C\#</span></span>
<span data-ttu-id="eb074-103">Com o C#Visual, você pode criar controles personalizados avançados por meio de *herança*.</span><span class="sxs-lookup"><span data-stu-id="eb074-103">With Visual C#, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="eb074-104">Com a herança, você é capaz de criar controles que mantêm todas as funcionalidades inerentes de controles padrão dos Windows Forms, mas também incorporam funcionalidades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="eb074-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="eb074-105">Neste passo a passo, você criará um controle herdado simples chamado `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="eb074-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="eb074-106">Esse botão herdará a funcionalidade do controle de <xref:System.Windows.Forms.Button> Windows Forms padrão e apresentará uma propriedade personalizada chamada `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="eb074-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="eb074-107">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="eb074-107">Creating the Project</span></span>
 <span data-ttu-id="eb074-108">Quando cria um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e para garantir que o componente padrão estará no namespace correto.</span><span class="sxs-lookup"><span data-stu-id="eb074-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="eb074-109">Para criar a biblioteca de controle ValueButtonLib e o controle ValueButton</span><span class="sxs-lookup"><span data-stu-id="eb074-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="eb074-110">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto** para abrir a caixa de diálogo **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="eb074-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="eb074-111">Selecione o modelo de projeto da **biblioteca de controle de Windows Forms** na C# lista de projetos visuais `ValueButtonLib` e digite na caixa **nome** .</span><span class="sxs-lookup"><span data-stu-id="eb074-111">Select the **Windows Forms Control Library** project template from the list of Visual C# Projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="eb074-112">O nome do projeto, `ValueButtonLib`, também é atribuído ao namespace raiz por padrão.</span><span class="sxs-lookup"><span data-stu-id="eb074-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="eb074-113">O namespace raiz é usado para qualificar os nomes dos componentes no assembly.</span><span class="sxs-lookup"><span data-stu-id="eb074-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="eb074-114">Por exemplo, se dois assemblies fornecerem componentes chamados `ValueButton`, você poderá especificar o componente `ValueButton` usando `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="eb074-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="eb074-115">Para obter mais informações, consulte [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb074-115">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>

3. <span data-ttu-id="eb074-116">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **UserControl1.cs** e escolha **Renomear** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="eb074-116">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="eb074-117">Altere o nome de arquivo para `ValueButton.cs`.</span><span class="sxs-lookup"><span data-stu-id="eb074-117">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="eb074-118">Clique no botão **Sim** quando solicitado se desejar renomear todas as referências ao elemento de código '`UserControl1`'.</span><span class="sxs-lookup"><span data-stu-id="eb074-118">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>

4. <span data-ttu-id="eb074-119">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **ValueButton.cs** e selecione **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="eb074-119">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>

5. <span data-ttu-id="eb074-120">Localize a `class` linha de instrução `public partial class ValueButton`, e altere o tipo do <xref:System.Windows.Forms.UserControl> qual <xref:System.Windows.Forms.Button>esse controle herda.</span><span class="sxs-lookup"><span data-stu-id="eb074-120">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="eb074-121">Isso permite que o controle herdado herde toda a funcionalidade <xref:System.Windows.Forms.Button> do controle.</span><span class="sxs-lookup"><span data-stu-id="eb074-121">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

6. <span data-ttu-id="eb074-122">No **Gerenciador de Soluções**, abra o nó **ValueButton.cs** para exibir o arquivo de código gerado pelo designer, **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="eb074-122">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="eb074-123">Abra esse arquivo no **Editor de Códigos**.</span><span class="sxs-lookup"><span data-stu-id="eb074-123">Open this file in the **Code Editor**.</span></span>

7. <span data-ttu-id="eb074-124">Localize o `InitializeComponent` método e remova a linha que atribui a <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="eb074-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="eb074-125">Esta propriedade não existe no <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="eb074-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="eb074-126">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="eb074-126">From the **File** menu, choose **Save All** to save the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eb074-127">Um designer visual não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="eb074-127">A visual designer is no longer available.</span></span> <span data-ttu-id="eb074-128">Como o <xref:System.Windows.Forms.Button> controle faz sua própria pintura, você não pode modificar sua aparência no designer.</span><span class="sxs-lookup"><span data-stu-id="eb074-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="eb074-129">Sua representação visual será exatamente igual à da classe da qual ela herda (ou seja, <xref:System.Windows.Forms.Button>), a menos que seja modificada no código.</span><span class="sxs-lookup"><span data-stu-id="eb074-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="eb074-130">Você ainda pode adicionar componentes, que não têm uma interface do usuário, à superfície de design.</span><span class="sxs-lookup"><span data-stu-id="eb074-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="eb074-131">Adicionando uma propriedade ao controle herdado</span><span class="sxs-lookup"><span data-stu-id="eb074-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="eb074-132">Um uso possível dos controles herdados dos Windows Forms é a criação de controles que são idênticos em termos de aparência a controles padrão dos Windows Forms, mas que expõem propriedades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="eb074-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="eb074-133">Nesta seção, você adicionará uma propriedade chamada `ButtonValue` ao controle.</span><span class="sxs-lookup"><span data-stu-id="eb074-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="eb074-134">Para adicionar a propriedade de valor</span><span class="sxs-lookup"><span data-stu-id="eb074-134">To add the Value property</span></span>

1. <span data-ttu-id="eb074-135">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **ValueButton.cs** e, depois, clique em **Exibir Código** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="eb074-135">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="eb074-136">Localize a instrução `class`.</span><span class="sxs-lookup"><span data-stu-id="eb074-136">Locate the `class` statement.</span></span> <span data-ttu-id="eb074-137">Cole o código a seguir imediatamente depois de `{`:</span><span class="sxs-lookup"><span data-stu-id="eb074-137">Immediately after the `{`, type the following code:</span></span>

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     <span data-ttu-id="eb074-138">Esse código define os métodos segundo os quais a propriedade `ButtonValue` é armazenada e recuperada.</span><span class="sxs-lookup"><span data-stu-id="eb074-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="eb074-139">A instrução `get` define o valor retornado como o valor que é armazenado na variável particular `varValue` e a instrução `set` define o valor da variável particular usando a palavra-chave `value`.</span><span class="sxs-lookup"><span data-stu-id="eb074-139">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>

3. <span data-ttu-id="eb074-140">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="eb074-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="eb074-141">Testando seu controle</span><span class="sxs-lookup"><span data-stu-id="eb074-141">Testing Your Control</span></span>
 <span data-ttu-id="eb074-142">Controles não são projetos autônomos; eles devem ser hospedados em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="eb074-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="eb074-143">Para testar seu controle, você precisa fornecer um projeto de teste em que ele será executado.</span><span class="sxs-lookup"><span data-stu-id="eb074-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="eb074-144">Você também precisa tornar seu controle acessível para o projeto de teste compilando-o.</span><span class="sxs-lookup"><span data-stu-id="eb074-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="eb074-145">Nesta seção, você compilará seu controle e o testará em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="eb074-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="eb074-146">Para compilar seu controle</span><span class="sxs-lookup"><span data-stu-id="eb074-146">To build your control</span></span>

1. <span data-ttu-id="eb074-147">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="eb074-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="eb074-148">O build deve ser bem-sucedido, sem avisos ou erros do compilador.</span><span class="sxs-lookup"><span data-stu-id="eb074-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="eb074-149">Para criar um projeto de teste</span><span class="sxs-lookup"><span data-stu-id="eb074-149">To create a test project</span></span>

1. <span data-ttu-id="eb074-150">No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto** para abrir a caixa de diálogo **Adicionar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="eb074-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="eb074-151">Selecione o nó **Windows**, abaixo de **Visual C#** e clique em **Aplicativo dos Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="eb074-151">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="eb074-152">Na caixa **Nome**, digite `Test`.</span><span class="sxs-lookup"><span data-stu-id="eb074-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="eb074-153">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** de seu projeto de teste e selecione **Adicionar Referência** no menu de atalho para exibir a caixa de diálogo **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="eb074-153">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="eb074-154">Clique na guia rotulada como **Projetos**.</span><span class="sxs-lookup"><span data-stu-id="eb074-154">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="eb074-155">O projeto `ValueButtonLib` estará listado em **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="eb074-155">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="eb074-156">Clique duas vezes no projeto para adicionar a referência ao projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="eb074-156">Double-click the project to add the reference to the test project.</span></span>

6. <span data-ttu-id="eb074-157">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Testar** e selecione **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="eb074-157">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="eb074-158">Para adicionar o controle ao formulário</span><span class="sxs-lookup"><span data-stu-id="eb074-158">To add your control to the form</span></span>

1. <span data-ttu-id="eb074-159">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1.cs** e selecione **Designer de Modo de Exibição** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="eb074-159">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="eb074-160">Na **Caixa de Ferramentas**, clique em **Componentes de ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="eb074-160">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="eb074-161">Clique duas vezes em **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="eb074-161">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="eb074-162">Um **ValueButton** aparece no formulário.</span><span class="sxs-lookup"><span data-stu-id="eb074-162">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="eb074-163">Clique com o botão direito do mouse em **ValueButton** e selecione **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="eb074-163">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="eb074-164">Na janela **Propriedades**, examine as propriedades desse controle.</span><span class="sxs-lookup"><span data-stu-id="eb074-164">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="eb074-165">Observe que elas são idênticas às propriedades expostas por um botão padrão, exceto pelo fato de que há uma propriedade adicional, `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="eb074-165">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="eb074-166">Defina a propriedade `ButtonValue` como `5`.</span><span class="sxs-lookup"><span data-stu-id="eb074-166">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="eb074-167">Na guia **todos os Windows Forms** da **caixa de ferramentas**, clique duas vezes em **rótulo** para <xref:System.Windows.Forms.Label> adicionar um controle ao formulário.</span><span class="sxs-lookup"><span data-stu-id="eb074-167">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="eb074-168">Reposicione o rótulo no centro do formulário.</span><span class="sxs-lookup"><span data-stu-id="eb074-168">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="eb074-169">Clique duas vezes em `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="eb074-169">Double-click `valueButton1`.</span></span>

     <span data-ttu-id="eb074-170">O **Editor de Códigos** é aberto no evento `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="eb074-170">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>

9. <span data-ttu-id="eb074-171">Insira a seguinte linha de código.</span><span class="sxs-lookup"><span data-stu-id="eb074-171">Insert the following line of code.</span></span>

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. <span data-ttu-id="eb074-172">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Teste** e escolha **Definir como Projeto de Inicialização** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="eb074-172">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="eb074-173">No menu **Depuração**, selecione **Iniciar Depuração**.</span><span class="sxs-lookup"><span data-stu-id="eb074-173">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="eb074-174">`Form1` é exibido.</span><span class="sxs-lookup"><span data-stu-id="eb074-174">`Form1` appears.</span></span>

12. <span data-ttu-id="eb074-175">Clique em `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="eb074-175">Click `valueButton1`.</span></span>

     <span data-ttu-id="eb074-176">O numeral "5" é exibido em `label1`, demonstrando que a propriedade `ButtonValue` de seu controle herdado foi passada para `label1` por meio do método `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="eb074-176">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="eb074-177">Portanto, seu controle `ValueButton` herda todas as funcionalidades do botão padrão dos Windows Forms, mas expõe uma propriedade adicional personalizada.</span><span class="sxs-lookup"><span data-stu-id="eb074-177">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb074-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb074-178">See also</span></span>

- [<span data-ttu-id="eb074-179">Como: Exibir um controle na caixa de diálogo escolher itens da Toolbox</span><span class="sxs-lookup"><span data-stu-id="eb074-179">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="eb074-180">Passo a passo: Criando um controle composto com VisualC#</span><span class="sxs-lookup"><span data-stu-id="eb074-180">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
