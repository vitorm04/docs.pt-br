---
title: 'Instruções passo a passo: depurando controles dos Windows Forms na hora do design'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
ms.openlocfilehash: 824c1e47cf50dc13a3a986e48a49158b15dbb935
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964824"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="256ae-102">Instruções passo a passo: depurando controles dos Windows Forms na hora do design</span><span class="sxs-lookup"><span data-stu-id="256ae-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="256ae-103">Quando criar um controle personalizado, frequentemente você achará necessário depurar seu comportamento em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="256ae-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="256ae-104">Isso será especialmente válido se você estiver criando um designer personalizado para seu controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="256ae-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="256ae-105">Para obter detalhes, consulte [Instruções passo a passo: criando um controle dos Windows Forms que aproveite os recursos de tempo de design do Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="256ae-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="256ae-106">Você pode depurar seus controles personalizados usando o Visual Studio, da mesma forma que depuraria qualquer outra classe do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="256ae-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="256ae-107">A diferença é que você depurará uma instância separada do Visual Studio que está executando o código do seu controle personalizado</span><span class="sxs-lookup"><span data-stu-id="256ae-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="256ae-108">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="256ae-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="256ae-109">Criar um projeto dos Windows Forms para hospedar o controle personalizado</span><span class="sxs-lookup"><span data-stu-id="256ae-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="256ae-110">Criar um projeto de biblioteca de controle</span><span class="sxs-lookup"><span data-stu-id="256ae-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="256ae-111">Adicionar uma propriedade ao controle personalizado</span><span class="sxs-lookup"><span data-stu-id="256ae-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="256ae-112">Adicionar o controle personalizado ao formulário de host</span><span class="sxs-lookup"><span data-stu-id="256ae-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="256ae-113">Configurar o projeto para depuração em tempo de design</span><span class="sxs-lookup"><span data-stu-id="256ae-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="256ae-114">Depurar o controle personalizado em tempo de design</span><span class="sxs-lookup"><span data-stu-id="256ae-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="256ae-115">Quando tiver terminado, você compreenderá as tarefas necessárias para depurar o comportamento de tempo de design de um controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="256ae-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="256ae-116">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="256ae-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="256ae-117">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="256ae-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="256ae-118">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="256ae-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="256ae-119">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="256ae-119">Creating the Project</span></span>  
 <span data-ttu-id="256ae-120">A primeira etapa é criar o projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="256ae-120">The first step is to create the application project.</span></span> <span data-ttu-id="256ae-121">Você usará este projeto para criar o aplicativo que hospeda o controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="256ae-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="256ae-122">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="256ae-122">To create the project</span></span>  
  
-   <span data-ttu-id="256ae-123">Crie um projeto de aplicativo do Windows chamado "DebuggingExample" (**arquivo** > **New** > **projeto**  >  **Visual c#** ou **Visual Basic** > **área de trabalho clássica** > **aplicativo de formulários do Windows**).</span><span class="sxs-lookup"><span data-stu-id="256ae-123">Create a Windows Application project called "DebuggingExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="256ae-124">Criar um Projeto de Biblioteca de Controle</span><span class="sxs-lookup"><span data-stu-id="256ae-124">Creating a Control Library Project</span></span>  
 <span data-ttu-id="256ae-125">A etapa seguinte é criar o projeto de biblioteca de controle e configurar o controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="256ae-125">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="256ae-126">Para criar o projeto de biblioteca de controles</span><span class="sxs-lookup"><span data-stu-id="256ae-126">To create the control library project</span></span>  
  
1.  <span data-ttu-id="256ae-127">Adicione um projeto de **Biblioteca de controle do Windows** à solução.</span><span class="sxs-lookup"><span data-stu-id="256ae-127">Add a **Windows Control Library** project to the solution.</span></span>  
  
2.  <span data-ttu-id="256ae-128">Adicione um novo item **UserControl** ao projeto DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="256ae-128">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="256ae-129">Para obter detalhes, consulte [NIB: como adicionar novos itens de projeto](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="256ae-129">For details, see [NIB:How to: Add New Project Items](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="256ae-130">Dê ao novo arquivo de origem o nome base "DebugControl".</span><span class="sxs-lookup"><span data-stu-id="256ae-130">Give the new source file a base name of "DebugControl".</span></span>  
  
3.  <span data-ttu-id="256ae-131">Usando o **Gerenciador de Soluções**, exclua o controle padrão do projeto excluindo o arquivo de código com o nome de base "`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="256ae-131">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="256ae-132">Para obter detalhes, consulte [NIB: como remover, apagar e excluir itens](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="256ae-132">For details, see [NIB:How to: Remove, Delete, and Exclude Items](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
4.  <span data-ttu-id="256ae-133">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="256ae-133">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="256ae-134">Ponto de verificação</span><span class="sxs-lookup"><span data-stu-id="256ae-134">Checkpoint</span></span>  
 <span data-ttu-id="256ae-135">Neste ponto, você poderá ver o controle personalizado na **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="256ae-135">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="256ae-136">Para verificar o progresso</span><span class="sxs-lookup"><span data-stu-id="256ae-136">To check your progress</span></span>  
  
-   <span data-ttu-id="256ae-137">Localize a nova guia chamada **Componentes de DebugControlLibrary** e clique para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="256ae-137">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="256ae-138">Quando ela abrir, você verá seu controle listado como **DebugControl** com o ícone padrão ao lado dele.</span><span class="sxs-lookup"><span data-stu-id="256ae-138">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="256ae-139">Adicionar uma Propriedade ao Controle Personalizado</span><span class="sxs-lookup"><span data-stu-id="256ae-139">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="256ae-140">Para demonstrar que o código de seu controle personalizado está sendo executado em tempo de design, você adicionará uma propriedade e definirá um ponto de interrupção no código que implementa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="256ae-140">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="256ae-141">Para adicionar uma propriedade ao controle personalizado</span><span class="sxs-lookup"><span data-stu-id="256ae-141">To add a property to your custom control</span></span>  
  
1.  <span data-ttu-id="256ae-142">Abra **DebugControl** no **Editor de Códigos**.</span><span class="sxs-lookup"><span data-stu-id="256ae-142">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="256ae-143">Adicione o seguinte código à definição da classe:</span><span class="sxs-lookup"><span data-stu-id="256ae-143">Add the following code to the class definition:</span></span>  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="256ae-144">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="256ae-144">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="256ae-145">Adicionar o Controle Personalizado ao Formulário de Host</span><span class="sxs-lookup"><span data-stu-id="256ae-145">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="256ae-146">Para depurar o comportamento em tempo de design do controle personalizado, você colocará uma instância da classe do controle personalizado em um formulário do host.</span><span class="sxs-lookup"><span data-stu-id="256ae-146">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="256ae-147">Para adicionar o controle personalizado ao formulário de host</span><span class="sxs-lookup"><span data-stu-id="256ae-147">To add your custom control to the host form</span></span>  
  
1.  <span data-ttu-id="256ae-148">No projeto "DebuggingExample", abra Form1 no **Designer de Formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="256ae-148">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="256ae-149">Na **caixa de Ferramentas**, abra a guia **Componentes de DebugControlLibrary** e arraste uma instância de **DebugControl** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="256ae-149">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3.  <span data-ttu-id="256ae-150">Encontre a propriedade personalizada `DemoString` na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="256ae-150">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="256ae-151">Observe que você pode alterar seu valor, da mesma forma que faria com qualquer outra propriedade.</span><span class="sxs-lookup"><span data-stu-id="256ae-151">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="256ae-152">Observe também que, quando a propriedade `DemoString` for selecionada, a cadeia de caracteres de descrição da propriedade aparecerá na parte inferior da janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="256ae-152">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="256ae-153">Configurar o Projeto para Depuração em Tempo de Design</span><span class="sxs-lookup"><span data-stu-id="256ae-153">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="256ae-154">Para depurar o comportamento em tempo de design do seu controle personalizado, você depurará uma instância separada do Visual Studio que está executando o código do seu controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="256ae-154">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="256ae-155">Para configurar o projeto para depuração em tempo de design</span><span class="sxs-lookup"><span data-stu-id="256ae-155">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="256ae-156">Clique com o botão direito do mouse no projeto **DebugControlLibrary** no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="256ae-156">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="256ae-157">Na folha de propriedades **DebugControlLibrary**, selecione a guia **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="256ae-157">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="256ae-158">Na seção **Iniciar Ação**, selecione **Iniciar programa externo**.</span><span class="sxs-lookup"><span data-stu-id="256ae-158">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="256ae-159">Você depurará uma instância separada do Visual Studio, então clique no botão de reticências (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) para procurar o IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="256ae-159">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="256ae-160">O nome do arquivo executável é **devenv.exe** e, se você o instalou no local padrão, o caminho dele é %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span><span class="sxs-lookup"><span data-stu-id="256ae-160">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3.  <span data-ttu-id="256ae-161">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="256ae-161">Click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="256ae-162">Clique com botão direito do mouse no projeto **DebugControlLibrary** e selecione **Definir como Projeto de Inicialização** para habilitar essa configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="256ae-162">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="256ae-163">Depurar o Controle Personalizado em Tempo de Design</span><span class="sxs-lookup"><span data-stu-id="256ae-163">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="256ae-164">Agora, você está pronto para depurar o controle personalizado enquanto ele é executado em modo de design.</span><span class="sxs-lookup"><span data-stu-id="256ae-164">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="256ae-165">Quando você iniciar a sessão de depuração, uma nova instância do Visual Studio será criada e você a usará para carregar a solução "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="256ae-165">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="256ae-166">Quando você abrir Form1 no **Designer de Formulários**, uma instância do controle personalizado será criada e começará a ser executada.</span><span class="sxs-lookup"><span data-stu-id="256ae-166">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="256ae-167">Para depurar o controle personalizado em tempo de design</span><span class="sxs-lookup"><span data-stu-id="256ae-167">To debug your custom control at design time</span></span>  
  
1.  <span data-ttu-id="256ae-168">Abra o arquivo de origem **DebugControl** no **Editor de Códigos** e coloque um ponto de interrupção no acessador `Set` da propriedade `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="256ae-168">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2.  <span data-ttu-id="256ae-169">Pressione F5 para iniciar a sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="256ae-169">Press F5 to start the debugging session.</span></span> <span data-ttu-id="256ae-170">Observe que uma nova instância do Visual Studio é criada.</span><span class="sxs-lookup"><span data-stu-id="256ae-170">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="256ae-171">É possível diferenciar as instâncias de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="256ae-171">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="256ae-172">A instância de depuração tem as palavras **Em execução** na barra de título</span><span class="sxs-lookup"><span data-stu-id="256ae-172">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="256ae-173">A instância de depuração tem o botão **Iniciar** em sua barra de ferramentas **Depurar** desabilitado</span><span class="sxs-lookup"><span data-stu-id="256ae-173">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="256ae-174">Seu ponto de interrupção é definido na instância de depuração.</span><span class="sxs-lookup"><span data-stu-id="256ae-174">Your breakpoint is set in the debugging instance.</span></span>  
  
3.  <span data-ttu-id="256ae-175">Na nova instância do Visual Studio, abra a solução "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="256ae-175">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="256ae-176">Você pode localizar facilmente a solução selecionando **Projetos Recentes** no menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="256ae-176">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="256ae-177">O arquivo de solução "DebuggingExample.sln" será listado como o arquivo usado mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="256ae-177">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="256ae-178">Abra Form1 no **Designer de Formulários** e selecione o controle **DebugControl**.</span><span class="sxs-lookup"><span data-stu-id="256ae-178">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5.  <span data-ttu-id="256ae-179">Altere o valor da propriedade `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="256ae-179">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="256ae-180">Observe que, quando você confirma a alteração, a instância de depuração do Visual Studio fica em foco e a execução é interrompida no ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="256ae-180">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="256ae-181">É possível percorrer passo a passo o acessador de propriedade, da mesma forma que você o faria com qualquer outro código.</span><span class="sxs-lookup"><span data-stu-id="256ae-181">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6.  <span data-ttu-id="256ae-182">Quando tiver terminado sua sessão de depuração, você pode sair ignorando a instância hospedada do Visual Studio ou clicando no botão **Parar Depuração** na instância de depuração.</span><span class="sxs-lookup"><span data-stu-id="256ae-182">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="256ae-183">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="256ae-183">Next Steps</span></span>  
 <span data-ttu-id="256ae-184">Agora que você pode depurar seus controles personalizados em tempo de design, há muitas possibilidades para expandir a interação do controle com o IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="256ae-184">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="256ae-185">Você pode usar o <xref:System.ComponentModel.Component.DesignMode%2A> propriedade do <xref:System.ComponentModel.Component> classe para escrever um código que será executado somente em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="256ae-185">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="256ae-186">Para obter detalhes, consulte <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="256ae-186">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="256ae-187">Há vários atributos que você pode aplicar a propriedades do controle para manipular a interação do seu controle personalizado com o designer.</span><span class="sxs-lookup"><span data-stu-id="256ae-187">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="256ae-188">Você pode encontrar esses atributos no <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="256ae-188">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="256ae-189">Você pode escrever um designer personalizado para seu controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="256ae-189">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="256ae-190">Isso lhe dá controle total sobre a experiência de design usando a infra-estrutura de designer extensível exposta pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="256ae-190">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="256ae-191">Para obter detalhes, consulte [Instruções passo a passo: criando um controle dos Windows Forms que aproveite os recursos de tempo de design do Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="256ae-191">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="256ae-192">Consulte também</span><span class="sxs-lookup"><span data-stu-id="256ae-192">See Also</span></span>  
 [<span data-ttu-id="256ae-193">Passo a passo: criando um controle dos Windows Forms que aproveita os recursos de tempo de design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="256ae-193">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [<span data-ttu-id="256ae-194">Como: acessar os serviços de tempo de Design</span><span class="sxs-lookup"><span data-stu-id="256ae-194">How to: Access Design-Time Services</span></span>](https://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [<span data-ttu-id="256ae-195">Como acessar o suporte em tempo de design nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="256ae-195">How to: Access Design-Time Support in Windows Forms</span></span>](https://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
