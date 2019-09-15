---
title: 'Passo a passo: hospedar um controle composto do Windows Forms no WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: e4c1de17b131ee68c6e6fce0035b703eb5b489a0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991878"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="e4a5c-102">Passo a passo: hospedar um controle composto do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="e4a5c-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
<span data-ttu-id="e4a5c-103">O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um ambiente avançado para a criação de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides a rich environment for creating applications.</span></span> <span data-ttu-id="e4a5c-104">No entanto, quando você tem um investimento [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] substancial em código, pode ser mais eficiente reutilizar pelo menos um pouco desse código em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seu aplicativo em vez de regravá-lo do zero.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="e4a5c-105">O cenário mais comum é quando você tem controles de Windows Forms existentes.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="e4a5c-106">Em alguns casos, talvez você não tenha nem acesso ao código-fonte desses controles.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="e4a5c-107">fornece um procedimento direto para hospedar esses controles em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="e4a5c-108">Por exemplo, você pode usar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para a maior parte de sua programação enquanto hospeda <xref:System.Windows.Forms.DataGridView> seus controles especializados.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="e4a5c-109">Este passo a passos percorre um aplicativo que hospeda um controle de composição Windows Forms para executar a entrada de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dados em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="e4a5c-110">O controle composto é empacotado em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="e4a5c-111">Esse procedimento geral pode ser estendido para aplicativos e controles mais complexos.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="e4a5c-112">Este tutorial foi projetado para ser praticamente idêntico na aparência e na funcionalidade [para o Walkthrough: Hospedando um controle composto do WPF](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="e4a5c-113">A principal diferença é que o cenário de hospedagem é invertido.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="e4a5c-114">O passo a passo está dividido em duas seções.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="e4a5c-115">A primeira seção descreve brevemente a implementação do controle composto Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="e4a5c-116">A segunda seção aborda em detalhes como hospedar o controle composto em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo, receber eventos do controle e acessar algumas das propriedades do controle.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="e4a5c-117">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="e4a5c-118">Implementação do controle de composição dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="e4a5c-119">Implementação do aplicativo host do WPF.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="e4a5c-120">Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [hospedando um Windows Forms controle composto no WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="e4a5c-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e4a5c-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e4a5c-121">Prerequisites</span></span>  

<span data-ttu-id="e4a5c-122">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="e4a5c-123">Implementação do controle de composição dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4a5c-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="e4a5c-124">O controle composto Windows Forms usado neste exemplo é um formulário simples de entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="e4a5c-125">Este formulário recebe o nome e o endereço do usuário e, em seguida, usa um evento personalizado para retornar essa informação ao host.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="e4a5c-126">A ilustração a seguir mostra o controle renderizado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="e4a5c-127">A imagem a seguir mostra um controle composto Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Captura de tela que mostra um controle de Windows Forms simples.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="e4a5c-129">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="e4a5c-129">Creating the Project</span></span>  
 <span data-ttu-id="e4a5c-130">Para iniciar o projeto:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-130">To start the project:</span></span>  
  
1. <span data-ttu-id="e4a5c-131">Inicie [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]o e abra a caixa de diálogo **novo projeto** .</span><span class="sxs-lookup"><span data-stu-id="e4a5c-131">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="e4a5c-132">Na categoria de janela, selecione o modelo de **biblioteca de controle de Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="e4a5c-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="e4a5c-133">Dê um nome ao novo projeto `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="e4a5c-134">Para o local, especifique uma pasta de nível superior que `WpfHostingWindowsFormsControl`seja convenientemente nomeada, como.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="e4a5c-135">Mais tarde, você colocará o aplicativo host nessa pasta.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="e4a5c-136">Clique em **OK** para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-136">Click **OK** to create the project.</span></span> <span data-ttu-id="e4a5c-137">O projeto padrão contém um único controle chamado `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="e4a5c-138">Em Gerenciador de soluções, renomeie `UserControl1` como. `MyControl1`</span><span class="sxs-lookup"><span data-stu-id="e4a5c-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="e4a5c-139">Seu projeto deve ter referências às seguintes DLLs de sistema.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="e4a5c-140">Se qualquer uma dessas DLLs não estiver incluída por padrão, adicione-as ao projeto.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="e4a5c-141">Sistema</span><span class="sxs-lookup"><span data-stu-id="e4a5c-141">System</span></span>  
  
- <span data-ttu-id="e4a5c-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="e4a5c-142">System.Data</span></span>  
  
- <span data-ttu-id="e4a5c-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="e4a5c-143">System.Drawing</span></span>  
  
- <span data-ttu-id="e4a5c-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="e4a5c-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="e4a5c-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="e4a5c-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="e4a5c-146">Adicionando controles ao formulário</span><span class="sxs-lookup"><span data-stu-id="e4a5c-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="e4a5c-147">Para adicionar controles ao formulário:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="e4a5c-148">Abra `MyControl1` no designer.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="e4a5c-149">Adicione cinco <xref:System.Windows.Forms.Label> controles e seus controles <xref:System.Windows.Forms.TextBox> correspondentes, dimensionados e organizados como estão na ilustração anterior, no formulário.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="e4a5c-150">No exemplo, os <xref:System.Windows.Forms.TextBox> controles são nomeados:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="e4a5c-151">Adicione dois <xref:System.Windows.Forms.Button> controles rotulados **OK** e **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="e4a5c-152">No exemplo, os nomes dos botões são `btnOK` e `btnCancel`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="e4a5c-153">Implementando o código de suporte</span><span class="sxs-lookup"><span data-stu-id="e4a5c-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="e4a5c-154">Abra o formulário no modo de exibição de código.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-154">Open the form in code view.</span></span> <span data-ttu-id="e4a5c-155">O controle retorna os dados coletados para seu host, gerando `OnButtonClick` o evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="e4a5c-156">Os dados estão contidos no objeto de argumento do evento.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="e4a5c-157">O código a seguir mostra a declaração do evento e do delegado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="e4a5c-158">Adicione o código a seguir à classe `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="e4a5c-159">A `MyControlEventArgs` classe contém as informações a serem retornadas ao host.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="e4a5c-160">Adicione a seguinte classe ao formulário.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="e4a5c-161">Quando o usuário clica no botão **OK** ou **Cancelar** , os <xref:System.Windows.Forms.Control.Click> manipuladores de eventos criam `MyControlEventArgs` um objeto que contém os dados e gera `OnButtonClick` o evento.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="e4a5c-162">A única diferença entre os dois manipuladores é a propriedade do argumento `IsOK` de evento.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="e4a5c-163">Essa propriedade permite que o host determine qual botão foi clicado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="e4a5c-164">Ele é definido como `true` para o botão **OK** e `false` para o botão **Cancelar** .</span><span class="sxs-lookup"><span data-stu-id="e4a5c-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="e4a5c-165">O código a seguir mostra os dois manipuladores de botão.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="e4a5c-166">Adicione o código a seguir à classe `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="e4a5c-167">Fornecendo um nome forte e compilando o assembly</span><span class="sxs-lookup"><span data-stu-id="e4a5c-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="e4a5c-168">Para que este assembly seja referenciado por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] um aplicativo, ele deve ter um nome forte.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="e4a5c-169">Para criar um nome forte, crie um arquivo de chave com o Sn. exe e adicione-o ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="e4a5c-170">Abra um prompt de comando do [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4a5c-170">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="e4a5c-171">Para fazer isso, clique no menu **Iniciar** e, em seguida, selecione **todos os programas/Microsoft Visual Studio 2010/ferramentas do Visual Studio/prompt de comando do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="e4a5c-172">Isso inicia uma janela de console com variáveis de ambiente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="e4a5c-173">No prompt de comando, use o `cd` comando para ir para a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="e4a5c-174">Gere um arquivo de chave chamado MyControls.snk, executando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```console
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="e4a5c-175">Para incluir o arquivo de chave em seu projeto, clique com o botão direito do mouse no nome do projeto em Gerenciador de Soluções e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="e4a5c-176">No designer de projeto, clique na guia **assinatura** , marque a caixa de seleção **assinar o assembly** e, em seguida, navegue até o arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="e4a5c-177">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-177">Build the solution.</span></span> <span data-ttu-id="e4a5c-178">O build produzirá uma DLL denominada MyControls.dll.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="e4a5c-179">Implementação do aplicativo host do WPF</span><span class="sxs-lookup"><span data-stu-id="e4a5c-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="e4a5c-180">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo host usa o <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle para hospedar `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="e4a5c-181">O aplicativo manipula o `OnButtonClick` evento para receber os dados do controle.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="e4a5c-182">Ele também tem uma coleção de botões de opção que permitem que você altere algumas das propriedades do controle do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="e4a5c-183">A ilustração a seguir mostra o aplicativo concluído.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="e4a5c-184">A imagem a seguir mostra o aplicativo completo, incluindo o controle inserido no aplicativo WPF:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![Captura de tela que mostra um controle inserido em uma página do WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="e4a5c-186">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="e4a5c-186">Creating the Project</span></span>
 <span data-ttu-id="e4a5c-187">Para iniciar o projeto:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-187">To start the project:</span></span>

1. <span data-ttu-id="e4a5c-188">Abra [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]e selecione **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-188">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>

2. <span data-ttu-id="e4a5c-189">Na categoria da janela, selecione o modelo de **aplicativo do WPF** .</span><span class="sxs-lookup"><span data-stu-id="e4a5c-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="e4a5c-190">Dê um nome ao novo projeto `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="e4a5c-191">Para o local, especifique a mesma pasta de nível superior que contém o projeto MyControls.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="e4a5c-192">Clique em **OK** para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="e4a5c-193">Você também precisa adicionar referências à dll que contém `MyControl1` e a outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="e4a5c-194">Clique com o botão direito do mouse no nome do projeto em Gerenciador de Soluções e selecione **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="e4a5c-195">Clique na guia **procurar** e navegue até a pasta que contém MyControls. dll.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="e4a5c-196">Para este passo a passo, a pasta é a MyControls\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="e4a5c-197">Selecione MyControls. dll e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="e4a5c-198">Adicione uma referência ao assembly WindowsFormsIntegration, que é chamado WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="e4a5c-199">Implementando o layout básico</span><span class="sxs-lookup"><span data-stu-id="e4a5c-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="e4a5c-200">O [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplicativo host é implementado em MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="e4a5c-201">Esse arquivo contém [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] marcação que define o layout e hospeda o controle de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="e4a5c-202">O aplicativo é dividido em três regiões:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="e4a5c-203">O painel **Propriedades de controle** , que contém uma coleção de botões de opção que você pode usar para modificar várias propriedades do controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="e4a5c-204">Os **dados do** painel de controle, que contém <xref:System.Windows.Controls.TextBlock> vários elementos que exibem os dados retornados do controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="e4a5c-205">O próprio controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-205">The hosted control itself.</span></span>

 <span data-ttu-id="e4a5c-206">O layout básico é mostrado no seguinte XAML.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="e4a5c-207">A marcação necessária para hospedar `MyControl1` é omitida neste exemplo, mas será discutida posteriormente.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="e4a5c-208">Substitua o XAML em MainWindow.xaml pelo seguinte.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="e4a5c-209">Se você estiver usando Visual Basic, altere a classe para `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="e4a5c-210">O primeiro <xref:System.Windows.Controls.StackPanel> elemento contém vários conjuntos de <xref:System.Windows.Controls.RadioButton> controles que permitem modificar várias propriedades padrão do controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="e4a5c-211">Isso é seguido por um <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, que hospeda `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="e4a5c-212">O elemento <xref:System.Windows.Controls.StackPanel> final contém vários <xref:System.Windows.Controls.TextBlock> elementos que exibem os dados retornados pelo controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="e4a5c-213">A ordenação dos elementos e <xref:System.Windows.Controls.DockPanel.Dock%2A> das configurações de atributo e <xref:System.Windows.FrameworkElement.Height%2A> incorpora o controle hospedado na janela sem intervalos ou distorção.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="e4a5c-214">Hospedagem do controle</span><span class="sxs-lookup"><span data-stu-id="e4a5c-214">Hosting the Control</span></span>
 <span data-ttu-id="e4a5c-215">A seguinte versão editada do XAML anterior se concentra nos elementos que são necessários para hospedar `MyControl1`o.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="e4a5c-216">O `xmlns` atributo de mapeamento de namespace cria uma referência `MyControls` ao namespace que contém o controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="e4a5c-217">Esse mapeamento permite que você `MyControl1` represente [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] no `<mcl:MyControl1>`como.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="e4a5c-218">Dois elementos no XAML manipulam a hospedagem:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="e4a5c-219">`WindowsFormsHost`representa o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento que permite hospedar um controle de Windows Forms em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="e4a5c-220">`mcl:MyControl1`, que representa `MyControl1`, é adicionado <xref:System.Windows.Forms.Integration.WindowsFormsHost> à coleção filho do elemento.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="e4a5c-221">Como resultado, esse Windows Forms controle é renderizado como parte da [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] janela e você pode se comunicar com o controle do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="e4a5c-222">Implementando o arquivo code-behind</span><span class="sxs-lookup"><span data-stu-id="e4a5c-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="e4a5c-223">O arquivo code-behind, MainWindow. XAML. vb ou MainWindow.XAML.cs, contém o código de procedimento que implementa a funcionalidade do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] abordado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="e4a5c-224">As tarefas principais são:</span><span class="sxs-lookup"><span data-stu-id="e4a5c-224">The primary tasks are:</span></span>

- <span data-ttu-id="e4a5c-225">Anexando um manipulador de `MyControl1`eventos `OnButtonClick` a um evento.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="e4a5c-226">Modificar várias propriedades de `MyControl1`, com base em como a coleção de botões de opção é definida.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="e4a5c-227">Exibir os dados coletados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="e4a5c-228">Inicializando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="e4a5c-228">Initializing the Application</span></span>
 <span data-ttu-id="e4a5c-229">O código de inicialização está contido em um manipulador de eventos para o <xref:System.Windows.FrameworkElement.Loaded> evento da janela e anexa um manipulador de eventos ao evento `OnButtonClick` do controle.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="e4a5c-230">Em MainWindow. XAML. vb ou MainWindow.XAML.cs, adicione o código a seguir à `MainWindow` classe.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="e4a5c-231">Como os [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discutidos anteriormente `MyControl1` foram adicionados <xref:System.Windows.Forms.Integration.WindowsFormsHost> à <xref:System.Windows.Forms.Integration.WindowsFormsHost> `MyControl1`coleção de elementos filho do elemento, você pode converter o elemento paraobterareferênciaa.<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A></span><span class="sxs-lookup"><span data-stu-id="e4a5c-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="e4a5c-232">Você pode usar essa referência para anexar um manipulador de eventos ao `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="e4a5c-233">Além de fornecer uma referência ao próprio controle, <xref:System.Windows.Forms.Integration.WindowsFormsHost> o expõe uma série de propriedades do controle, que você pode manipular a partir do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="e4a5c-234">O código de inicialização atribui esses valores a variáveis globais particulares para uso posterior no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="e4a5c-235">Para que você possa acessar facilmente os tipos na `MyControls` dll, adicione a seguinte `Imports` instrução ou `using` à parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="e4a5c-236">Manipulando o evento OnButtonClick</span><span class="sxs-lookup"><span data-stu-id="e4a5c-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="e4a5c-237">`MyControl1`gera o `OnButtonClick` evento quando o usuário clica em um dos botões do controle.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="e4a5c-238">Adicione o código a seguir à classe `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="e4a5c-239">Os dados nas caixas de texto são incluídos `MyControlEventArgs` no objeto.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="e4a5c-240">Se o usuário clicar no botão **OK** , o manipulador de eventos extrairá os dados e os exibirá no painel `MyControl1`abaixo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="e4a5c-241">Modificando as propriedades do controle</span><span class="sxs-lookup"><span data-stu-id="e4a5c-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="e4a5c-242">O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento expõe várias das propriedades padrão do controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="e4a5c-243">Como resultado, você pode alterar a aparência do controle para combinar melhor com o estilo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="e4a5c-244">Os conjuntos de botões de opção no painel esquerdo permitem ao usuário modificar várias propriedades de fonte e cor.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="e4a5c-245">Cada conjunto de botões tem um manipulador para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento, que detecta as seleções do botão de opção do usuário e altera a propriedade correspondente no controle.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="e4a5c-246">Adicione o código a seguir à classe `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="e4a5c-247">Crie e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-247">Build and run the application.</span></span> <span data-ttu-id="e4a5c-248">Adicione texto no controle de composição Windows Forms e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="e4a5c-249">O texto é exibido nos rótulos.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-249">The text appears in the labels.</span></span> <span data-ttu-id="e4a5c-250">Clique nos diferentes botões de opção para ver o efeito no controle.</span><span class="sxs-lookup"><span data-stu-id="e4a5c-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a5c-251">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4a5c-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="e4a5c-252">Criar o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e4a5c-252">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="e4a5c-253">Passo a passo: Hospedando um controle de Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="e4a5c-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="e4a5c-254">Passo a passo: Hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4a5c-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
