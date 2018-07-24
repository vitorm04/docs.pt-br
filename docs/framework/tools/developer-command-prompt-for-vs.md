---
title: Prompt de Comando do Desenvolvedor para o Visual Studio
ms.date: 06/18/2018
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
ms.openlocfilehash: 8e64facffd4face929b28d660ffd5210f127c3bd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315219"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="cf984-102">Prompt de Comando do Desenvolvedor para o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cf984-102">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="cf984-103">O Prompt de Comando do Desenvolvedor do Visual Studio define automaticamente as variáveis de ambiente que permitem usar as ferramentas do .NET Framework com facilidade.</span><span class="sxs-lookup"><span data-stu-id="cf984-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="cf984-104">O Prompt de Comando do Desenvolvedor é instalado com as edições completa ou Community do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf984-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="cf984-105">Ele não é instalado com as versões Express do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf984-105">It isn't installed with the Express versions of Visual Studio.</span></span>

> [!div class="button"]
[<span data-ttu-id="cf984-106">Baixar o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cf984-106">Download Visual Studio</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="cf984-107">Procurar o prompt de comando no computador</span><span class="sxs-lookup"><span data-stu-id="cf984-107">Searching for the Command Prompt on your machine</span></span>

<span data-ttu-id="cf984-108">Você pode ver vários prompts de comando, dependendo da versão do Visual Studio e dos SDKs adicionais instalados.</span><span class="sxs-lookup"><span data-stu-id="cf984-108">You may see many command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="cf984-109">Por exemplo, as versões 64 bits do Visual Studio oferecem prompts de comando 32 e 64 bits.</span><span class="sxs-lookup"><span data-stu-id="cf984-109">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="cf984-110">(As versões de 32 e 64 bits da maioria das ferramentas são iguais; porém, algumas ferramentas fazem alterações específicas em ambientes de 32 e 64 bits.) Se as etapas abaixo não funcionarem, você poderá tentar [Localizar manualmente os arquivos em seu computador](#manually-locating-the-files-on-your-machine) ou [Executar o prompt de comando de dentro do Visual Studio](#running-command-prompt-from-inside-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="cf984-110">(The 32-bit and 64-bit versions of most tools are the same; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the following steps don't work, you can try [Manually locating the files on your machine](#manually-locating-the-files-on-your-machine) or [Running command prompt from inside Visual Studio](#running-command-prompt-from-inside-visual-studio).</span></span>

### <a name="in-windows-10"></a><span data-ttu-id="cf984-111">No Windows 10</span><span class="sxs-lookup"><span data-stu-id="cf984-111">In Windows 10</span></span>

1. <span data-ttu-id="cf984-112">Na caixa de pesquisa da barra de tarefas, comece a digitar o nome da ferramenta, por exemplo, `dev` ou `developer command prompt`.</span><span class="sxs-lookup"><span data-stu-id="cf984-112">In the search box on the taskbar, start typing the name of the tool, such as `dev` or `developer command prompt`.</span></span> <span data-ttu-id="cf984-113">Será exibida uma lista dos aplicativos instalados que correspondem ao padrão de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="cf984-113">This brings a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="cf984-114">Se você estiver procurando por um prompt de comando diferente, experimente digitar um termo de pesquisa diferente, como `prompt`.</span><span class="sxs-lookup"><span data-stu-id="cf984-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>

2. <span data-ttu-id="cf984-115">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="cf984-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-81"></a><span data-ttu-id="cf984-116">No Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="cf984-116">In Windows 8.1</span></span>

1. <span data-ttu-id="cf984-117">Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="cf984-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="cf984-118">Na tela **Iniciar**, pressione `CTRL + TAB` para abrir a lista **Aplicativos** e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="cf984-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="cf984-119">Isso mostra uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="cf984-119">This brings a list that includes all installed Visual Studio command prompts.</span></span>

3. <span data-ttu-id="cf984-120">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="cf984-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-8"></a><span data-ttu-id="cf984-121">No Windows 8</span><span class="sxs-lookup"><span data-stu-id="cf984-121">In Windows 8</span></span>

1. <span data-ttu-id="cf984-122">Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="cf984-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>

2. <span data-ttu-id="cf984-123">Na tela **Iniciar**, pressione a tecla do logotipo do Windows ![Logotipo do Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="cf984-123">On the **Start** screen, press the Windows logo key ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>

3. <span data-ttu-id="cf984-124">Escolha o ícone **Exibição de aplicativos** na parte inferior da tela e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="cf984-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="cf984-125">Isso mostra uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="cf984-125">This brings a list that includes all installed Visual Studio command prompts.</span></span>

4. <span data-ttu-id="cf984-126">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="cf984-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>

### <a name="in-windows-7"></a><span data-ttu-id="cf984-127">No Windows 7</span><span class="sxs-lookup"><span data-stu-id="cf984-127">In Windows 7</span></span>

1. <span data-ttu-id="cf984-128">Escolha **Iniciar**, expanda **Todos os Programas** e expanda **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="cf984-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>

2. <span data-ttu-id="cf984-129">Dependendo da versão do Visual Studio que você instalou, escolha **Ferramentas do Visual Studio**, **Prompt de Comando do Visual Studio** ou o prompt de comando que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="cf984-129">Depending on the version of Visual Studio you've installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>

<span data-ttu-id="cf984-130">Se você tiver outros SDKs instalados, como o [SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ou [versões anteriores](https://developer.microsoft.com/windows/downloads/sdk-archive), poderá ver prompts de comando adicionais para arquiteturas ARM, x86 ou x64.</span><span class="sxs-lookup"><span data-stu-id="cf984-130">If you have other SDKs installed such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="cf984-131">Consulte a documentação das ferramentas individuais para determinar qual versão do prompt de comando você deve usar.</span><span class="sxs-lookup"><span data-stu-id="cf984-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="cf984-132">Localizar manualmente os arquivos em seu computador</span><span class="sxs-lookup"><span data-stu-id="cf984-132">Manually locating the files on your machine</span></span>

<span data-ttu-id="cf984-133">Normalmente, os atalhos para os prompts de comando que você instalou são colocados na pasta **Menu Iniciar** do Visual Studio, como em C:\ProgramData\Microsoft\Windows\MenuIniciar\Programas\Visual Studio 2017\Visual Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="cf984-133">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools.</span></span> <span data-ttu-id="cf984-134">Porém, se por algum motivo a pesquisa do prompt de comando não gerar os resultados esperados, você poderá tentar localizar manualmente o atalho em seu computador.</span><span class="sxs-lookup"><span data-stu-id="cf984-134">But if for some reason, searching for the command prompt doesn't bring the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="cf984-135">Tente pesquisar pelo nome do arquivo do prompt de comando, como *VsDevCmd.bat* ou acesse a pasta Tools, como C:\Arquivos de Programas (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (o caminho mudará conforme seu local de instalação, edição e versão do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="cf984-135">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="cf984-136">Executar o prompt de comando de dentro do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cf984-136">Running command prompt from inside Visual Studio</span></span>

<span data-ttu-id="cf984-137">Para facilitar o acesso, você pode adicionar o Prompt de Comando do Visual Studio Developer ou qualquer outro prompt de comando ao menu Ferramentas no Visual Studio, adicionando-o à lista de ferramentas externas.</span><span class="sxs-lookup"><span data-stu-id="cf984-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="cf984-138">Faça isso da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="cf984-138">This is how you can accomplish that:</span></span>

1. <span data-ttu-id="cf984-139">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf984-139">Open Visual Studio.</span></span>

2. <span data-ttu-id="cf984-140">Selecione o menu **Ferramentas** e escolha **Ferramentas Externas**.</span><span class="sxs-lookup"><span data-stu-id="cf984-140">Select the **Tools** menu and choose **External Tools**.</span></span>

3. <span data-ttu-id="cf984-141">Na caixa de diálogo **Ferramentas Externas**, escolha o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="cf984-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="cf984-142">Uma nova entrada é exibida.</span><span class="sxs-lookup"><span data-stu-id="cf984-142">A new entry appears.</span></span>

4. <span data-ttu-id="cf984-143">Insira um **Título** para o novo item de menu, como `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="cf984-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

5. <span data-ttu-id="cf984-144">No campo **Comando**, especifique o arquivo que você deseja iniciar, como `%comspec%` ou `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="cf984-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

6. <span data-ttu-id="cf984-145">No campo **Argumentos**, especifique em que ponto encontrar o prompt de comando específico que você deseja usar como `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (esse comando inicializa o Prompt de Comando do Desenvolvedor que é instalado com o Visual Studio 2017 Enterprise).</span><span class="sxs-lookup"><span data-stu-id="cf984-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (this command launches the Developer Command Prompt that is installed with Visual Studio 2017 Enterprise).</span></span> <span data-ttu-id="cf984-146">Altere este valor de acordo com a sua versão, edição e local de instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf984-146">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

7. <span data-ttu-id="cf984-147">Escolha um valor para o campo **Diretório inicial**, como **Diretório do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="cf984-147">Choose a value for the **Initial directory** field such as **Project Directory**.</span></span>

8. <span data-ttu-id="cf984-148">Escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf984-148">Choose the **OK** button.</span></span>

<span data-ttu-id="cf984-149">Depois disso, o novo item de menu será adicionado e você poderá acessar o prompt de comando no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="cf984-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf984-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf984-150">See also</span></span>

 [<span data-ttu-id="cf984-151">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="cf984-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="cf984-152">Gerenciando ferramentas externas</span><span class="sxs-lookup"><span data-stu-id="cf984-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)  
