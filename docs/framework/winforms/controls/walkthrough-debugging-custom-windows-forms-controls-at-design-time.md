---
title: 'Passo a passo: Depurando controles do Windows Forms no tempo de design'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 824d8a7de8e9e37899cb84d6cee9621f84a5bc65
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015694"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="be599-102">Passo a passo: Depurar controles de Windows Forms personalizados em tempo de design</span><span class="sxs-lookup"><span data-stu-id="be599-102">Walkthrough: Debug Custom Windows Forms Controls at Design Time</span></span>

<span data-ttu-id="be599-103">Quando criar um controle personalizado, frequentemente você achará necessário depurar seu comportamento em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="be599-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="be599-104">Isso será especialmente válido se você estiver criando um designer personalizado para seu controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="be599-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="be599-105">Para obter detalhes, [consulte Passo a passos: Criar um controle de Windows Forms que aproveita os recursos](creating-a-wf-control-design-time-features.md)de tempo de design do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be599-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

<span data-ttu-id="be599-106">Você pode depurar seus controles personalizados usando o Visual Studio, da mesma forma que depuraria qualquer outra classe do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be599-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="be599-107">A diferença é que você depurará uma instância separada do Visual Studio que está executando o código do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="be599-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="be599-108">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="be599-108">Create the project</span></span>

<span data-ttu-id="be599-109">A primeira etapa é criar o projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="be599-109">The first step is to create the application project.</span></span> <span data-ttu-id="be599-110">Você usará este projeto para criar o aplicativo que hospeda o controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="be599-110">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="be599-111">No Visual Studio, crie um projeto de aplicativo do Windows e nomeie-o **DebuggingExample**.</span><span class="sxs-lookup"><span data-stu-id="be599-111">In Visual Studio, create a Windows Application project, and name it **DebuggingExample**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="be599-112">Criar o projeto de biblioteca de controle</span><span class="sxs-lookup"><span data-stu-id="be599-112">Create the control library project</span></span>

1. <span data-ttu-id="be599-113">Adicione um projeto de **Biblioteca de controle do Windows** à solução.</span><span class="sxs-lookup"><span data-stu-id="be599-113">Add a **Windows Control Library** project to the solution.</span></span>

2. <span data-ttu-id="be599-114">Adicione um novo item **UserControl** ao projeto DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="be599-114">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="be599-115">Nomeie-o como **DebugControl**.</span><span class="sxs-lookup"><span data-stu-id="be599-115">Name it **DebugControl**.</span></span>

3. <span data-ttu-id="be599-116">Em **Gerenciador de soluções**, exclua o controle padrão do projeto excluindo o arquivo de código com um nome base de UserControl1.</span><span class="sxs-lookup"><span data-stu-id="be599-116">In **Solution Explorer**, delete the project's default control by deleting the code file with a base name of UserControl1.</span></span>

4. <span data-ttu-id="be599-117">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="be599-117">Build the solution.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="be599-118">Ponto de verificação</span><span class="sxs-lookup"><span data-stu-id="be599-118">Checkpoint</span></span>

<span data-ttu-id="be599-119">Neste ponto, você poderá ver o controle personalizado na **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="be599-119">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="be599-120">Para verificar seu progresso, localize a nova guia chamada **componentes DebugControlLibrary** e clique para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="be599-120">To check your progress, find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="be599-121">Quando ela abrir, você verá seu controle listado como **DebugControl** com o ícone padrão ao lado dele.</span><span class="sxs-lookup"><span data-stu-id="be599-121">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>

## <a name="add-a-property-to-your-custom-control"></a><span data-ttu-id="be599-122">Adicionar uma propriedade ao seu controle personalizado</span><span class="sxs-lookup"><span data-stu-id="be599-122">Add a property to your custom control</span></span>

<span data-ttu-id="be599-123">Para demonstrar que o código de seu controle personalizado está sendo executado em tempo de design, você adicionará uma propriedade e definirá um ponto de interrupção no código que implementa a propriedade.</span><span class="sxs-lookup"><span data-stu-id="be599-123">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>

1. <span data-ttu-id="be599-124">Abra **DebugControl** no **Editor de Códigos**.</span><span class="sxs-lookup"><span data-stu-id="be599-124">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="be599-125">Adicione o seguinte código à definição da classe:</span><span class="sxs-lookup"><span data-stu-id="be599-125">Add the following code to the class definition:</span></span>

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

2. <span data-ttu-id="be599-126">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="be599-126">Build the solution.</span></span>

## <a name="add-your-custom-control-to-the-host-form"></a><span data-ttu-id="be599-127">Adicionar seu controle personalizado ao formulário do host</span><span class="sxs-lookup"><span data-stu-id="be599-127">Add your custom control to the host form</span></span>

<span data-ttu-id="be599-128">Para depurar o comportamento em tempo de design do controle personalizado, você colocará uma instância da classe do controle personalizado em um formulário do host.</span><span class="sxs-lookup"><span data-stu-id="be599-128">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>

1. <span data-ttu-id="be599-129">No projeto "DebuggingExample", abra Form1 no **Designer de Formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="be599-129">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>

2. <span data-ttu-id="be599-130">Na **caixa de Ferramentas**, abra a guia **Componentes de DebugControlLibrary** e arraste uma instância de **DebugControl** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="be599-130">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>

3. <span data-ttu-id="be599-131">Encontre a propriedade personalizada `DemoString` na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="be599-131">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="be599-132">Observe que você pode alterar seu valor, da mesma forma que faria com qualquer outra propriedade.</span><span class="sxs-lookup"><span data-stu-id="be599-132">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="be599-133">Observe também que, quando a propriedade `DemoString` for selecionada, a cadeia de caracteres de descrição da propriedade aparecerá na parte inferior da janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="be599-133">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="be599-134">Configurar o projeto para depuração em tempo de design</span><span class="sxs-lookup"><span data-stu-id="be599-134">Set up the project for design-time debugging</span></span>

<span data-ttu-id="be599-135">Para depurar o comportamento em tempo de design do seu controle personalizado, você depurará uma instância separada do Visual Studio que está executando o código do seu controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="be599-135">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

1. <span data-ttu-id="be599-136">Clique com o botão direito do mouse no projeto **DebugControlLibrary** no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="be599-136">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="be599-137">Na folha de propriedades **DebugControlLibrary**, selecione a guia **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="be599-137">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>

     <span data-ttu-id="be599-138">Na seção **Iniciar Ação**, selecione **Iniciar programa externo**.</span><span class="sxs-lookup"><span data-stu-id="be599-138">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="be599-139">Você estará Depurando uma instância separada do Visual Studio, então clique nas reticências (![o botão de reticências (...) no botão janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png)) para procurar o IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be599-139">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="be599-140">O nome do arquivo executável é **devenv. exe**e, se você tiver instalado no local padrão, seu caminho será *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE*.</span><span class="sxs-lookup"><span data-stu-id="be599-140">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE*.</span></span>

3. <span data-ttu-id="be599-141">Selecione **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="be599-141">Select **OK** to close the dialog box.</span></span>

4. <span data-ttu-id="be599-142">Clique com botão direito do mouse no projeto **DebugControlLibrary** e selecione **Definir como Projeto de Inicialização** para habilitar essa configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="be599-142">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="debug-your-custom-control-at-design-time"></a><span data-ttu-id="be599-143">Depurar seu controle personalizado em tempo de design</span><span class="sxs-lookup"><span data-stu-id="be599-143">Debug your custom control at design time</span></span>

<span data-ttu-id="be599-144">Agora, você está pronto para depurar o controle personalizado enquanto ele é executado em modo de design.</span><span class="sxs-lookup"><span data-stu-id="be599-144">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="be599-145">Quando você iniciar a sessão de depuração, uma nova instância do Visual Studio será criada e você a usará para carregar a solução "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="be599-145">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="be599-146">Quando você abrir Form1 no **Designer de Formulários**, uma instância do controle personalizado será criada e começará a ser executada.</span><span class="sxs-lookup"><span data-stu-id="be599-146">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>

1. <span data-ttu-id="be599-147">Abra o arquivo de origem **DebugControl** no **Editor de Códigos** e coloque um ponto de interrupção no acessador `Set` da propriedade `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="be599-147">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>

2. <span data-ttu-id="be599-148">Pressione **F5** para iniciar a sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="be599-148">Press **F5** to start the debugging session.</span></span> <span data-ttu-id="be599-149">Uma nova instância do Visual Studio é criada.</span><span class="sxs-lookup"><span data-stu-id="be599-149">A new instance of Visual Studio is created.</span></span> <span data-ttu-id="be599-150">É possível diferenciar as instâncias de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="be599-150">You can distinguish between the instances in two ways:</span></span>

    - <span data-ttu-id="be599-151">A instância de depuração tem as palavras **Em execução** na barra de título</span><span class="sxs-lookup"><span data-stu-id="be599-151">The debugging instance has the word **Running** in its title bar</span></span>

    - <span data-ttu-id="be599-152">A instância de depuração tem o botão **Iniciar** em sua barra de ferramentas **Depurar** desabilitado</span><span class="sxs-lookup"><span data-stu-id="be599-152">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>

   <span data-ttu-id="be599-153">Seu ponto de interrupção é definido na instância de depuração.</span><span class="sxs-lookup"><span data-stu-id="be599-153">Your breakpoint is set in the debugging instance.</span></span>

3. <span data-ttu-id="be599-154">Na nova instância do Visual Studio, abra a solução "DebuggingExample".</span><span class="sxs-lookup"><span data-stu-id="be599-154">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="be599-155">Você pode localizar facilmente a solução selecionando **Projetos Recentes** no menu **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="be599-155">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="be599-156">O arquivo de solução "DebuggingExample.sln" será listado como o arquivo usado mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="be599-156">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="be599-157">Abra Form1 no **Designer de Formulários** e selecione o controle **DebugControl**.</span><span class="sxs-lookup"><span data-stu-id="be599-157">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>

5. <span data-ttu-id="be599-158">Altere o valor da propriedade `DemoString`.</span><span class="sxs-lookup"><span data-stu-id="be599-158">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="be599-159">Quando você confirma a alteração, a instância de depuração do Visual Studio adquire o foco e a execução é interrompida em seu ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="be599-159">When you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="be599-160">É possível percorrer passo a passo o acessador de propriedade, da mesma forma que você o faria com qualquer outro código.</span><span class="sxs-lookup"><span data-stu-id="be599-160">You can single-step through the property accessor just as your would any other code.</span></span>

6. <span data-ttu-id="be599-161">Para interromper a depuração, saia da instância hospedada do Visual Studio ou selecione o botão **parar depuração** na instância de depuração.</span><span class="sxs-lookup"><span data-stu-id="be599-161">To stop debugging, exit the hosted instance of Visual Studio or select the **Stop Debugging** button in the debugging instance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="be599-162">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="be599-162">Next steps</span></span>

<span data-ttu-id="be599-163">Agora que você pode depurar seus controles personalizados em tempo de design, há muitas possibilidades para expandir a interação do controle com o IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be599-163">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>

- <span data-ttu-id="be599-164">Você pode usar a <xref:System.ComponentModel.Component.DesignMode%2A> propriedade <xref:System.ComponentModel.Component> da classe para escrever o código que será executado somente no momento do design.</span><span class="sxs-lookup"><span data-stu-id="be599-164">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="be599-165">Para obter detalhes, consulte <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="be599-165">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>

- <span data-ttu-id="be599-166">Há vários atributos que você pode aplicar a propriedades do controle para manipular a interação do seu controle personalizado com o designer.</span><span class="sxs-lookup"><span data-stu-id="be599-166">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="be599-167">Você pode encontrar esses atributos no <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="be599-167">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="be599-168">Você pode escrever um designer personalizado para seu controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="be599-168">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="be599-169">Isso lhe dá controle total sobre a experiência de design usando a infra-estrutura de designer extensível exposta pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be599-169">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="be599-170">Para obter detalhes, [consulte Passo a passos: Criar um controle de Windows Forms que aproveita os recursos](creating-a-wf-control-design-time-features.md)de tempo de design do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be599-170">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be599-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be599-171">See also</span></span>

- [<span data-ttu-id="be599-172">Passo a passo: Criando um controle de Windows Forms que aproveita os recursos de tempo de design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be599-172">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
