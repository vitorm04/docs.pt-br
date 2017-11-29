---
title: "Instruções passo a passo: herdando um controle dos Windows Forms com Visual C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 668dd3624d06f916b23ec16dd8268d2bae4ffcf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="beb25-102">Instruções passo a passo: herdando um controle dos Windows Forms com Visual C#</span><span class="sxs-lookup"><span data-stu-id="beb25-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span> #
<span data-ttu-id="beb25-103">Com o [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], você pode criar controles personalizados avançados por meio da *herança*.</span><span class="sxs-lookup"><span data-stu-id="beb25-103">With [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="beb25-104">Com a herança, você é capaz de criar controles que mantêm todas as funcionalidades inerentes de controles padrão dos Windows Forms, mas também incorporam funcionalidades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="beb25-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="beb25-105">Neste passo a passo, você criará um controle herdado simples chamado `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="beb25-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="beb25-106">Esse botão herdará a funcionalidade de formulários do Windows padrão <xref:System.Windows.Forms.Button> controlar e expõe uma propriedade personalizada chamada `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="beb25-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="beb25-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="beb25-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="beb25-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="beb25-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="beb25-109">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="beb25-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="beb25-110">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="beb25-110">Creating the Project</span></span>  
 <span data-ttu-id="beb25-111">Quando cria um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e para garantir que o componente padrão estará no namespace correto.</span><span class="sxs-lookup"><span data-stu-id="beb25-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="beb25-112">Para criar a biblioteca de controle ValueButtonLib e o controle ValueButton</span><span class="sxs-lookup"><span data-stu-id="beb25-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="beb25-113">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto** para abrir a caixa de diálogo **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="beb25-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="beb25-114">Selecione o modelo de projeto **Biblioteca de Controles dos Windows Forms** na lista de projetos [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] e digite `ValueButtonLib` na caixa **Nome**.</span><span class="sxs-lookup"><span data-stu-id="beb25-114">Select the **Windows Forms Control Library** project template from the list of [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] Projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="beb25-115">O nome do projeto, `ValueButtonLib`, também é atribuído ao namespace raiz por padrão.</span><span class="sxs-lookup"><span data-stu-id="beb25-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="beb25-116">O namespace raiz é usado para qualificar os nomes dos componentes no assembly.</span><span class="sxs-lookup"><span data-stu-id="beb25-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="beb25-117">Por exemplo, se dois assemblies fornecerem componentes chamados `ValueButton`, você poderá especificar o componente `ValueButton` usando `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="beb25-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="beb25-118">Para obter mais informações, consulte [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="beb25-118">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>  
  
3.  <span data-ttu-id="beb25-119">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **UserControl1.cs** e escolha **Renomear** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="beb25-119">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="beb25-120">Altere o nome de arquivo para `ValueButton.cs`.</span><span class="sxs-lookup"><span data-stu-id="beb25-120">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="beb25-121">Clique no botão **Sim** quando solicitado se desejar renomear todas as referências ao elemento de código '`UserControl1`'.</span><span class="sxs-lookup"><span data-stu-id="beb25-121">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>  
  
4.  <span data-ttu-id="beb25-122">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **ValueButton.cs** e selecione **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="beb25-122">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="beb25-123">Localize o `class` linha da instrução, `public partial class ValueButton`e alterar o tipo da qual este controle herda do <xref:System.Windows.Forms.UserControl> para <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="beb25-123">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="beb25-124">Isso permite que o controle herdado herdar toda a funcionalidade do <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="beb25-124">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
6.  <span data-ttu-id="beb25-125">No **Gerenciador de Soluções**, abra o nó **ValueButton.cs** para exibir o arquivo de código gerado pelo designer, **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="beb25-125">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="beb25-126">Abra esse arquivo no **Editor de Códigos**.</span><span class="sxs-lookup"><span data-stu-id="beb25-126">Open this file in the **Code Editor**.</span></span>  
  
7.  <span data-ttu-id="beb25-127">Localize o `InitializeComponent` método e remova a linha que atribui o <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="beb25-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="beb25-128">Essa propriedade não existe no <xref:System.Windows.Forms.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="beb25-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="beb25-129">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="beb25-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="beb25-130">Um designer visual não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="beb25-130">A visual designer is no longer available.</span></span> <span data-ttu-id="beb25-131">Porque o <xref:System.Windows.Forms.Button> controle faz sua própria pintura, você não é possível modificar sua aparência no designer.</span><span class="sxs-lookup"><span data-stu-id="beb25-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="beb25-132">Sua representação visual será exatamente o mesmo que ela herda da classe (ou seja, <xref:System.Windows.Forms.Button>), a menos que modificado no código.</span><span class="sxs-lookup"><span data-stu-id="beb25-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="beb25-133">Você ainda pode adicionar componentes, que não têm uma interface do usuário, à superfície de design.</span><span class="sxs-lookup"><span data-stu-id="beb25-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="beb25-134">Adicionando uma propriedade ao controle herdado</span><span class="sxs-lookup"><span data-stu-id="beb25-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="beb25-135">Um uso possível dos controles herdados dos Windows Forms é a criação de controles que são idênticos em termos de aparência a controles padrão dos Windows Forms, mas que expõem propriedades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="beb25-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="beb25-136">Nesta seção, você adicionará uma propriedade chamada `ButtonValue` ao controle.</span><span class="sxs-lookup"><span data-stu-id="beb25-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="beb25-137">Para adicionar a propriedade de valor</span><span class="sxs-lookup"><span data-stu-id="beb25-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="beb25-138">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **ValueButton.cs** e, depois, clique em **Exibir Código** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="beb25-138">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="beb25-139">Localize a instrução `class`.</span><span class="sxs-lookup"><span data-stu-id="beb25-139">Locate the `class` statement.</span></span> <span data-ttu-id="beb25-140">Cole o código a seguir imediatamente depois de `{`:</span><span class="sxs-lookup"><span data-stu-id="beb25-140">Immediately after the `{`, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="beb25-141">Esse código define os métodos segundo os quais a propriedade `ButtonValue` é armazenada e recuperada.</span><span class="sxs-lookup"><span data-stu-id="beb25-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="beb25-142">A instrução `get` define o valor retornado como o valor que é armazenado na variável particular `varValue` e a instrução `set` define o valor da variável particular usando a palavra-chave `value`.</span><span class="sxs-lookup"><span data-stu-id="beb25-142">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>  
  
3.  <span data-ttu-id="beb25-143">No menu **Arquivo**, escolha **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="beb25-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="beb25-144">Testando seu controle</span><span class="sxs-lookup"><span data-stu-id="beb25-144">Testing Your Control</span></span>  
 <span data-ttu-id="beb25-145">Controles não são projetos autônomos; eles devem ser hospedados em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="beb25-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="beb25-146">Para testar seu controle, você precisa fornecer um projeto de teste em que ele será executado.</span><span class="sxs-lookup"><span data-stu-id="beb25-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="beb25-147">Você também precisa tornar seu controle acessível para o projeto de teste compilando-o.</span><span class="sxs-lookup"><span data-stu-id="beb25-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="beb25-148">Nesta seção, você compilará seu controle e o testará em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="beb25-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="beb25-149">Para compilar seu controle</span><span class="sxs-lookup"><span data-stu-id="beb25-149">To build your control</span></span>  
  
1.  <span data-ttu-id="beb25-150">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="beb25-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="beb25-151">O build deve ser bem-sucedido, sem avisos ou erros do compilador.</span><span class="sxs-lookup"><span data-stu-id="beb25-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="beb25-152">Para criar um projeto de teste</span><span class="sxs-lookup"><span data-stu-id="beb25-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="beb25-153">No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto** para abrir a caixa de diálogo **Adicionar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="beb25-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="beb25-154">Selecione o nó **Windows**, abaixo de **Visual C#** e clique em **Aplicativo dos Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="beb25-154">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="beb25-155">Na caixa **Nome**, digite `Test`.</span><span class="sxs-lookup"><span data-stu-id="beb25-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="beb25-156">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** de seu projeto de teste e selecione **Adicionar Referência** no menu de atalho para exibir a caixa de diálogo **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="beb25-156">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="beb25-157">Clique na guia rotulada como **Projetos**.</span><span class="sxs-lookup"><span data-stu-id="beb25-157">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="beb25-158">O projeto `ValueButtonLib` estará listado em **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="beb25-158">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="beb25-159">Clique duas vezes no projeto para adicionar a referência ao projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="beb25-159">Double-click the project to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="beb25-160">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Testar** e selecione **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="beb25-160">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="beb25-161">Para adicionar o controle ao formulário</span><span class="sxs-lookup"><span data-stu-id="beb25-161">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="beb25-162">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1.cs** e selecione **Designer de Modo de Exibição** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="beb25-162">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="beb25-163">Na **Caixa de Ferramentas**, clique em **Componentes de ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="beb25-163">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="beb25-164">Clique duas vezes em **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="beb25-164">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="beb25-165">Um **ValueButton** aparece no formulário.</span><span class="sxs-lookup"><span data-stu-id="beb25-165">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="beb25-166">Clique com o botão direito do mouse em **ValueButton** e selecione **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="beb25-166">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="beb25-167">Na janela **Propriedades**, examine as propriedades desse controle.</span><span class="sxs-lookup"><span data-stu-id="beb25-167">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="beb25-168">Observe que elas são idênticas às propriedades expostas por um botão padrão, exceto pelo fato de que há uma propriedade adicional, `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="beb25-168">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="beb25-169">Defina a propriedade `ButtonValue` como `5`.</span><span class="sxs-lookup"><span data-stu-id="beb25-169">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="beb25-170">No **todos os Windows Forms** guia do **caixa de ferramentas**, clique duas vezes em **rótulo** para adicionar um <xref:System.Windows.Forms.Label> a seu formulário.</span><span class="sxs-lookup"><span data-stu-id="beb25-170">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="beb25-171">Reposicione o rótulo no centro do formulário.</span><span class="sxs-lookup"><span data-stu-id="beb25-171">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="beb25-172">Clique duas vezes em `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="beb25-172">Double-click `valueButton1`.</span></span>  
  
     <span data-ttu-id="beb25-173">O **Editor de Códigos** é aberto no evento `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="beb25-173">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="beb25-174">Insira a seguinte linha de código.</span><span class="sxs-lookup"><span data-stu-id="beb25-174">Insert the following line of code.</span></span>  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. <span data-ttu-id="beb25-175">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Teste** e escolha **Definir como Projeto de Inicialização** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="beb25-175">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="beb25-176">No menu **Depuração**, selecione **Iniciar Depuração**.</span><span class="sxs-lookup"><span data-stu-id="beb25-176">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="beb25-177">`Form1` é exibido.</span><span class="sxs-lookup"><span data-stu-id="beb25-177">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="beb25-178">Clique em `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="beb25-178">Click `valueButton1`.</span></span>  
  
     <span data-ttu-id="beb25-179">O numeral "5" é exibido em `label1`, demonstrando que a propriedade `ButtonValue` de seu controle herdado foi passada para `label1` por meio do método `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="beb25-179">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="beb25-180">Portanto, seu controle `ValueButton` herda todas as funcionalidades do botão padrão dos Windows Forms, mas expõe uma propriedade adicional personalizada.</span><span class="sxs-lookup"><span data-stu-id="beb25-180">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb25-181">Consulte também</span><span class="sxs-lookup"><span data-stu-id="beb25-181">See Also</span></span>  
 [<span data-ttu-id="beb25-182">Programação com componentes</span><span class="sxs-lookup"><span data-stu-id="beb25-182">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="beb25-183">Instruções passo a passo para criação de componentes</span><span class="sxs-lookup"><span data-stu-id="beb25-183">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="beb25-184">Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="beb25-184">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="beb25-185">Passo a passo: criando um controle de composição com o Visual C#</span><span class="sxs-lookup"><span data-stu-id="beb25-185">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
