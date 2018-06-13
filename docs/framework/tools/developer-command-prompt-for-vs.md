---
title: Prompt de Comando do Desenvolvedor para o Visual Studio
ms.date: 03/30/2017
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
ms.openlocfilehash: d3ff897e37e3fa2f7202a54c05c8093ba05282c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402022"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="286af-102">Prompt de Comando do Desenvolvedor para o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="286af-102">Developer Command Prompt for Visual Studio</span></span>
<span data-ttu-id="286af-103">O Prompt de Comando do Desenvolvedor do Visual Studio define automaticamente as variáveis de ambiente que permitem usar as ferramentas do .NET Framework com facilidade.</span><span class="sxs-lookup"><span data-stu-id="286af-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="286af-104">O Prompt de Comando do Desenvolvedor é instalado com as edições completa ou Community do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="286af-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="286af-105">Ele não é instalado com as versões Express do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="286af-105">It is not installed with the Express versions of Visual Studio.</span></span>  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="286af-106">Procurar o prompt de comando no computador</span><span class="sxs-lookup"><span data-stu-id="286af-106">Searching for the Command Prompt on your machine</span></span>  
 <span data-ttu-id="286af-107">Você pode consultar vários prompts de comando, dependendo da versão do Visual Studio e de todos os SDKs adicionais instalados.</span><span class="sxs-lookup"><span data-stu-id="286af-107">You may see multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="286af-108">Por exemplo, as versões 64 bits do Visual Studio oferecem prompts de comando 32 e 64 bits.</span><span class="sxs-lookup"><span data-stu-id="286af-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="286af-109">(As versões 32 e 64 bits da maioria das ferramentas são idênticas; porém, algumas ferramentas fazem alterações específicas em ambientes 32 e 64 bits.) Se estas etapas abaixo não funcionarem, tente [Localizar manualmente os arquivos em seu computador](#alternative) ou [Executar o prompt de comando de dentro do Visual Studio](#visualstudio).</span><span class="sxs-lookup"><span data-stu-id="286af-109">(The 32-bit and 64-bit versions of most tools are identical; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the steps below don't work, you can try [Manually locating the files on your machine](#alternative) or [Running command prompt from inside Visual Studio](#visualstudio).</span></span>  
  
 <span data-ttu-id="286af-110">**No Windows 10**</span><span class="sxs-lookup"><span data-stu-id="286af-110">**In Windows 10**</span></span>  
  
1.  <span data-ttu-id="286af-111">Abra o menu **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="286af-111">Open the **Start** menu, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="286af-112">No menu **Iniciar**, digite `dev`.</span><span class="sxs-lookup"><span data-stu-id="286af-112">On the **Start** menu, enter `dev`.</span></span> <span data-ttu-id="286af-113">Isso exibirá uma lista de aplicativos instalados que correspondem ao seu padrão de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="286af-113">This will bring a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="286af-114">Se você estiver procurando por um prompt de comando diferente, experimente digitar um termo de pesquisa diferente, como `prompt`.</span><span class="sxs-lookup"><span data-stu-id="286af-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>  
  
3.  <span data-ttu-id="286af-115">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="286af-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="286af-116">**No Windows 8.1**</span><span class="sxs-lookup"><span data-stu-id="286af-116">**In Windows 8.1**</span></span>  
  
1.  <span data-ttu-id="286af-117">Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="286af-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="286af-118">Na tela **Iniciar**, pressione `CTRL + TAB` para abrir a lista **Aplicativos** e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="286af-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="286af-119">Isso mostrará uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="286af-119">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
3.  <span data-ttu-id="286af-120">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="286af-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="286af-121">**No Windows 8**</span><span class="sxs-lookup"><span data-stu-id="286af-121">**In Windows 8**</span></span>  
  
1.  <span data-ttu-id="286af-122">Abra a tela **Iniciar** pressionando a tecla do logotipo do Windows ![Logotipo do Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") no seu teclado, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="286af-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="286af-123">Na tela **Iniciar**, pressione a tecla do logotipo do Windows ![Logotipo do Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="286af-123">On the **Start** screen, press the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>  
  
3.  <span data-ttu-id="286af-124">Escolha o ícone **Exibição de aplicativos** na parte inferior da tela e digite `V`.</span><span class="sxs-lookup"><span data-stu-id="286af-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="286af-125">Isso mostrará uma lista que inclui todos os prompts de comando do Visual Studio instalados.</span><span class="sxs-lookup"><span data-stu-id="286af-125">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
4.  <span data-ttu-id="286af-126">Escolha o **Prompt de Comando do Desenvolvedor** (ou o prompt de comando que você deseja usar).</span><span class="sxs-lookup"><span data-stu-id="286af-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="286af-127">**No Windows 7**</span><span class="sxs-lookup"><span data-stu-id="286af-127">**In Windows 7**</span></span>  
  
1.  <span data-ttu-id="286af-128">Escolha **Iniciar**, expanda **Todos os Programas** e expanda **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="286af-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="286af-129">Dependendo da versão do Visual Studio que você instalou, escolha **Ferramentas do Visual Studio**, **Prompt de Comando do Visual Studio** ou o prompt de comando que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="286af-129">Depending on the version of Visual Studio you have installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>  
  
 <span data-ttu-id="286af-130">Se você tiver o [SDK do Windows](http://msdn.microsoft.com/windows/desktop/aa904949) ou o [SDK do Windows Phone](https://dev.windowsphone.com/downloadsdk), você poderá ver prompts de comando adicionais para arquiteturas ARM, x86 ou x64.</span><span class="sxs-lookup"><span data-stu-id="286af-130">If you have the [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) or [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="286af-131">Consulte a documentação das ferramentas individuais para determinar qual versão do prompt de comando você deve usar.</span><span class="sxs-lookup"><span data-stu-id="286af-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="286af-132">Localizar manualmente os arquivos em seu computador</span><span class="sxs-lookup"><span data-stu-id="286af-132">Manually locating the files on your machine</span></span>  
  <span data-ttu-id="286af-133">Normalmente, os atalhos para os prompts de comando que você instalou serão colocados na pasta **Menu Iniciar** do Visual Studio, como em C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="286af-133">Usually, the shortcuts for the command prompts you have installed will be placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools.</span></span>    <span data-ttu-id="286af-134">Porém, se por algum motivo a pesquisa do prompt de comando não produzir os resultados esperados, você poderá tentar localizar manualmente o atalho em seu computador para usá-lo.</span><span class="sxs-lookup"><span data-stu-id="286af-134">But if for some reason, searching for the command prompt doesn't yield the expected results, you can try to manually locate the shortcut on your machine in order to use it.</span></span>   <span data-ttu-id="286af-135">Tente pesquisar pelo nome de arquivo do prompt de comando como VsDevCmd.bat ou acesse a pasta das Ferramentas como C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools (o caminho será alterado de acordo com seu local de instalação e da versão do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="286af-135">Try searching for the name of the command prompt file such as VsDevCmd.bat or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools (path will change according to your Visual Studio version and installation location).</span></span>  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="286af-136">Executar o prompt de comando de dentro do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="286af-136">Running command prompt from inside Visual Studio</span></span>  
 <span data-ttu-id="286af-137">Para facilitar o acesso, você pode adicionar o Prompt de Comando do Visual Studio Developer ou qualquer outro prompt de comando ao menu Ferramentas no Visual Studio, adicionando-o à lista de ferramentas externas.</span><span class="sxs-lookup"><span data-stu-id="286af-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="286af-138">Faça isso da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="286af-138">This is how you can accomplish that:</span></span>  
  
1.  <span data-ttu-id="286af-139">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="286af-139">Open Visual Studio.</span></span>  
  
2.  <span data-ttu-id="286af-140">Selecione o menu **Ferramentas** e escolha **Ferramentas Externas...**.</span><span class="sxs-lookup"><span data-stu-id="286af-140">Select the **Tools** menu and choose **External Tools...**.</span></span>  
  
3.  <span data-ttu-id="286af-141">Na caixa de diálogo **Ferramentas Externas**, escolha o botão **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="286af-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="286af-142">Uma nova entrada será exibida</span><span class="sxs-lookup"><span data-stu-id="286af-142">A new entry appears</span></span>  
  
4.  <span data-ttu-id="286af-143">Insira um **Título** para o novo item de menu, como `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="286af-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>  
  
5.  <span data-ttu-id="286af-144">No campo **Comando**, especifique o arquivo que você deseja iniciar, como `%comspec%` ou `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="286af-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe` .</span></span>  
  
6.  <span data-ttu-id="286af-145">No campo **Argumentos**, especifique onde encontrar o prompt de comando específico que você deseja usar, como `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (isso iniciar o Prompt de Comando do Desenvolvedor instalado com [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="286af-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (this will launch the Developer Command Prompt installed with [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span></span> <span data-ttu-id="286af-146">Esse valor precisa ser alterado de acordo com seu local de instalação e da versão do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="286af-146">This value needs to be changed according to your Visual Studio version and installation location.</span></span>  
  
7.  <span data-ttu-id="286af-147">Escolha um valor para o campo **Diretório inicial**, como **Diretório do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="286af-147">Choose a value for the **Initial directory** field such as **Project Directory** .</span></span>  
  
8.  <span data-ttu-id="286af-148">Escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="286af-148">Choose the **OK** button.</span></span>  
  
 <span data-ttu-id="286af-149">Depois disso, o novo item de menu será adicionado e você poderá acessar o prompt de comando no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="286af-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286af-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="286af-150">See Also</span></span>  
 [<span data-ttu-id="286af-151">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="286af-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="286af-152">Gerenciando ferramentas externas</span><span class="sxs-lookup"><span data-stu-id="286af-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
