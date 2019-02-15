---
title: 'Passo a passo: Herdando um controle de formulários do Windows com o Visual Basic'
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
ms.openlocfilehash: 6ffbc24ca8c969630279162619ee5ec9e9aad3ec
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303590"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="606d6-102">Passo a passo: Herdando um controle de formulários do Windows com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="606d6-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="606d6-103">Com o Visual Basic, você pode criar controles personalizados avançados por meio *herança*.</span><span class="sxs-lookup"><span data-stu-id="606d6-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="606d6-104">Com a herança, você é capaz de criar controles que mantêm todas as funcionalidades inerentes de controles padrão dos Windows Forms, mas também incorporam funcionalidades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="606d6-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="606d6-105">Neste passo a passo, você criará um controle herdado simples chamado `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="606d6-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="606d6-106">Esse botão herdará funcionalidades do formulários padrão do Windows <xref:System.Windows.Forms.Button> controlar e exporá uma propriedade personalizada chamada `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="606d6-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="606d6-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="606d6-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="606d6-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="606d6-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="606d6-109">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="606d6-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="606d6-110">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="606d6-110">Creating the Project</span></span>  
 <span data-ttu-id="606d6-111">Quando cria um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e para garantir que o componente padrão estará no namespace correto.</span><span class="sxs-lookup"><span data-stu-id="606d6-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="606d6-112">Para criar a biblioteca de controle ValueButtonLib e o controle ValueButton</span><span class="sxs-lookup"><span data-stu-id="606d6-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="606d6-113">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto** para abrir a caixa de diálogo **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="606d6-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="606d6-114">Selecione o **biblioteca de controle do Windows Forms** modelo de projeto da lista de projetos do Visual Basic e o tipo `ValueButtonLib` no **nome** caixa.</span><span class="sxs-lookup"><span data-stu-id="606d6-114">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="606d6-115">O nome do projeto, `ValueButtonLib`, também é atribuído ao namespace raiz por padrão.</span><span class="sxs-lookup"><span data-stu-id="606d6-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="606d6-116">O namespace raiz é usado para qualificar os nomes dos componentes no assembly.</span><span class="sxs-lookup"><span data-stu-id="606d6-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="606d6-117">Por exemplo, se dois assemblies fornecerem componentes chamados `ValueButton`, você poderá especificar o componente `ValueButton` usando `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="606d6-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="606d6-118">Para obter mais informações, consulte [Namespaces no Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="606d6-118">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
3.  <span data-ttu-id="606d6-119">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **UserControl1.vb** e escolha **Renomear** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="606d6-119">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="606d6-120">Altere o nome de arquivo para `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="606d6-120">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="606d6-121">Clique no botão **Sim** quando for solicitado se quiser renomear todas as referências ao elemento de código “UserControl1”.</span><span class="sxs-lookup"><span data-stu-id="606d6-121">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>  
  
4.  <span data-ttu-id="606d6-122">Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="606d6-122">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="606d6-123">Abra o nó **ValueButton.vb** para exibir o arquivo de código gerado pelo designer, **ValueButton.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="606d6-123">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="606d6-124">Abra esse arquivo no **Editor de Códigos**.</span><span class="sxs-lookup"><span data-stu-id="606d6-124">Open this file in the **Code Editor**.</span></span>  
  
6.  <span data-ttu-id="606d6-125">Localize o `Class` instrução `Partial Public Class ValueButton`e altere o tipo do qual esse controle herda de <xref:System.Windows.Forms.UserControl> para <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="606d6-125">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="606d6-126">Isso permite que o controle herdado herde toda a funcionalidade do <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="606d6-126">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
7.  <span data-ttu-id="606d6-127">Localize o `InitializeComponent` método e remova a linha que atribui o <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="606d6-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="606d6-128">Essa propriedade não existe no <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="606d6-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="606d6-129">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="606d6-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
     <span data-ttu-id="606d6-130">Observe que um designer visual não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="606d6-130">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="606d6-131">Porque o <xref:System.Windows.Forms.Button> controle faz sua própria pintura, você não conseguir modificar sua aparência no designer.</span><span class="sxs-lookup"><span data-stu-id="606d6-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="606d6-132">Sua representação visual será exatamente o mesmo que a classe herda de (ou seja, <xref:System.Windows.Forms.Button>), a menos que modificado no código.</span><span class="sxs-lookup"><span data-stu-id="606d6-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="606d6-133">Você ainda pode adicionar componentes, que não têm uma interface do usuário, à superfície de design.</span><span class="sxs-lookup"><span data-stu-id="606d6-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="606d6-134">Adicionando uma propriedade ao controle herdado</span><span class="sxs-lookup"><span data-stu-id="606d6-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="606d6-135">Um uso possível dos controles herdados dos Windows Forms é a criação de controles que são idênticos em termos de aparência e comportamento a controles padrão dos Windows Forms, mas que expõem propriedades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="606d6-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="606d6-136">Nesta seção, você adicionará uma propriedade chamada `ButtonValue` ao controle.</span><span class="sxs-lookup"><span data-stu-id="606d6-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="606d6-137">Para adicionar a propriedade de valor</span><span class="sxs-lookup"><span data-stu-id="606d6-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="606d6-138">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **ValueButton.vb** e, depois, clique em **Exibir Código** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="606d6-138">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="606d6-139">Localize a instrução `Public Class ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="606d6-139">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="606d6-140">Logo abaixo dessa instrução, digite o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="606d6-140">Immediately beneath this statement, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="606d6-141">Esse código define os métodos segundo os quais a propriedade `ButtonValue` é armazenada e recuperada.</span><span class="sxs-lookup"><span data-stu-id="606d6-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="606d6-142">A instrução `Get` define o valor retornado como o valor que é armazenado na variável particular `varValue` e a instrução `Set` define o valor da variável particular usando a palavra-chave `Value`.</span><span class="sxs-lookup"><span data-stu-id="606d6-142">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>  
  
3.  <span data-ttu-id="606d6-143">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="606d6-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="606d6-144">Testando seu controle</span><span class="sxs-lookup"><span data-stu-id="606d6-144">Testing Your Control</span></span>  
 <span data-ttu-id="606d6-145">Controles não são projetos autônomos; eles devem ser hospedados em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="606d6-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="606d6-146">Para testar seu controle, você precisa fornecer um projeto de teste em que ele será executado.</span><span class="sxs-lookup"><span data-stu-id="606d6-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="606d6-147">Você também precisa tornar seu controle acessível para o projeto de teste compilando-o.</span><span class="sxs-lookup"><span data-stu-id="606d6-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="606d6-148">Nesta seção, você compilará seu controle e o testará em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="606d6-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="606d6-149">Para compilar seu controle</span><span class="sxs-lookup"><span data-stu-id="606d6-149">To build your control</span></span>  
  
1.  <span data-ttu-id="606d6-150">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="606d6-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="606d6-151">O build deve ser bem-sucedido, sem avisos ou erros do compilador.</span><span class="sxs-lookup"><span data-stu-id="606d6-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="606d6-152">Para criar um projeto de teste</span><span class="sxs-lookup"><span data-stu-id="606d6-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="606d6-153">No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto** para abrir a caixa de diálogo **Adicionar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="606d6-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="606d6-154">Selecione o nó de projetos do Visual Basic e, em seguida, clique em **aplicativo do Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="606d6-154">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="606d6-155">Na caixa **Nome**, digite `Test`.</span><span class="sxs-lookup"><span data-stu-id="606d6-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="606d6-156">Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="606d6-156">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="606d6-157">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** de seu projeto de teste e selecione **Adicionar Referência** no menu de atalho para exibir a caixa de diálogo **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="606d6-157">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
6.  <span data-ttu-id="606d6-158">Clique na guia **Projetos**.</span><span class="sxs-lookup"><span data-stu-id="606d6-158">Click the **Projects** tab.</span></span>  
  
7.  <span data-ttu-id="606d6-159">Clique na guia rotulada como **Projetos**.</span><span class="sxs-lookup"><span data-stu-id="606d6-159">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="606d6-160">O projeto `ValueButtonLib` estará listado em **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="606d6-160">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="606d6-161">Clique duas vezes no projeto para adicionar a referência ao projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="606d6-161">Double-click the project to add the reference to the test project.</span></span>  
  
8.  <span data-ttu-id="606d6-162">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Testar** e selecione **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="606d6-162">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="606d6-163">Para adicionar o controle ao formulário</span><span class="sxs-lookup"><span data-stu-id="606d6-163">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="606d6-164">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1.vb** e selecione **Designer de Modo de Exibição** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="606d6-164">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="606d6-165">Na **Caixa de Ferramentas**, clique em **Componentes de ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="606d6-165">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="606d6-166">Clique duas vezes em **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="606d6-166">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="606d6-167">Um **ValueButton** aparece no formulário.</span><span class="sxs-lookup"><span data-stu-id="606d6-167">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="606d6-168">Clique com o botão direito do mouse em **ValueButton** e selecione **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="606d6-168">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="606d6-169">Na janela **Propriedades**, examine as propriedades desse controle.</span><span class="sxs-lookup"><span data-stu-id="606d6-169">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="606d6-170">Observe que elas são idênticas às propriedades expostas por um botão padrão, exceto pelo fato de que há uma propriedade adicional, `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="606d6-170">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="606d6-171">Defina a propriedade `ButtonValue` como `5`.</span><span class="sxs-lookup"><span data-stu-id="606d6-171">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="606d6-172">No **todos os Windows Forms** guia da **caixa de ferramentas**, clique duas vezes em **rótulo** para adicionar um <xref:System.Windows.Forms.Label> controle ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="606d6-172">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="606d6-173">Reposicione o rótulo no centro do formulário.</span><span class="sxs-lookup"><span data-stu-id="606d6-173">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="606d6-174">Clique duas vezes em `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="606d6-174">Double-click `ValueButton1`.</span></span>  
  
     <span data-ttu-id="606d6-175">O **Editor de Códigos** é aberto no evento `ValueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="606d6-175">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="606d6-176">Digite a seguinte linha de código.</span><span class="sxs-lookup"><span data-stu-id="606d6-176">Type the following line of code.</span></span>  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. <span data-ttu-id="606d6-177">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Teste** e escolha **Definir como Projeto de Inicialização** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="606d6-177">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="606d6-178">No menu **Depuração**, selecione **Iniciar Depuração**.</span><span class="sxs-lookup"><span data-stu-id="606d6-178">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="606d6-179">`Form1` é exibido.</span><span class="sxs-lookup"><span data-stu-id="606d6-179">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="606d6-180">Clique em `Valuebutton1`.</span><span class="sxs-lookup"><span data-stu-id="606d6-180">Click `Valuebutton1`.</span></span>  
  
     <span data-ttu-id="606d6-181">O numeral "5" é exibido em `Label1`, demonstrando que a propriedade `ButtonValue` de seu controle herdado foi passada para `Label1` por meio do método `ValueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="606d6-181">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="606d6-182">Portanto, seu controle `ValueButton` herda todas as funcionalidades do botão padrão dos Windows Forms, mas expõe uma propriedade adicional personalizada.</span><span class="sxs-lookup"><span data-stu-id="606d6-182">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="606d6-183">Consulte também</span><span class="sxs-lookup"><span data-stu-id="606d6-183">See also</span></span>
- [<span data-ttu-id="606d6-184">Passo a passo: Criando um controle composto com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="606d6-184">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="606d6-185">Como: Exibir um controle na caixa de diálogo de itens de caixa de ferramentas de escolha</span><span class="sxs-lookup"><span data-stu-id="606d6-185">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="606d6-186">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="606d6-186">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="606d6-187">Noções básicas de herança (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="606d6-187">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
