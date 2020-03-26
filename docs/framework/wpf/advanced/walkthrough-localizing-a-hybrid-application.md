---
title: 'Instruções passo a passo: localizando um aplicativo híbrido'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111108"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="fab9e-102">Instruções passo a passo: localizando um aplicativo híbrido</span><span class="sxs-lookup"><span data-stu-id="fab9e-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="fab9e-103">Este passo a passo mostra [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como localizar elementos em um aplicativo híbrido baseado no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fab9e-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a Windows Forms-based hybrid application.</span></span>

<span data-ttu-id="fab9e-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="fab9e-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="fab9e-105">Criando o projeto de host do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fab9e-105">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="fab9e-106">Atributo de conteúdo localizável.</span><span class="sxs-lookup"><span data-stu-id="fab9e-106">Adding localizable content.</span></span>

- <span data-ttu-id="fab9e-107">Habilitando a localização.</span><span class="sxs-lookup"><span data-stu-id="fab9e-107">Enabling localization.</span></span>

- <span data-ttu-id="fab9e-108">Atribuindo identificadores de recursos.</span><span class="sxs-lookup"><span data-stu-id="fab9e-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="fab9e-109">Usando a ferramenta LocBaml para produzir um assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="fab9e-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="fab9e-110">Para obter uma lista completa de códigodas das tarefas ilustradas neste passo a passo, consulte [Localing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="fab9e-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="fab9e-111">Quando tiver terminado, você terá um aplicativo híbrido localizado.</span><span class="sxs-lookup"><span data-stu-id="fab9e-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fab9e-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fab9e-112">Prerequisites</span></span>

<span data-ttu-id="fab9e-113">Você precisará dos seguintes componentes para concluir este passo a passo:</span><span class="sxs-lookup"><span data-stu-id="fab9e-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="fab9e-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fab9e-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="fab9e-115">Criando o projeto de host do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fab9e-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="fab9e-116">O primeiro passo é criar o projeto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de aplicativo Do Windows Forms e adicionar um elemento com conteúdo que você irá localizar.</span><span class="sxs-lookup"><span data-stu-id="fab9e-116">The first step is to create the Windows Forms application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="fab9e-117">Criar o projeto de host</span><span class="sxs-lookup"><span data-stu-id="fab9e-117">To create the host project</span></span>

1. <span data-ttu-id="fab9e-118">Crie um projeto **wpf app** chamado `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="fab9e-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="fab9e-119">(**Arquivo** > **Novo** > **Projeto** > Visual**C#** ou Visual **Basic** > Classic**Desktop** > **WPF Application**).</span><span class="sxs-lookup"><span data-stu-id="fab9e-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="fab9e-120">Adicione [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> um `SimpleControl` elemento chamado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fab9e-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="fab9e-121">Use <xref:System.Windows.Forms.Integration.ElementHost> o controle `SimpleControl` para colocar um elemento no formulário.</span><span class="sxs-lookup"><span data-stu-id="fab9e-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="fab9e-122">Para obter mais informações, consulte [Passo a Passo: Hospedando um controle composto 3D WPF em formulários windows](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fab9e-122">For more information, see [Walkthrough: Hosting a 3D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="fab9e-123">Adicionando conteúdo localizável</span><span class="sxs-lookup"><span data-stu-id="fab9e-123">Adding Localizable Content</span></span>

<span data-ttu-id="fab9e-124">Em seguida, você adicionará um controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de rótulo do Windows Forms e definirá o conteúdo do elemento como uma seqüência de string satisfaz.</span><span class="sxs-lookup"><span data-stu-id="fab9e-124">Next, you will add a Windows Forms label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="fab9e-125">Para adicionar um conteúdo localizável</span><span class="sxs-lookup"><span data-stu-id="fab9e-125">To add localizable content</span></span>

1. <span data-ttu-id="fab9e-126">No **Solution Explorer**, clique duas vezes em **SimpleControl.xaml** para abri-lo no WPF Designer.</span><span class="sxs-lookup"><span data-stu-id="fab9e-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the WPF Designer.</span></span>

2. <span data-ttu-id="fab9e-127">Defina o <xref:System.Windows.Controls.Button> conteúdo do controle usando o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="fab9e-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="fab9e-128">No **Solution Explorer,** clique duas vezes em **Formulário1** para abri-lo no Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="fab9e-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="fab9e-129">Abra a **caixa de ferramentas** e clique duas vezes em **Etiqueta** para adicionar um controle de etiqueta ao formulário.</span><span class="sxs-lookup"><span data-stu-id="fab9e-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="fab9e-130">Defina o <xref:System.Windows.Forms.Control.Text%2A> valor `"Hello"`de sua propriedade para .</span><span class="sxs-lookup"><span data-stu-id="fab9e-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="fab9e-131">Pressione **F5** para construir e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fab9e-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="fab9e-132">Tanto `SimpleControl` o elemento quanto o controle da etiqueta exibem o texto **"Olá".**</span><span class="sxs-lookup"><span data-stu-id="fab9e-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="fab9e-133">Habilitando a localização</span><span class="sxs-lookup"><span data-stu-id="fab9e-133">Enabling Localization</span></span>

<span data-ttu-id="fab9e-134">O Designer de Formulários do Windows fornece configurações para habilitar a localização em um assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="fab9e-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="fab9e-135">Para permitir a localização</span><span class="sxs-lookup"><span data-stu-id="fab9e-135">To enable localization</span></span>

1. <span data-ttu-id="fab9e-136">No **Solution Explorer,** clique duas vezes **em Form1.cs** para abri-lo no Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="fab9e-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="fab9e-137">Na janela **Propriedades,** defina o valor da propriedade `true` **Localizable** do formulário como .</span><span class="sxs-lookup"><span data-stu-id="fab9e-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="fab9e-138">Na janela **Propriedades,** defina o valor da propriedade **do idioma** para **espanhol (Espanha)**.</span><span class="sxs-lookup"><span data-stu-id="fab9e-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="fab9e-139">No Designer de Formulários do Windows, selecione o controle de rótulo.</span><span class="sxs-lookup"><span data-stu-id="fab9e-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="fab9e-140">Na janela **Propriedades,** defina <xref:System.Windows.Forms.Control.Text%2A> o `"Hola"`valor do imóvel como .</span><span class="sxs-lookup"><span data-stu-id="fab9e-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="fab9e-141">Um novo arquivo de recursos chamado Form1.es-ES.resx é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fab9e-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="fab9e-142">No **Solution Explorer,** clique com o botão **direito do Form1.cs** e clique em Exibir **Código** para abri-lo no Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="fab9e-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="fab9e-143">Copie o seguinte `Form1` código no construtor, `InitializeComponent`precedendo a chamada para .</span><span class="sxs-lookup"><span data-stu-id="fab9e-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="fab9e-144">No **Solution Explorer,** clique com o botão direito do mouse **LocalizingWpfInWf** e clique **em Descarregar projeto**.</span><span class="sxs-lookup"><span data-stu-id="fab9e-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="fab9e-145">O nome do projeto está rotulado **(indisponível)**.</span><span class="sxs-lookup"><span data-stu-id="fab9e-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="fab9e-146">Clique com o botão direito do mouse **LocalizingWpfInWf**e clique **em Editar LocalizingWpfInWf.csproj**.</span><span class="sxs-lookup"><span data-stu-id="fab9e-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="fab9e-147">O arquivo de projeto é aberto no Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="fab9e-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="fab9e-148">Copie a linha a `PropertyGroup` seguir na primeira no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="fab9e-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="fab9e-149">Salve o arquivo de projeto e feche-o.</span><span class="sxs-lookup"><span data-stu-id="fab9e-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="fab9e-150">No **Solution Explorer,** clique com o botão direito do mouse **LocalizingWpfInWf** e clique em **Recarregar projeto**.</span><span class="sxs-lookup"><span data-stu-id="fab9e-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="fab9e-151">Atribuindo identificadores de recursos</span><span class="sxs-lookup"><span data-stu-id="fab9e-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="fab9e-152">Você pode mapear o conteúdo localizável para assemblies de recursos usando identificadores de recurso.</span><span class="sxs-lookup"><span data-stu-id="fab9e-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="fab9e-153">O aplicativo MsBuild.exe atribui automaticamente identificadores de `updateuid` recursos quando você especifica a opção.</span><span class="sxs-lookup"><span data-stu-id="fab9e-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="fab9e-154">Para atribuir identificadores de recursos</span><span class="sxs-lookup"><span data-stu-id="fab9e-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="fab9e-155">A partir do menu Iniciar, abra o Prompt de comando do desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fab9e-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="fab9e-156">Use o comando a seguir para atribuir identificadores de recurso ao seu conteúdo localizável.</span><span class="sxs-lookup"><span data-stu-id="fab9e-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="fab9e-157">No **Solution Explorer**, clique duas vezes em **SimpleControl.xaml** para abri-lo no Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="fab9e-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="fab9e-158">Você verá que `msbuild` o comando `Uid` adicionou o atributo a todos os elementos.</span><span class="sxs-lookup"><span data-stu-id="fab9e-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="fab9e-159">Isso facilita a localização por meio da atribuição de identificadores de recurso.</span><span class="sxs-lookup"><span data-stu-id="fab9e-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="fab9e-160">Pressione **F6** para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="fab9e-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="fab9e-161">Usando LocBaml para produzir um assembly satélite</span><span class="sxs-lookup"><span data-stu-id="fab9e-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="fab9e-162">Seu conteúdo localizado é armazenado em um conjunto de *satélite*somente com recursos .</span><span class="sxs-lookup"><span data-stu-id="fab9e-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="fab9e-163">Use a ferramenta de linha de comando LocBaml.exe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para produzir um conjunto localizado para o seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="fab9e-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="fab9e-164">Para produzir um assembly satélite</span><span class="sxs-lookup"><span data-stu-id="fab9e-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="fab9e-165">Copie LocBaml.exe para sua pasta do projeto obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="fab9e-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="fab9e-166">Para obter mais informações, consulte [Localize an Application](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="fab9e-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="fab9e-167">Na janela do Prompt de Comando, use o seguinte comando para extrair cadeias de caracteres de recurso em um arquivo temporário.</span><span class="sxs-lookup"><span data-stu-id="fab9e-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="fab9e-168">Abra o arquivo temporário.csv com o Visual Studio ou outro editor de texto.</span><span class="sxs-lookup"><span data-stu-id="fab9e-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="fab9e-169">Substitua `"Hello"` a corda por `"Hola"`sua tradução em espanhol, .</span><span class="sxs-lookup"><span data-stu-id="fab9e-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="fab9e-170">Salve o arquivo temp.csv.</span><span class="sxs-lookup"><span data-stu-id="fab9e-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="fab9e-171">Use o seguinte comando para gerar o arquivo de recurso localizado.</span><span class="sxs-lookup"><span data-stu-id="fab9e-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="fab9e-172">O arquivo LocalizingWpfInWf.g.es-ES.resources é criado na pasta obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="fab9e-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="fab9e-173">Use o seguinte comando para compilar o assembly satélite localizado.</span><span class="sxs-lookup"><span data-stu-id="fab9e-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="fab9e-174">O arquivo LocalizingWpfInWf.resources.dll é criado na pasta obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="fab9e-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="fab9e-175">Copie o arquivo LocalizingWpfInWf.resources.dll para a pasta do projeto bin\Debug\es-ES.</span><span class="sxs-lookup"><span data-stu-id="fab9e-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="fab9e-176">Substitua o arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="fab9e-176">Replace the existing file.</span></span>

8. <span data-ttu-id="fab9e-177">Execute LocalizingWpfInWf.exe, que está localizado na pasta bin\Debug de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="fab9e-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="fab9e-178">Não recompilar o aplicativo ou o assembly satélite será substituído.</span><span class="sxs-lookup"><span data-stu-id="fab9e-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="fab9e-179">O aplicativo mostra as cadeias de caracteres localizadas em vez de cadeias de caracteres em inglês.</span><span class="sxs-lookup"><span data-stu-id="fab9e-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="fab9e-180">Confira também</span><span class="sxs-lookup"><span data-stu-id="fab9e-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="fab9e-181">Localize um aplicativo</span><span class="sxs-lookup"><span data-stu-id="fab9e-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="fab9e-182">[Instruções passo a passo: localizando Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fab9e-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="fab9e-183">Criar XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fab9e-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
