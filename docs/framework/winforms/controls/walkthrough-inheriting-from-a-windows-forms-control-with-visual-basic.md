---
title: 'Passo a passo: Herdar de um controle do Windows Forms com Visual Basic'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 0891b64fdb26953ab90f3da931f04513ac9e8bcf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040222"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="29f14-102">Passo a passo: Herdar de um controle do Windows Forms com Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29f14-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="29f14-103">Com Visual Basic, você pode criar controles personalizados avançados por meio de *herança*.</span><span class="sxs-lookup"><span data-stu-id="29f14-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="29f14-104">Com a herança, você é capaz de criar controles que mantêm todas as funcionalidades inerentes de controles padrão dos Windows Forms, mas também incorporam funcionalidades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="29f14-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="29f14-105">Neste passo a passo, você criará um controle herdado simples chamado `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="29f14-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="29f14-106">Esse botão herdará a funcionalidade do controle de <xref:System.Windows.Forms.Button> Windows Forms padrão e apresentará uma propriedade personalizada chamada `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="29f14-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="29f14-107">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="29f14-107">Creating the Project</span></span>
 <span data-ttu-id="29f14-108">Quando cria um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e para garantir que o componente padrão estará no namespace correto.</span><span class="sxs-lookup"><span data-stu-id="29f14-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="29f14-109">Para criar a biblioteca de controle ValueButtonLib e o controle ValueButton</span><span class="sxs-lookup"><span data-stu-id="29f14-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="29f14-110">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto** para abrir a caixa de diálogo **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="29f14-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="29f14-111">Selecione o modelo de projeto da **biblioteca de controle de Windows Forms** na lista de projetos de `ValueButtonLib` Visual Basic e digite na caixa **nome** .</span><span class="sxs-lookup"><span data-stu-id="29f14-111">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="29f14-112">O nome do projeto, `ValueButtonLib`, também é atribuído ao namespace raiz por padrão.</span><span class="sxs-lookup"><span data-stu-id="29f14-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="29f14-113">O namespace raiz é usado para qualificar os nomes dos componentes no assembly.</span><span class="sxs-lookup"><span data-stu-id="29f14-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="29f14-114">Por exemplo, se dois assemblies fornecerem componentes chamados `ValueButton`, você poderá especificar o componente `ValueButton` usando `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="29f14-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="29f14-115">Para obter mais informações, consulte [Namespaces no Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="29f14-115">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>

3. <span data-ttu-id="29f14-116">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **UserControl1.vb** e escolha **Renomear** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="29f14-116">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="29f14-117">Altere o nome de arquivo para `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="29f14-117">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="29f14-118">Clique no botão **Sim** quando for solicitado se quiser renomear todas as referências ao elemento de código “UserControl1”.</span><span class="sxs-lookup"><span data-stu-id="29f14-118">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>

4. <span data-ttu-id="29f14-119">Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="29f14-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="29f14-120">Abra o nó **ValueButton.vb** para exibir o arquivo de código gerado pelo designer, **ValueButton.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="29f14-120">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="29f14-121">Abra esse arquivo no **Editor de Códigos**.</span><span class="sxs-lookup"><span data-stu-id="29f14-121">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="29f14-122">Localize a `Class` instrução, `Partial Public Class ValueButton`e altere o tipo do <xref:System.Windows.Forms.UserControl> qual <xref:System.Windows.Forms.Button>esse controle herda.</span><span class="sxs-lookup"><span data-stu-id="29f14-122">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="29f14-123">Isso permite que o controle herdado herde toda a funcionalidade <xref:System.Windows.Forms.Button> do controle.</span><span class="sxs-lookup"><span data-stu-id="29f14-123">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="29f14-124">Localize o `InitializeComponent` método e remova a linha que atribui a <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="29f14-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="29f14-125">Esta propriedade não existe no <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="29f14-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="29f14-126">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="29f14-126">From the **File** menu, choose **Save All** to save the project.</span></span>

     <span data-ttu-id="29f14-127">Observe que um designer visual não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="29f14-127">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="29f14-128">Como o <xref:System.Windows.Forms.Button> controle faz sua própria pintura, você não pode modificar sua aparência no designer.</span><span class="sxs-lookup"><span data-stu-id="29f14-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="29f14-129">Sua representação visual será exatamente igual à da classe da qual ela herda (ou seja, <xref:System.Windows.Forms.Button>), a menos que seja modificada no código.</span><span class="sxs-lookup"><span data-stu-id="29f14-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>

> [!NOTE]
>  <span data-ttu-id="29f14-130">Você ainda pode adicionar componentes, que não têm uma interface do usuário, à superfície de design.</span><span class="sxs-lookup"><span data-stu-id="29f14-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="29f14-131">Adicionando uma propriedade ao controle herdado</span><span class="sxs-lookup"><span data-stu-id="29f14-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="29f14-132">Um uso possível dos controles herdados dos Windows Forms é a criação de controles que são idênticos em termos de aparência e comportamento a controles padrão dos Windows Forms, mas que expõem propriedades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="29f14-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="29f14-133">Nesta seção, você adicionará uma propriedade chamada `ButtonValue` ao controle.</span><span class="sxs-lookup"><span data-stu-id="29f14-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="29f14-134">Para adicionar a propriedade de valor</span><span class="sxs-lookup"><span data-stu-id="29f14-134">To add the Value property</span></span>

1. <span data-ttu-id="29f14-135">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **ValueButton.vb** e, depois, clique em **Exibir Código** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="29f14-135">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="29f14-136">Localize a instrução `Public Class ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="29f14-136">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="29f14-137">Logo abaixo dessa instrução, digite o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="29f14-137">Immediately beneath this statement, type the following code:</span></span>

    ```vb
    ' Creates the private variable that will store the value of your
    ' property.
    Private varValue as integer
    ' Declares the property.
    Property ButtonValue() as Integer
    ' Sets the method for retrieving the value of your property.
       Get
          Return varValue
       End Get
    ' Sets the method for setting the value of your property.
       Set(ByVal Value as Integer)
          varValue = Value
       End Set
    End Property
    ```

     <span data-ttu-id="29f14-138">Esse código define os métodos segundo os quais a propriedade `ButtonValue` é armazenada e recuperada.</span><span class="sxs-lookup"><span data-stu-id="29f14-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="29f14-139">A instrução `Get` define o valor retornado como o valor que é armazenado na variável particular `varValue` e a instrução `Set` define o valor da variável particular usando a palavra-chave `Value`.</span><span class="sxs-lookup"><span data-stu-id="29f14-139">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>

3. <span data-ttu-id="29f14-140">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="29f14-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="29f14-141">Testando seu controle</span><span class="sxs-lookup"><span data-stu-id="29f14-141">Testing Your Control</span></span>
 <span data-ttu-id="29f14-142">Controles não são projetos autônomos; eles devem ser hospedados em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="29f14-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="29f14-143">Para testar seu controle, você precisa fornecer um projeto de teste em que ele será executado.</span><span class="sxs-lookup"><span data-stu-id="29f14-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="29f14-144">Você também precisa tornar seu controle acessível para o projeto de teste compilando-o.</span><span class="sxs-lookup"><span data-stu-id="29f14-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="29f14-145">Nesta seção, você compilará seu controle e o testará em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="29f14-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="29f14-146">Para compilar seu controle</span><span class="sxs-lookup"><span data-stu-id="29f14-146">To build your control</span></span>

1. <span data-ttu-id="29f14-147">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="29f14-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="29f14-148">O build deve ser bem-sucedido, sem avisos ou erros do compilador.</span><span class="sxs-lookup"><span data-stu-id="29f14-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="29f14-149">Para criar um projeto de teste</span><span class="sxs-lookup"><span data-stu-id="29f14-149">To create a test project</span></span>

1. <span data-ttu-id="29f14-150">No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto** para abrir a caixa de diálogo **Adicionar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="29f14-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="29f14-151">Selecione o nó projetos de Visual Basic e clique em **Windows Forms aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="29f14-151">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="29f14-152">Na caixa **Nome**, digite `Test`.</span><span class="sxs-lookup"><span data-stu-id="29f14-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="29f14-153">Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="29f14-153">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="29f14-154">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** de seu projeto de teste e selecione **Adicionar Referência** no menu de atalho para exibir a caixa de diálogo **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="29f14-154">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

6. <span data-ttu-id="29f14-155">Clique na guia **Projetos**.</span><span class="sxs-lookup"><span data-stu-id="29f14-155">Click the **Projects** tab.</span></span>

7. <span data-ttu-id="29f14-156">Clique na guia rotulada como **Projetos**.</span><span class="sxs-lookup"><span data-stu-id="29f14-156">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="29f14-157">O projeto `ValueButtonLib` estará listado em **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="29f14-157">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="29f14-158">Clique duas vezes no projeto para adicionar a referência ao projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="29f14-158">Double-click the project to add the reference to the test project.</span></span>

8. <span data-ttu-id="29f14-159">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Testar** e selecione **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="29f14-159">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="29f14-160">Para adicionar o controle ao formulário</span><span class="sxs-lookup"><span data-stu-id="29f14-160">To add your control to the form</span></span>

1. <span data-ttu-id="29f14-161">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1.vb** e selecione **Designer de Modo de Exibição** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="29f14-161">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="29f14-162">Na **Caixa de Ferramentas**, clique em **Componentes de ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="29f14-162">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="29f14-163">Clique duas vezes em **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="29f14-163">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="29f14-164">Um **ValueButton** aparece no formulário.</span><span class="sxs-lookup"><span data-stu-id="29f14-164">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="29f14-165">Clique com o botão direito do mouse em **ValueButton** e selecione **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="29f14-165">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="29f14-166">Na janela **Propriedades**, examine as propriedades desse controle.</span><span class="sxs-lookup"><span data-stu-id="29f14-166">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="29f14-167">Observe que elas são idênticas às propriedades expostas por um botão padrão, exceto pelo fato de que há uma propriedade adicional, `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="29f14-167">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="29f14-168">Defina a propriedade `ButtonValue` como `5`.</span><span class="sxs-lookup"><span data-stu-id="29f14-168">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="29f14-169">Na guia **todos os Windows Forms** da **caixa de ferramentas**, clique duas vezes em **rótulo** para <xref:System.Windows.Forms.Label> adicionar um controle ao formulário.</span><span class="sxs-lookup"><span data-stu-id="29f14-169">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="29f14-170">Reposicione o rótulo no centro do formulário.</span><span class="sxs-lookup"><span data-stu-id="29f14-170">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="29f14-171">Clique duas vezes em `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="29f14-171">Double-click `ValueButton1`.</span></span>

     <span data-ttu-id="29f14-172">O **Editor de Códigos** é aberto no evento `ValueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="29f14-172">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>

9. <span data-ttu-id="29f14-173">Digite a seguinte linha de código.</span><span class="sxs-lookup"><span data-stu-id="29f14-173">Type the following line of code.</span></span>

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. <span data-ttu-id="29f14-174">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Teste** e escolha **Definir como Projeto de Inicialização** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="29f14-174">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="29f14-175">No menu **Depuração**, selecione **Iniciar Depuração**.</span><span class="sxs-lookup"><span data-stu-id="29f14-175">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="29f14-176">`Form1` é exibido.</span><span class="sxs-lookup"><span data-stu-id="29f14-176">`Form1` appears.</span></span>

12. <span data-ttu-id="29f14-177">Clique em `Valuebutton1`.</span><span class="sxs-lookup"><span data-stu-id="29f14-177">Click `Valuebutton1`.</span></span>

     <span data-ttu-id="29f14-178">O numeral "5" é exibido em `Label1`, demonstrando que a propriedade `ButtonValue` de seu controle herdado foi passada para `Label1` por meio do método `ValueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="29f14-178">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="29f14-179">Portanto, seu controle `ValueButton` herda todas as funcionalidades do botão padrão dos Windows Forms, mas expõe uma propriedade adicional personalizada.</span><span class="sxs-lookup"><span data-stu-id="29f14-179">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="29f14-180">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29f14-180">See also</span></span>

- [<span data-ttu-id="29f14-181">Passo a passo: Criando um controle composto com Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29f14-181">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="29f14-182">Como: Exibir um controle na caixa de diálogo escolher itens da Toolbox</span><span class="sxs-lookup"><span data-stu-id="29f14-182">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="29f14-183">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="29f14-183">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="29f14-184">Noções básicas de herança (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29f14-184">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
