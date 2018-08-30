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
ms.openlocfilehash: 4c95074190419dd3e984c7659ede917b83b97f08
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42754236"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="6d695-102">Prompt de Comando do Desenvolvedor para o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6d695-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="6d695-103">O Prompt de Comando do Desenvolvedor do Visual Studio define automaticamente as variáveis de ambiente que permitem usar as ferramentas do .NET Framework com facilidade.</span><span class="sxs-lookup"><span data-stu-id="6d695-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span>

> [!div class="button"]
[<span data-ttu-id="6d695-104">Baixar o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6d695-104">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="6d695-105">Pesquisando o prompt de comando em seu computador</span><span class="sxs-lookup"><span data-stu-id="6d695-105">Searching for the command prompt on your machine</span></span>

<span data-ttu-id="6d695-106">É possível que haja vários prompts de comando, dependendo da versão do Visual Studio e de todos os SDKs adicionais instalados.</span><span class="sxs-lookup"><span data-stu-id="6d695-106">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="6d695-107">Por exemplo, as versões 64 bits do Visual Studio oferecem prompts de comando 32 e 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6d695-107">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="6d695-108">(As versões 32 e 64 bits da maioria das ferramentas são iguais; porém, algumas ferramentas fazem alterações específicas em ambientes 32 e 64 bits.) Se as etapas a seguir não funcionarem, tente [Localizar manualmente os arquivos em seu computador](#manually-locating-the-files-on-your-machine) ou [Executar o prompt de comando de dentro do Visual Studio](#running-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6d695-108">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locating the files on your machine](#manually-locating-the-files-on-your-machine) or [Running the command prompt from inside Visual Studio](#running-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="6d695-109">No Windows 10</span><span class="sxs-lookup"><span data-stu-id="6d695-109">In Windows 10</span></span>

1. <span data-ttu-id="6d695-110">Na caixa de pesquisa na barra de tarefas, comece a digitar o nome da ferramenta, como `dev` ou `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="6d695-110">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="6d695-111">Isso abre uma lista de aplicativos instalados que correspondem ao seu padrão de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="6d695-111">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="6d695-112">Se você estiver procurando por um prompt de comando diferente, experimente digitar um termo de pesquisa diferente, como `prompt`.</span><span class="sxs-lookup"><span data-stu-id="6d695-112">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="6d695-113">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="6d695-113">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="6d695-114">No Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="6d695-114">In Windows 8.1</span></span>

1. <span data-ttu-id="6d695-115">Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="6d695-115">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="6d695-116">Na tela **Iniciar**, pressione `CTRL + TAB` para abrir a lista **Aplicativos** e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="6d695-116">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="6d695-117">Isso mostra uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="6d695-117">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="6d695-118">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="6d695-118">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="6d695-119">No Windows 8</span><span class="sxs-lookup"><span data-stu-id="6d695-119">In Windows 8</span></span>

1. <span data-ttu-id="6d695-120">Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="6d695-120">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="6d695-121">Na tela **Iniciar**, pressione a tecla do logotipo do Windows ![Logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="6d695-121">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="6d695-122">Escolha o ícone **Exibição de aplicativos** na parte inferior da tela e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="6d695-122">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="6d695-123">Isso mostra uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="6d695-123">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="6d695-124">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="6d695-124">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="6d695-125">No Windows 7</span><span class="sxs-lookup"><span data-stu-id="6d695-125">In Windows 7</span></span>

1. <span data-ttu-id="6d695-126">Escolha **Iniciar**, expanda **Todos os Programas** e expanda **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6d695-126">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="6d695-127">Dependendo da versão do Visual Studio que você instalou, escolha **Ferramentas do Visual Studio**, **Prompt de Comando do Visual Studio** ou o prompt de comando que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="6d695-127">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="6d695-128">Se houver outros SDKs instalados, como o [SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [versões anteriores](https://developer.microsoft.com/windows/downloads/sdk-archive), poderão ser exibidos outros prompts de comando, para as arquiteturas ARM, x86 ou x64.</span><span class="sxs-lookup"><span data-stu-id="6d695-128">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="6d695-129">Consulte a documentação das ferramentas individuais para determinar qual versão do prompt de comando você deve usar.</span><span class="sxs-lookup"><span data-stu-id="6d695-129">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="6d695-130">Localizar manualmente os arquivos em seu computador</span><span class="sxs-lookup"><span data-stu-id="6d695-130">Manually locate the files on your machine</span></span>

<span data-ttu-id="6d695-131">Normalmente, os atalhos para os prompts de comando que você instalou serão colocados na pasta **Menu Iniciar** do Visual Studio, como em C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="6d695-131">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="6d695-132">Porém, se por algum motivo a pesquisa do prompt de comando não gerar os resultados esperados, você poderá tentar localizar manualmente o atalho em seu computador.</span><span class="sxs-lookup"><span data-stu-id="6d695-132">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="6d695-133">Tente pesquisar pelo nome do arquivo do prompt de comando, como *VsDevCmd.bat* ou acesse a pasta Tools, como C:\Arquivos de Programas (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (o caminho mudará conforme seu local de instalação, edição e versão do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="6d695-133">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="6d695-134">Executar o prompt de comando de dentro do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6d695-134">Run command prompt from inside Visual Studio</span></span>

<span data-ttu-id="6d695-135">Para facilitar o acesso, você pode adicionar o Prompt de Comando do Desenvolvedor do Visual Studio ou qualquer outro prompt de comando ao menu **Ferramentas** do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6d695-135">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="6d695-136">Para disponibilizar a ferramenta, adicione-a à lista de ferramentas externas.</span><span class="sxs-lookup"><span data-stu-id="6d695-136">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="6d695-137">Aqui estão as etapas:</span><span class="sxs-lookup"><span data-stu-id="6d695-137">Here are the steps:</span></span>

1. <span data-ttu-id="6d695-138">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6d695-138">Open Visual Studio.</span></span>

2. <span data-ttu-id="6d695-139">Selecione o menu **Ferramentas** e, em seguida, escolha **Ferramentas Externas**.</span><span class="sxs-lookup"><span data-stu-id="6d695-139">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="6d695-140">Na caixa de diálogo **Ferramentas Externas**, escolha o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="6d695-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="6d695-141">Uma nova entrada é exibida.</span><span class="sxs-lookup"><span data-stu-id="6d695-141">A new entry appears.</span></span>

4. <span data-ttu-id="6d695-142">Insira um **Título** para o novo item de menu, como `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="6d695-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="6d695-143">No campo **Comando**, especifique o arquivo que deseja iniciar, como `%comspec%` ou `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="6d695-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="6d695-144">No campo **Argumentos**, especifique em que ponto encontrar o prompt de comando específico que você deseja usar como `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (esse comando inicializa o Prompt de Comando do Desenvolvedor que é instalado com o Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="6d695-144">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="6d695-145">Altere este valor de acordo com a sua versão, edição e local de instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6d695-145">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="6d695-146">Escolha um valor para o campo **Diretório inicial**, como **Diretório do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="6d695-146">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="6d695-147">Escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="6d695-147">Choose the **OK** button.</span></span>

   <span data-ttu-id="6d695-148">O novo item de menu foi adicionado e você pode acessar o prompt de comando no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="6d695-148">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d695-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d695-149">See also</span></span>

- [<span data-ttu-id="6d695-150">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="6d695-150">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="6d695-151">Gerenciando ferramentas externas</span><span class="sxs-lookup"><span data-stu-id="6d695-151">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
