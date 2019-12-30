---
title: Instalar arquivos do IntelliSense localizado
description: Saiba como configurar seu computador de desenvolvimento para usar arquivos do IntelliSense localizado para projetos do .NET Core no Visual Studio.
author: mairaw
ms.author: mairaw
ms.date: 12/18/2019
ms.openlocfilehash: 98d75544ab853e75c175dd2919991b250cfaa3b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443473"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="5fb18-103">Como instalar arquivos do IntelliSense localizado para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="5fb18-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="5fb18-104">O [IntelliSense](/visualstudio/ide/using-intellisense) é um recurso de conclusão de código disponível em IDEs (ambientes de desenvolvimento integrado) diferentes, como o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5fb18-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="5fb18-105">Por padrão, quando você está desenvolvendo projetos do .NET Core, o SDK inclui apenas a versão em inglês dos arquivos do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5fb18-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="5fb18-106">Este artigo explica:</span><span class="sxs-lookup"><span data-stu-id="5fb18-106">This article explains:</span></span>

- <span data-ttu-id="5fb18-107">Como instalar a versão localizada desses arquivos.</span><span class="sxs-lookup"><span data-stu-id="5fb18-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="5fb18-108">Como modificar a instalação do Visual Studio para usar uma linguagem diferente.</span><span class="sxs-lookup"><span data-stu-id="5fb18-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5fb18-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5fb18-109">Prerequisites</span></span>

- <span data-ttu-id="5fb18-110">[SDK do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="5fb18-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="5fb18-111">[Visual Studio 2019 versão 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="5fb18-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="5fb18-112">Baixar e instalar os arquivos do IntelliSense localizado</span><span class="sxs-lookup"><span data-stu-id="5fb18-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fb18-113">Este procedimento requer que você tenha permissão de administrador para copiar os arquivos do IntelliSense para a pasta de instalação do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5fb18-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="5fb18-114">Acesse a página [Baixar arquivos do IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense).</span><span class="sxs-lookup"><span data-stu-id="5fb18-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="5fb18-115">Baixe o arquivo do IntelliSense para a linguagem e a versão que você gostaria de usar.</span><span class="sxs-lookup"><span data-stu-id="5fb18-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="5fb18-116">Extraia o conteúdo do arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="5fb18-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="5fb18-117">Navegue até a pasta de instalação do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5fb18-117">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="5fb18-118">Por padrão, ela está em *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="5fb18-118">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>

   - <span data-ttu-id="5fb18-119">Escolha o SDK para o qual você deseja instalar o IntelliSense e navegue até o caminho associado.</span><span class="sxs-lookup"><span data-stu-id="5fb18-119">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="5fb18-120">Você tem as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="5fb18-120">You have the following options:</span></span>

      | <span data-ttu-id="5fb18-121">Tipo de SDK</span><span class="sxs-lookup"><span data-stu-id="5fb18-121">SDK type</span></span>        | <span data-ttu-id="5fb18-122">Caminho</span><span class="sxs-lookup"><span data-stu-id="5fb18-122">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="5fb18-123">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5fb18-123">.NET Core</span></span>       | <span data-ttu-id="5fb18-124">*Microsoft.NETCore.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="5fb18-124">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="5fb18-125">Área de Trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="5fb18-125">Windows Desktop</span></span> | <span data-ttu-id="5fb18-126">*Microsoft.WindowsDesktop.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="5fb18-126">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="5fb18-127">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="5fb18-127">.NET Standard</span></span>   | <span data-ttu-id="5fb18-128">*NETStandard.Library.Ref*</span><span class="sxs-lookup"><span data-stu-id="5fb18-128">*NETStandard.Library.Ref*</span></span>          |
   
   - <span data-ttu-id="5fb18-129">Navegue até a versão para a qual você deseja instalar o IntelliSense localizado.</span><span class="sxs-lookup"><span data-stu-id="5fb18-129">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="5fb18-130">Por exemplo, *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="5fb18-130">For example, *3.1.0*.</span></span>
   - <span data-ttu-id="5fb18-131">Abra a pasta *ref*.</span><span class="sxs-lookup"><span data-stu-id="5fb18-131">Open the *ref* folder.</span></span>
   - <span data-ttu-id="5fb18-132">Abra a pasta moniker.</span><span class="sxs-lookup"><span data-stu-id="5fb18-132">Open the moniker folder.</span></span> <span data-ttu-id="5fb18-133">Por exemplo, *netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="5fb18-133">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="5fb18-134">Portanto, o caminho completo para o qual você navegaria seria semelhante a *C:\Arquivos de Programas\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="5fb18-134">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="5fb18-135">Crie uma subpasta dentro da pasta moniker que você acabou de abrir.</span><span class="sxs-lookup"><span data-stu-id="5fb18-135">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="5fb18-136">O nome da pasta indica qual linguagem você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="5fb18-136">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="5fb18-137">A tabela a seguir especifica as diferentes opções:</span><span class="sxs-lookup"><span data-stu-id="5fb18-137">The following table specifies the different options:</span></span>

   | <span data-ttu-id="5fb18-138">Idioma</span><span class="sxs-lookup"><span data-stu-id="5fb18-138">Language</span></span>              | <span data-ttu-id="5fb18-139">Nome da pasta</span><span class="sxs-lookup"><span data-stu-id="5fb18-139">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="5fb18-140">Português do Brasil</span><span class="sxs-lookup"><span data-stu-id="5fb18-140">Brazilian Portuguese</span></span>  | <span data-ttu-id="5fb18-141">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="5fb18-141">*pt-br*</span></span>     |
   | <span data-ttu-id="5fb18-142">Chinês (simplificado)</span><span class="sxs-lookup"><span data-stu-id="5fb18-142">Chinese (simplified)</span></span>  | <span data-ttu-id="5fb18-143">*zh-hans*</span><span class="sxs-lookup"><span data-stu-id="5fb18-143">*zh-hans*</span></span>   |
   | <span data-ttu-id="5fb18-144">Chinês (tradicional)</span><span class="sxs-lookup"><span data-stu-id="5fb18-144">Chinese (traditional)</span></span> | <span data-ttu-id="5fb18-145">*zh-hant*</span><span class="sxs-lookup"><span data-stu-id="5fb18-145">*zh-hant*</span></span>   |
   | <span data-ttu-id="5fb18-146">Francês</span><span class="sxs-lookup"><span data-stu-id="5fb18-146">French</span></span>                | <span data-ttu-id="5fb18-147">*fr*</span><span class="sxs-lookup"><span data-stu-id="5fb18-147">*fr*</span></span>        |
   | <span data-ttu-id="5fb18-148">Alemão</span><span class="sxs-lookup"><span data-stu-id="5fb18-148">German</span></span>                | <span data-ttu-id="5fb18-149">*de*</span><span class="sxs-lookup"><span data-stu-id="5fb18-149">*de*</span></span>        |
   | <span data-ttu-id="5fb18-150">Italiano</span><span class="sxs-lookup"><span data-stu-id="5fb18-150">Italian</span></span>               | <span data-ttu-id="5fb18-151">*it*</span><span class="sxs-lookup"><span data-stu-id="5fb18-151">*it*</span></span>        |
   | <span data-ttu-id="5fb18-152">Japonês</span><span class="sxs-lookup"><span data-stu-id="5fb18-152">Japanese</span></span>              | <span data-ttu-id="5fb18-153">*ja*</span><span class="sxs-lookup"><span data-stu-id="5fb18-153">*ja*</span></span>        |
   | <span data-ttu-id="5fb18-154">Coreano</span><span class="sxs-lookup"><span data-stu-id="5fb18-154">Korean</span></span>                | <span data-ttu-id="5fb18-155">*ko*</span><span class="sxs-lookup"><span data-stu-id="5fb18-155">*ko*</span></span>        |
   | <span data-ttu-id="5fb18-156">Russo</span><span class="sxs-lookup"><span data-stu-id="5fb18-156">Russian</span></span>               | <span data-ttu-id="5fb18-157">*ru*</span><span class="sxs-lookup"><span data-stu-id="5fb18-157">*ru*</span></span>        |
   | <span data-ttu-id="5fb18-158">Espanhol</span><span class="sxs-lookup"><span data-stu-id="5fb18-158">Spanish</span></span>               | <span data-ttu-id="5fb18-159">*es*</span><span class="sxs-lookup"><span data-stu-id="5fb18-159">*es*</span></span>        |

1. <span data-ttu-id="5fb18-160">Copie os arquivos *.xml* que você extraiu na etapa 3 para essa nova pasta.</span><span class="sxs-lookup"><span data-stu-id="5fb18-160">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="5fb18-161">Os arquivos *.xml* são divididos por pastas do SDK. Portanto, copie-os para o SDK correspondente que você escolheu na etapa 4.</span><span class="sxs-lookup"><span data-stu-id="5fb18-161">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="5fb18-162">Modificar o idioma do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5fb18-162">Modify Visual Studio language</span></span>

<span data-ttu-id="5fb18-163">Para que o Visual Studio use um idioma diferente para o IntelliSense, instale o pacote de idiomas apropriado.</span><span class="sxs-lookup"><span data-stu-id="5fb18-163">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="5fb18-164">Isso pode ser feito [durante a instalação](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) ou em um momento posterior, modificando a instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5fb18-164">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="5fb18-165">Se você já tiver o Visual Studio configurado para o idioma de sua escolha, a instalação do IntelliSense estará pronta.</span><span class="sxs-lookup"><span data-stu-id="5fb18-165">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="5fb18-166">Instalar o pacote de idiomas</span><span class="sxs-lookup"><span data-stu-id="5fb18-166">Install the language pack</span></span>

<span data-ttu-id="5fb18-167">Se você não instalou o pacote de idiomas desejado durante a instalação, atualize o Visual Studio da seguinte maneira para instalar o pacote de idiomas:</span><span class="sxs-lookup"><span data-stu-id="5fb18-167">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fb18-168">Para instalar, atualizar ou modificar o Visual Studio, faça logon com uma conta que tenha permissões administrativas.</span><span class="sxs-lookup"><span data-stu-id="5fb18-168">To install, update, or modify Visual Studio, you must log on with an account that has administrative permissions.</span></span> <span data-ttu-id="5fb18-169">Para saber mais, confira [Permissões de usuário e Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5fb18-169">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="5fb18-170">Localize o Instalador do Visual Studio no computador.</span><span class="sxs-lookup"><span data-stu-id="5fb18-170">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="5fb18-171">Por exemplo, em um computador que executa o Windows 10, selecione **Iniciar** e, em seguida, role até a letra **I**, onde ele está listado como **Instalador do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="5fb18-171">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Abra o Instalador do Visual Studio no Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="5fb18-173">Também é possível encontrar o Instalador do Visual Studio no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="5fb18-173">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="5fb18-174">Talvez você precise atualizar o instalador antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5fb18-174">You might have to update the installer before continuing.</span></span> <span data-ttu-id="5fb18-175">Nesse caso, siga os prompts.</span><span class="sxs-lookup"><span data-stu-id="5fb18-175">If so, follow the prompts.</span></span>

1. <span data-ttu-id="5fb18-176">No instalador, procure a edição do Visual Studio à qual você deseja adicionar o pacote de idiomas e escolha **Modificar**.</span><span class="sxs-lookup"><span data-stu-id="5fb18-176">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Atualizar ou modificar o Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="5fb18-178">Se você não vir um botão **Modificar**, mas vir um **Atualizar**, será necessário atualizar seu Visual Studio antes de poder modificar sua instalação.</span><span class="sxs-lookup"><span data-stu-id="5fb18-178">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="5fb18-179">Depois que a atualização for concluída, o botão **Modificar** deverá ser exibido.</span><span class="sxs-lookup"><span data-stu-id="5fb18-179">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="5fb18-180">Na guia **Pacotes de idiomas**, selecione ou cancele a seleção dos idiomas que você deseja instalar ou desinstalar.</span><span class="sxs-lookup"><span data-stu-id="5fb18-180">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Guia de pacotes de idiomas do Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="5fb18-182">Escolha **Modificar**.</span><span class="sxs-lookup"><span data-stu-id="5fb18-182">Choose **Modify**.</span></span> <span data-ttu-id="5fb18-183">A atualização será iniciada.</span><span class="sxs-lookup"><span data-stu-id="5fb18-183">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="5fb18-184">Modificar as configurações de idioma no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5fb18-184">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="5fb18-185">Depois de instalar os pacotes de idiomas desejados, modifique suas configurações do Visual Studio para usar um idioma diferente:</span><span class="sxs-lookup"><span data-stu-id="5fb18-185">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="5fb18-186">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5fb18-186">Open Visual Studio.</span></span>

1. <span data-ttu-id="5fb18-187">Na janela de início, escolha **Continuar sem código**.</span><span class="sxs-lookup"><span data-stu-id="5fb18-187">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="5fb18-188">No menu principal, selecione **Ferramentas** > **Opções**.</span><span class="sxs-lookup"><span data-stu-id="5fb18-188">On the main menu, select **Tools** > **Options**.</span></span> <span data-ttu-id="5fb18-189">A caixa de diálogo Opções é aberta.</span><span class="sxs-lookup"><span data-stu-id="5fb18-189">The Options dialog opens.</span></span>

1. <span data-ttu-id="5fb18-190">Na pasta **Ambiente**, escolha **Configurações Internacionais**.</span><span class="sxs-lookup"><span data-stu-id="5fb18-190">Under the **Environment** folder, choose **International Settings**.</span></span>

1. <span data-ttu-id="5fb18-191">No menu suspenso **Idioma**, selecione o idioma desejado.</span><span class="sxs-lookup"><span data-stu-id="5fb18-191">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="5fb18-192">Escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fb18-192">Choose **OK**.</span></span> 

1. <span data-ttu-id="5fb18-193">Uma caixa de diálogo informa que você precisa reiniciar o Visual Studio para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="5fb18-193">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="5fb18-194">Escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fb18-194">Choose **OK**.</span></span>

1. <span data-ttu-id="5fb18-195">Reinicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5fb18-195">Restart Visual Studio.</span></span>

<span data-ttu-id="5fb18-196">Depois disso, seu IntelliSense deverá funcionar conforme o esperado quando você abrir um projeto do .NET Core que direciona a versão dos arquivos do IntelliSense que você acabou de instalar.</span><span class="sxs-lookup"><span data-stu-id="5fb18-196">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fb18-197">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fb18-197">See also</span></span>

- [<span data-ttu-id="5fb18-198">IntelliSense no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5fb18-198">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
