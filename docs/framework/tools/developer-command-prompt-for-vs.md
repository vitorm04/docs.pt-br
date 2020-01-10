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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715820"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="17149-102">Prompt de Comando do Desenvolvedor para o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="17149-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="17149-103">O Prompt de Comando do Desenvolvedor para Visual Studio permite que você use .NET Framework ferramentas com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="17149-103">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="17149-104">É um prompt de comando que define automaticamente variáveis de ambiente específicas.</span><span class="sxs-lookup"><span data-stu-id="17149-104">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="17149-105">Depois de abrir Prompt de Comando do Desenvolvedor, você pode inserir os comandos para [.NET Framework ferramentas](index.md) como `ildasm` ou `clrver`.</span><span class="sxs-lookup"><span data-stu-id="17149-105">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="17149-106">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="17149-106">Prerequisites</span></span>

- [<span data-ttu-id="17149-107">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="17149-107">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="17149-108">Pesquisar pelo prompt de comando em seu computador</span><span class="sxs-lookup"><span data-stu-id="17149-108">Search for the command prompt on your machine</span></span>

<span data-ttu-id="17149-109">Você pode ter vários prompts de comando, dependendo da versão do Visual Studio e de quaisquer SDKs e cargas de trabalho adicionais instalados.</span><span class="sxs-lookup"><span data-stu-id="17149-109">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="17149-110">Se as etapas a seguir não funcionarem, você poderá tentar [localizar manualmente os arquivos em seu computador](#manually-locate-the-files-on-your-machine) ou [iniciar o prompt de comando de dentro do Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="17149-110">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="17149-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="17149-111">Windows 10</span></span>

1. <span data-ttu-id="17149-112">Selecione **iniciar** ![tecla do logotipo do Windows no teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="17149-112">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="17149-113">e role até a letra **V**.</span><span class="sxs-lookup"><span data-stu-id="17149-113">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="17149-114">Expanda a pasta do **Visual Studio 2019** .</span><span class="sxs-lookup"><span data-stu-id="17149-114">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="17149-115">Escolha **prompt de comando do desenvolvedor para VS 2019** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="17149-115">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="17149-116">Como alternativa, você pode começar a digitar o nome do prompt de comando na caixa de pesquisa na barra de tarefas e escolher o resultado desejado, pois a lista de resultados começa a exibir as correspondências de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="17149-116">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![GIF animado mostrando o comportamento de pesquisa no Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="17149-118">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="17149-118">Windows 8.1</span></span>

1. <span data-ttu-id="17149-119">Vá para a tela **Inicial** pressionando a tecla do logotipo do Windows ![tecla do logotipo do Windows no teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="17149-119">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="17149-120">no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="17149-120">on your keyboard for example.</span></span>

1. <span data-ttu-id="17149-121">Na tela **Iniciar** , pressione **Ctrl**+**Tab** para abrir a lista de **aplicativos** e, em seguida, pressione **V**. Isso abre uma lista que inclui todos os prompts de comando instalados do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17149-121">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="17149-122">Escolha **prompt de comando do desenvolvedor para VS 2019** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="17149-122">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="17149-123">Windows 7</span><span class="sxs-lookup"><span data-stu-id="17149-123">Windows 7</span></span>

1. <span data-ttu-id="17149-124">Escolha **Iniciar** e expanda **todos os programas**.</span><span class="sxs-lookup"><span data-stu-id="17149-124">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="17149-125">Escolha **Visual Studio 2019** > **Ferramentas do Visual Studio** > **prompt de comando do desenvolvedor para vs 2019**ou o prompt de comando que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="17149-125">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![Menu Iniciar do Windows 7 com o prompt de comando realçado](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="17149-127">Se você tiver outros SDKs instalados, como o [SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [versões anteriores](https://developer.microsoft.com/windows/downloads/sdk-archive), poderá ver prompts de comando adicionais.</span><span class="sxs-lookup"><span data-stu-id="17149-127">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="17149-128">Consulte a documentação das ferramentas individuais para determinar qual versão do prompt de comando você deve usar.</span><span class="sxs-lookup"><span data-stu-id="17149-128">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="17149-129">Localizar manualmente os arquivos em seu computador</span><span class="sxs-lookup"><span data-stu-id="17149-129">Manually locate the files on your machine</span></span>

<span data-ttu-id="17149-130">Normalmente, os atalhos para os prompts de comando que você instalou são colocados na pasta do **menu iniciar** do Visual Studio, como no *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Ferramentas do Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="17149-130">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="17149-131">Mas se, por algum motivo, pesquisar o prompt de comando não produzir os resultados esperados, você poderá tentar localizar manualmente o atalho em seu computador.</span><span class="sxs-lookup"><span data-stu-id="17149-131">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="17149-132">Tente pesquisar o nome do arquivo de prompt de comando, como *VsDevCmd. bat*, ou vá para a pasta ferramentas, como *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (o caminho muda de acordo com sua versão, edição e local de instalação do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="17149-132">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="17149-133">Iniciar o prompt de comando de dentro do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="17149-133">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="17149-134">Para facilitar o acesso, você pode adicionar Prompt de Comando do Desenvolvedor, ou qualquer outro prompt de comando, ao menu ferramentas no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17149-134">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="17149-135">Para disponibilizar a ferramenta, adicione-a à lista de ferramentas externas.</span><span class="sxs-lookup"><span data-stu-id="17149-135">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="17149-136">Aqui estão as etapas:</span><span class="sxs-lookup"><span data-stu-id="17149-136">Here are the steps:</span></span>

1. <span data-ttu-id="17149-137">{1&gt;Abra o Visual Studio.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="17149-137">Open Visual Studio.</span></span>

1. <span data-ttu-id="17149-138">Na janela de início, escolha **Continuar sem código**.</span><span class="sxs-lookup"><span data-stu-id="17149-138">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="17149-139">Na barra de menus, escolha **ferramentas** > **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="17149-139">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="17149-140">Na caixa de diálogo **Ferramentas Externas**, escolha o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="17149-140">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="17149-141">Uma nova entrada é exibida.</span><span class="sxs-lookup"><span data-stu-id="17149-141">A new entry appears.</span></span>

1. <span data-ttu-id="17149-142">Insira um **Título** para o novo item de menu, como `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="17149-142">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="17149-143">No campo **Comando**, especifique o arquivo que deseja iniciar, como `%comspec%` ou `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="17149-143">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="17149-144">No campo **argumentos** , especifique onde encontrar o prompt de comando específico que você deseja usar, como `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span><span class="sxs-lookup"><span data-stu-id="17149-144">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="17149-145">Esse comando inicia o Prompt de Comando do Desenvolvedor instalado com a Comunidade do Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="17149-145">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="17149-146">Altere este valor de acordo com a sua versão, edição e local de instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17149-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="17149-147">No campo **diretório inicial** , especifique o diretório no qual o prompt de comando será iniciado.</span><span class="sxs-lookup"><span data-stu-id="17149-147">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="17149-148">Escolha um valor, como **diretório do projeto** , selecionando a seta ao lado do campo.</span><span class="sxs-lookup"><span data-stu-id="17149-148">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="17149-149">Escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="17149-149">Choose the **OK** button.</span></span>

   ![Caixa de diálogo Ferramentas externas com os valores de campo preenchidos.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="17149-151">O novo item de menu é adicionado e você pode acessar o prompt de comando no menu ferramentas.</span><span class="sxs-lookup"><span data-stu-id="17149-151">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Item de menu do prompt de comando no Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="17149-153">Veja também</span><span class="sxs-lookup"><span data-stu-id="17149-153">See also</span></span>

- [<span data-ttu-id="17149-154">Ferramentas de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="17149-154">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="17149-155">Gerenciando ferramentas externas</span><span class="sxs-lookup"><span data-stu-id="17149-155">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="17149-156">Usar o conjunto C++ de ferramentas da Microsoft na linha de comando</span><span class="sxs-lookup"><span data-stu-id="17149-156">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
