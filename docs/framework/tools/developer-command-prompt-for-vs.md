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
ms.openlocfilehash: 79cfc607e20d921c7ae942cb9755eee4264336eb
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877051"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="13ccb-102">Prompt de Comando do Desenvolvedor para o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="13ccb-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="13ccb-103">O Prompt de Comando do Desenvolvedor para Visual Studio permite que você use ferramentas do .NET Framework com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="13ccb-103">The Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="13ccb-104">Trata-se de um prompt de comando que define variáveis de ambiente específicas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="13ccb-104">It is a command prompt that automatically sets specific environment variables.</span></span>

> [!div class="button"]
> [<span data-ttu-id="13ccb-105">Baixar o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="13ccb-105">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="13ccb-106">Pesquisar pelo prompt de comando em seu computador</span><span class="sxs-lookup"><span data-stu-id="13ccb-106">Search for the command prompt on your machine</span></span>

<span data-ttu-id="13ccb-107">É possível que haja vários prompts de comando, dependendo da versão do Visual Studio e de todos os SDKs adicionais instalados.</span><span class="sxs-lookup"><span data-stu-id="13ccb-107">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="13ccb-108">Por exemplo, as versões 64 bits do Visual Studio oferecem prompts de comando 32 e 64 bits.</span><span class="sxs-lookup"><span data-stu-id="13ccb-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="13ccb-109">(As versões 32 e 64 bits da maioria das ferramentas são iguais; porém, algumas ferramentas fazem alterações específicas em ambientes 32 e 64 bits.) Se as etapas a seguir não funcionarem, você poderá tentar [Localizar manualmente os arquivos em seu computador](#manually-locate-the-files-on-your-machine) ou [Executar o prompt de comando de dentro do Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="13ccb-109">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [Run the command prompt from inside Visual Studio](#run-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="13ccb-110">No Windows 10</span><span class="sxs-lookup"><span data-stu-id="13ccb-110">In Windows 10</span></span>

1. <span data-ttu-id="13ccb-111">Na caixa de pesquisa na barra de tarefas, comece a digitar o nome da ferramenta, como `dev` ou `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="13ccb-111">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="13ccb-112">Isso abre uma lista de aplicativos instalados que correspondem ao seu padrão de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="13ccb-112">This brings up a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="13ccb-113">Se você estiver procurando por um prompt de comando diferente, experimente digitar um termo de pesquisa diferente, como `prompt`.</span><span class="sxs-lookup"><span data-stu-id="13ccb-113">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="13ccb-114">Escolha o **Prompt de Comando do Desenvolvedor para Visual Studio** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="13ccb-114">Choose the **Developer Command Prompt for Visual Studio** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="13ccb-115">No Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="13ccb-115">In Windows 8.1</span></span>

1. <span data-ttu-id="13ccb-116">Vá para a tela **Inicial** pressionando a tecla do logotipo do Windows ![tecla do logotipo do Windows no teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="13ccb-116">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="13ccb-117">no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="13ccb-117">on your keyboard for example.</span></span>

2. <span data-ttu-id="13ccb-118">Na tela **Iniciar**, pressione **Ctrl**+**Tab** para abrir a lista **Aplicativos** e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="13ccb-118">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then enter `V`.</span></span> <span data-ttu-id="13ccb-119">Isso mostra uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="13ccb-119">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="13ccb-120">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="13ccb-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="13ccb-121">No Windows 8</span><span class="sxs-lookup"><span data-stu-id="13ccb-121">In Windows 8</span></span>

1. <span data-ttu-id="13ccb-122">Vá para a tela **Inicial** pressionando a tecla do logotipo do Windows ![tecla do logotipo do Windows no teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="13ccb-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="13ccb-123">no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="13ccb-123">on your keyboard for example.</span></span>

2. <span data-ttu-id="13ccb-124">Na tela **Iniciar**, pressione a tecla do logotipo do Windows ![tecla do logotipo do Windows no teclado.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="13ccb-124">On the **Start** screen, press the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="13ccb-125">`+ Z`.</span><span class="sxs-lookup"><span data-stu-id="13ccb-125">`+ Z`.</span></span>

3. <span data-ttu-id="13ccb-126">Escolha o ícone **Exibição de aplicativos** na parte inferior da tela e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="13ccb-126">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="13ccb-127">Isso mostra uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="13ccb-127">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="13ccb-128">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="13ccb-128">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="13ccb-129">No Windows 7</span><span class="sxs-lookup"><span data-stu-id="13ccb-129">In Windows 7</span></span>

1. <span data-ttu-id="13ccb-130">Escolha **Iniciar**, expanda **Todos os Programas** e expanda **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="13ccb-130">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="13ccb-131">Dependendo da versão do Visual Studio que você instalou, escolha **Ferramentas do Visual Studio**, **Prompt de Comando do Visual Studio** ou o prompt de comando que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="13ccb-131">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="13ccb-132">Se houver outros SDKs instalados, como o [SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [versões anteriores](https://developer.microsoft.com/windows/downloads/sdk-archive), poderão ser exibidos outros prompts de comando, para as arquiteturas ARM, x86 ou x64.</span><span class="sxs-lookup"><span data-stu-id="13ccb-132">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="13ccb-133">Consulte a documentação das ferramentas individuais para determinar qual versão do prompt de comando você deve usar.</span><span class="sxs-lookup"><span data-stu-id="13ccb-133">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="13ccb-134">Localizar manualmente os arquivos em seu computador</span><span class="sxs-lookup"><span data-stu-id="13ccb-134">Manually locate the files on your machine</span></span>

<span data-ttu-id="13ccb-135">Normalmente, os atalhos para os prompts de comando que você instalou serão colocados na pasta **Menu Iniciar** do Visual Studio, como em C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="13ccb-135">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="13ccb-136">Porém, se por algum motivo a pesquisa do prompt de comando não gerar os resultados esperados, você poderá tentar localizar manualmente o atalho em seu computador.</span><span class="sxs-lookup"><span data-stu-id="13ccb-136">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="13ccb-137">Tente pesquisar pelo nome do arquivo do prompt de comando, como *VsDevCmd.bat* ou acesse a pasta Tools, como C:\Arquivos de Programas (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (o caminho mudará conforme seu local de instalação, edição e versão do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="13ccb-137">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="run-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="13ccb-138">Executar o prompt de comando de dentro do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="13ccb-138">Run the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="13ccb-139">Para facilitar o acesso, você pode adicionar o Prompt de Comando do Desenvolvedor do Visual Studio ou qualquer outro prompt de comando ao menu **Ferramentas** do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13ccb-139">For easier access, you can add the Visual Studio Developer Command Prompt, or any other command prompt, to the **Tools** menu in Visual Studio.</span></span> <span data-ttu-id="13ccb-140">Para disponibilizar a ferramenta, adicione-a à lista de ferramentas externas.</span><span class="sxs-lookup"><span data-stu-id="13ccb-140">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="13ccb-141">Aqui estão as etapas:</span><span class="sxs-lookup"><span data-stu-id="13ccb-141">Here are the steps:</span></span>

1. <span data-ttu-id="13ccb-142">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13ccb-142">Open Visual Studio.</span></span>

2. <span data-ttu-id="13ccb-143">Selecione o menu **Ferramentas** e, em seguida, escolha **Ferramentas Externas**.</span><span class="sxs-lookup"><span data-stu-id="13ccb-143">Select the **Tools** menu, and then choose **External Tools**.</span></span>

3. <span data-ttu-id="13ccb-144">Na caixa de diálogo **Ferramentas Externas**, escolha o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="13ccb-144">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="13ccb-145">Uma nova entrada é exibida.</span><span class="sxs-lookup"><span data-stu-id="13ccb-145">A new entry appears.</span></span>

4. <span data-ttu-id="13ccb-146">Insira um **Título** para o novo item de menu, como `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="13ccb-146">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="13ccb-147">No campo **Comando**, especifique o arquivo que deseja iniciar, como `%comspec%` ou `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="13ccb-147">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="13ccb-148">No campo **Argumentos**, especifique em que ponto encontrar o prompt de comando específico que você deseja usar como `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (esse comando inicializa o Prompt de Comando do Desenvolvedor que é instalado com o Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="13ccb-148">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="13ccb-149">Altere este valor de acordo com a sua versão, edição e local de instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13ccb-149">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="13ccb-150">Escolha um valor para o campo **Diretório inicial**, como **Diretório do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="13ccb-150">Choose a value for the **Initial directory** field, such as **Project Directory**.</span></span>

8. <span data-ttu-id="13ccb-151">Escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="13ccb-151">Choose the **OK** button.</span></span>

   <span data-ttu-id="13ccb-152">O novo item de menu foi adicionado e você pode acessar o prompt de comando no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="13ccb-152">The new menu item is added, and you can access the command prompt from the **Tools** menu.</span></span>

   ![Item de menu do prompt de comando no Visual Studio](media/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="13ccb-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13ccb-154">See also</span></span>

- [<span data-ttu-id="13ccb-155">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="13ccb-155">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="13ccb-156">Gerenciando ferramentas externas</span><span class="sxs-lookup"><span data-stu-id="13ccb-156">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
