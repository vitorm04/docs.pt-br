---
title: Prompt de Comando do Desenvolvedor para o Visual Studio
ms.date: 08/14/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20dc7caa9e4c3e023bf2848b1dd8c63a9b94a01b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170003"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="e26bc-102">Prompt de Comando do Desenvolvedor para o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e26bc-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="e26bc-103">O Prompt de Comando do Desenvolvedor para Visual Studio permite que você use ferramentas do .NET Framework com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="e26bc-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="e26bc-104">Trata-se de um prompt de comando que define variáveis de ambiente específicas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e26bc-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
[<span data-ttu-id="e26bc-105">Baixar o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e26bc-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="e26bc-106">Pesquisar pelo prompt de comando em seu computador</span><span class="sxs-lookup"><span data-stu-id="e26bc-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="e26bc-107">É possível que haja vários prompts de comando, dependendo da versão do Visual Studio e de todos os SDKs adicionais instalados.</span><span class="sxs-lookup"><span data-stu-id="e26bc-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="e26bc-108">Por exemplo, as versões 64 bits do Visual Studio oferecem prompts de comando 32 e 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e26bc-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="e26bc-109">(As versões 32 e 64 bits da maioria das ferramentas são iguais; porém, algumas ferramentas fazem alterações específicas em ambientes 32 e 64 bits.) Se as etapas a seguir não funcionarem, você poderá tentar [Localizar manualmente os arquivos em seu computador](#manually-locate-the-files-on-your-machine) ou [Executar o prompt de comando de dentro do Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e26bc-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="e26bc-110">No Windows 10</span><span class="sxs-lookup"><span data-stu-id="e26bc-110">In Windows 10</span></span>

1. <span data-ttu-id="e26bc-111">Na caixa de pesquisa na barra de tarefas, comece a digitar o nome da ferramenta, como `dev` ou `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="e26bc-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="e26bc-112">Isso abre uma lista de aplicativos instalados que correspondem ao seu padrão de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e26bc-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="e26bc-113">Se você estiver procurando por um prompt de comando diferente, experimente digitar um termo de pesquisa diferente, como `prompt`.</span><span class="sxs-lookup"><span data-stu-id="e26bc-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="e26bc-114">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="e26bc-114">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="e26bc-115">No Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="e26bc-115">In Windows 8.1</span></span>

1. <span data-ttu-id="e26bc-116">Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="e26bc-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="e26bc-117">Na tela **Iniciar**, pressione **Ctrl**+**Tab** para abrir a lista **Aplicativos** e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="e26bc-117">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="e26bc-118">Isso mostra uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="e26bc-118">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="e26bc-119">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="e26bc-119">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="e26bc-120">No Windows 8</span><span class="sxs-lookup"><span data-stu-id="e26bc-120">In Windows 8</span></span>

1. <span data-ttu-id="e26bc-121">Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="e26bc-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="e26bc-122">Na tela **Iniciar**, pressione a tecla do logotipo do Windows ![Logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="e26bc-122">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="e26bc-123">Escolha o ícone **Exibição de aplicativos** na parte inferior da tela e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="e26bc-123">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="e26bc-124">Isso mostra uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="e26bc-124">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="e26bc-125">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="e26bc-125">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="e26bc-126">No Windows 7</span><span class="sxs-lookup"><span data-stu-id="e26bc-126">In Windows 7</span></span>

1. <span data-ttu-id="e26bc-127">Escolha **Iniciar**, expanda **Todos os Programas** e expanda **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="e26bc-127">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="e26bc-128">Dependendo da versão do Visual Studio que você instalou, escolha **Ferramentas do Visual Studio**, **Prompt de Comando do Visual Studio** ou o prompt de comando que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="e26bc-128">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="e26bc-129">Se houver outros SDKs instalados, como o [SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [versões anteriores](https://developer.microsoft.com/windows/downloads/sdk-archive), poderão ser exibidos outros prompts de comando, para as arquiteturas ARM, x86 ou x64.</span><span class="sxs-lookup"><span data-stu-id="e26bc-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="e26bc-130">Consulte a documentação das ferramentas individuais para determinar qual versão do prompt de comando você deve usar.</span><span class="sxs-lookup"><span data-stu-id="e26bc-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="e26bc-131">Localizar manualmente os arquivos em seu computador</span><span class="sxs-lookup"><span data-stu-id="e26bc-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="e26bc-132">Normalmente, os atalhos para os prompts de comando que você instalou serão colocados na pasta **Menu Iniciar** do Visual Studio, como em C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="e26bc-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="e26bc-133">Porém, se por algum motivo a pesquisa do prompt de comando não gerar os resultados esperados, você poderá tentar localizar manualmente o atalho em seu computador.</span><span class="sxs-lookup"><span data-stu-id="e26bc-133">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="e26bc-134">Tente pesquisar pelo nome do arquivo do prompt de comando, como *VsDevCmd.bat* ou acesse a pasta Tools, como C:\Arquivos de Programas (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (o caminho mudará conforme seu local de instalação, edição e versão do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="e26bc-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="e26bc-135">Executar o prompt de comando de dentro do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e26bc-135">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="e26bc-136">Para facilitar o acesso, você pode adicionar o Prompt de Comando do Desenvolvedor do Visual Studio ou qualquer outro prompt de comando ao menu **Ferramentas** do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e26bc-136">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="e26bc-137">Para disponibilizar a ferramenta, adicione-a à lista de ferramentas externas.</span><span class="sxs-lookup"><span data-stu-id="e26bc-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="e26bc-138">Aqui estão as etapas:</span><span class="sxs-lookup"><span data-stu-id="e26bc-138">Here are the steps:</span></span>

1. <span data-ttu-id="e26bc-139">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e26bc-139">Open Visual Studio.</span></span>

2. <span data-ttu-id="e26bc-140">Selecione o menu **Ferramentas** e, em seguida, escolha **Ferramentas Externas**.</span><span class="sxs-lookup"><span data-stu-id="e26bc-140">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="e26bc-141">Na caixa de diálogo **Ferramentas Externas**, escolha o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="e26bc-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="e26bc-142">Uma nova entrada é exibida.</span><span class="sxs-lookup"><span data-stu-id="e26bc-142">A new entry appears.</span></span>

4. <span data-ttu-id="e26bc-143">Insira um **Título** para o novo item de menu, como `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="e26bc-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="e26bc-144">No campo **Comando**, especifique o arquivo que deseja iniciar, como `%comspec%` ou `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="e26bc-144">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="e26bc-145">No campo **Argumentos**, especifique em que ponto encontrar o prompt de comando específico que você deseja usar como `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (esse comando inicializa o Prompt de Comando do Desenvolvedor que é instalado com o Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="e26bc-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="e26bc-146">Altere este valor de acordo com a sua versão, edição e local de instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e26bc-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="e26bc-147">Escolha um valor para o campo **Diretório inicial**, como **Diretório do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="e26bc-147">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="e26bc-148">Escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="e26bc-148">Choose the **OK** button.</span></span>

   <span data-ttu-id="e26bc-149">O novo item de menu foi adicionado e você pode acessar o prompt de comando no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="e26bc-149">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Item de menu do prompt de comando no Visual Studio](media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="e26bc-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e26bc-151">See also</span></span>

- [<span data-ttu-id="e26bc-152">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="e26bc-152">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="e26bc-153">Gerenciando ferramentas externas</span><span class="sxs-lookup"><span data-stu-id="e26bc-153">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
