---
title: Prompt de Comando do Desenvolvedor para o Visual Studio
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715820"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="36e06-102">Prompt de Comando do Desenvolvedor para o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="36e06-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="36e06-103">O Prompt de comando do desenvolvedor para o Visual Studio permite que você use as ferramentas .NET Framework com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="36e06-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="36e06-104">É um prompt de comando que define automaticamente variáveis específicas do ambiente.</span><span class="sxs-lookup"><span data-stu-id="36e06-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="36e06-105">Depois de abrir o Prompt de comando do desenvolvedor, `ildasm` você `clrver`pode inserir os comandos para ferramentas do [Framework .NET,](index.md) tais como ou .</span><span class="sxs-lookup"><span data-stu-id="36e06-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36e06-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="36e06-106">Prerequisites</span></span>

- [<span data-ttu-id="36e06-107">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="36e06-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="36e06-108">Pesquisar pelo prompt de comando em seu computador</span><span class="sxs-lookup"><span data-stu-id="36e06-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="36e06-109">Você pode ter várias solicitações de comando, dependendo da versão do Visual Studio e de quaisquer SDKs e cargas de trabalho adicionais que você instalou.</span><span class="sxs-lookup"><span data-stu-id="36e06-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="36e06-110">Se as etapas seguintes não funcionarem, você pode tentar [localizar manualmente os arquivos da sua máquina](#manually-locate-the-files-on-your-machine) ou iniciar o prompt de comando de dentro do Visual [Studio](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="36e06-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="36e06-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="36e06-111">Windows 10</span></span>

1. <span data-ttu-id="36e06-112">Selecione **Iniciar** ![a tecla de logotipo do Windows no teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="36e06-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="36e06-113">e rolar até a letra **V**.</span><span class="sxs-lookup"><span data-stu-id="36e06-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="36e06-114">Expanda a pasta **Visual Studio 2019.**</span><span class="sxs-lookup"><span data-stu-id="36e06-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="36e06-115">Escolha **o Prompt de comando do desenvolvedor para VS 2019** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="36e06-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="36e06-116">Alternativamente, você pode começar a digitar o nome do prompt de comando na caixa de pesquisa na barra de tarefas e escolher o resultado que deseja, pois a lista de resultados começa a exibir as correspondências de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="36e06-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![Gif animado mostrando o comportamento de pesquisa no Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="36e06-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="36e06-118">Windows 8.1</span></span>

1. <span data-ttu-id="36e06-119">Vá para a tela **Inicial** pressionando a tecla do logotipo do Windows ![tecla do logotipo do Windows no teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="36e06-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="36e06-120">no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="36e06-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="36e06-121">Na tela **Iniciar,** **pressione Ctrl**+**Tab** para abrir a lista **de aplicativos** e, em seguida, pressione **V**. Isso traz à tona uma lista que inclui todas as solicitações de comando do Visual Studio instaladas.</span><span class="sxs-lookup"><span data-stu-id="36e06-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="36e06-122">Escolha **o Prompt de comando do desenvolvedor para VS 2019** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="36e06-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="36e06-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="36e06-123">Windows 7</span></span>

1. <span data-ttu-id="36e06-124">Escolha **Iniciar** e, em seguida, expandir **todos os programas**.</span><span class="sxs-lookup"><span data-stu-id="36e06-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="36e06-125">Escolha **visual studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, ou o prompt de comando que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="36e06-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Menu Iniciar do Windows 7 com o prompt de comando destacado](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="36e06-127">Se você tiver outros SDKs instalados, como o [SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) do Windows 10 ou [versões anteriores,](https://developer.microsoft.com/windows/downloads/sdk-archive)você poderá ver solicitações de comando adicionais.</span><span class="sxs-lookup"><span data-stu-id="36e06-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="36e06-128">Consulte a documentação das ferramentas individuais para determinar qual versão do prompt de comando você deve usar.</span><span class="sxs-lookup"><span data-stu-id="36e06-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="36e06-129">Localizar manualmente os arquivos em seu computador</span><span class="sxs-lookup"><span data-stu-id="36e06-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="36e06-130">Normalmente, os atalhos para as solicitações de comando instaladas são colocados na pasta **Menu Iniciar** para o Visual Studio, como em *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span><span class="sxs-lookup"><span data-stu-id="36e06-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="36e06-131">Mas se, por algum motivo, procurar o prompt de comando não produzir os resultados esperados, você pode tentar localizar manualmente o atalho em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="36e06-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="36e06-132">Tente procurar o nome do arquivo de solicitação de comando, como *VsDevCmd.bat,* ou vá para a pasta Ferramentas, como *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools (alterações* de caminho de acordo com a sua versão do Visual Studio, edição e local de instalação).</span><span class="sxs-lookup"><span data-stu-id="36e06-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="36e06-133">Inicie o prompt de comando de dentro do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="36e06-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="36e06-134">Para facilitar o acesso, você pode adicionar o Prompt de comando do desenvolvedor ou qualquer outro prompt de comando ao menu Ferramentas no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36e06-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="36e06-135">Para disponibilizar a ferramenta, adicione-a à lista de ferramentas externas.</span><span class="sxs-lookup"><span data-stu-id="36e06-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="36e06-136">Siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="36e06-136">Here are the steps:</span></span>

1. <span data-ttu-id="36e06-137">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36e06-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="36e06-138">Na janela de início, escolha **Continuar sem código**.</span><span class="sxs-lookup"><span data-stu-id="36e06-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="36e06-139">Na barra de menus, escolha **Ferramentas** > **Externas Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="36e06-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="36e06-140">Na caixa de diálogo **Ferramentas Externas**, escolha o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="36e06-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="36e06-141">Uma nova entrada é exibida.</span><span class="sxs-lookup"><span data-stu-id="36e06-141">A new entry appears.</span></span>

1. <span data-ttu-id="36e06-142">Insira um **Título** para o novo item de menu, como `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="36e06-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="36e06-143">No campo **Comando**, especifique o arquivo que deseja iniciar, como `%comspec%` ou `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="36e06-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="36e06-144">No campo **Argumentos,** especifique onde encontrar o prompt `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`de comando específico que deseja usar, como .</span><span class="sxs-lookup"><span data-stu-id="36e06-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="36e06-145">Este comando lança o Prompt de Comando do Desenvolvedor instalado com a Comunidade Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="36e06-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="36e06-146">Altere este valor de acordo com a sua versão, edição e local de instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36e06-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="36e06-147">No **campo de diretório inicial,** especifique o diretório no qual o prompt de comando será iniciado.</span><span class="sxs-lookup"><span data-stu-id="36e06-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="36e06-148">Escolha um valor como **Diretório de Projeto** selecionando a seta ao lado do campo.</span><span class="sxs-lookup"><span data-stu-id="36e06-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="36e06-149">Clique no botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="36e06-149">Choose the **OK** button.</span></span>

   ![Ferramentas externas dialogam com os valores de campo preenchidos.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="36e06-151">O novo item de menu foi adicionado e você pode acessar o prompt de comando no menu Ferramentas.</span><span class="sxs-lookup"><span data-stu-id="36e06-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Item de menu do prompt de comando no Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="36e06-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="36e06-153">See also</span></span>

- [<span data-ttu-id="36e06-154">Ferramentas do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="36e06-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="36e06-155">Gerenciando ferramentas externas</span><span class="sxs-lookup"><span data-stu-id="36e06-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="36e06-156">Use o conjunto de ferramentas Microsoft C++ da linha de comando</span><span class="sxs-lookup"><span data-stu-id="36e06-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
