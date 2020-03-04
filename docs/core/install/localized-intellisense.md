---
title: Instalar arquivos do IntelliSense localizado
description: Saiba como configurar seu computador de desenvolvimento para usar arquivos do IntelliSense localizado para projetos do .NET Core no Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157707"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="3740c-103">Como instalar arquivos do IntelliSense localizado para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="3740c-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="3740c-104">O [IntelliSense](/visualstudio/ide/using-intellisense) é um recurso de conclusão de código disponível em IDEs (ambientes de desenvolvimento integrado) diferentes, como o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3740c-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="3740c-105">Por padrão, quando você está desenvolvendo projetos do .NET Core, o SDK inclui apenas a versão em inglês dos arquivos do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3740c-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="3740c-106">Este artigo explica:</span><span class="sxs-lookup"><span data-stu-id="3740c-106">This article explains:</span></span>

- <span data-ttu-id="3740c-107">Como instalar a versão localizada desses arquivos.</span><span class="sxs-lookup"><span data-stu-id="3740c-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="3740c-108">Como modificar a instalação do Visual Studio para usar uma linguagem diferente.</span><span class="sxs-lookup"><span data-stu-id="3740c-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3740c-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3740c-109">Prerequisites</span></span>

- <span data-ttu-id="3740c-110">[SDK do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="3740c-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="3740c-111">[Visual Studio 2019 versão 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="3740c-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="3740c-112">Baixar e instalar os arquivos do IntelliSense localizado</span><span class="sxs-lookup"><span data-stu-id="3740c-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3740c-113">Este procedimento requer que você tenha permissão de administrador para copiar os arquivos do IntelliSense para a pasta de instalação do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3740c-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="3740c-114">Acesse a página [Baixar arquivos do IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense).</span><span class="sxs-lookup"><span data-stu-id="3740c-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="3740c-115">Baixe o arquivo do IntelliSense para a linguagem e a versão que você gostaria de usar.</span><span class="sxs-lookup"><span data-stu-id="3740c-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="3740c-116">Extraia o conteúdo do arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="3740c-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="3740c-117">Navegue até a pasta .NET Core IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3740c-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="3740c-118">Navegue até a pasta de instalação do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3740c-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="3740c-119">Por padrão, ela está em *%ProgramFiles%\dotnet\packs*.</span><span class="sxs-lookup"><span data-stu-id="3740c-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="3740c-120">Escolha o SDK para o qual você deseja instalar o IntelliSense e navegue até o caminho associado.</span><span class="sxs-lookup"><span data-stu-id="3740c-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="3740c-121">Você tem as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="3740c-121">You have the following options:</span></span>

      | <span data-ttu-id="3740c-122">Tipo de SDK</span><span class="sxs-lookup"><span data-stu-id="3740c-122">SDK type</span></span>        | <span data-ttu-id="3740c-123">Caminho</span><span class="sxs-lookup"><span data-stu-id="3740c-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="3740c-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="3740c-124">.NET Core</span></span>       | <span data-ttu-id="3740c-125">*Microsoft.NETCore.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="3740c-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="3740c-126">Área de Trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="3740c-126">Windows Desktop</span></span> | <span data-ttu-id="3740c-127">*Microsoft.WindowsDesktop.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="3740c-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="3740c-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="3740c-128">.NET Standard</span></span>   | <span data-ttu-id="3740c-129">*NETStandard.Library.Ref*</span><span class="sxs-lookup"><span data-stu-id="3740c-129">*NETStandard.Library.Ref*</span></span>          |

   1. <span data-ttu-id="3740c-130">Navegue até a versão para a qual você deseja instalar o IntelliSense localizado.</span><span class="sxs-lookup"><span data-stu-id="3740c-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="3740c-131">Por exemplo, *3.1.0*.</span><span class="sxs-lookup"><span data-stu-id="3740c-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="3740c-132">Abra a pasta *ref*.</span><span class="sxs-lookup"><span data-stu-id="3740c-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="3740c-133">Abra a pasta moniker.</span><span class="sxs-lookup"><span data-stu-id="3740c-133">Open the moniker folder.</span></span> <span data-ttu-id="3740c-134">Por exemplo, *netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="3740c-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="3740c-135">Portanto, o caminho completo para o qual você navegaria seria semelhante a *C:\Arquivos de Programas\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span><span class="sxs-lookup"><span data-stu-id="3740c-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="3740c-136">Crie uma subpasta dentro da pasta moniker que você acabou de abrir.</span><span class="sxs-lookup"><span data-stu-id="3740c-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="3740c-137">O nome da pasta indica qual linguagem você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="3740c-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="3740c-138">A tabela a seguir especifica as diferentes opções:</span><span class="sxs-lookup"><span data-stu-id="3740c-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="3740c-139">Linguagem</span><span class="sxs-lookup"><span data-stu-id="3740c-139">Language</span></span>              | <span data-ttu-id="3740c-140">Nome da pasta</span><span class="sxs-lookup"><span data-stu-id="3740c-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="3740c-141">Português (Brasil)</span><span class="sxs-lookup"><span data-stu-id="3740c-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="3740c-142">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="3740c-142">*pt-br*</span></span>     |
   | <span data-ttu-id="3740c-143">Chinês (simplificado)</span><span class="sxs-lookup"><span data-stu-id="3740c-143">Chinese (simplified)</span></span>  | <span data-ttu-id="3740c-144">*zh-hans*</span><span class="sxs-lookup"><span data-stu-id="3740c-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="3740c-145">Chinês (tradicional)</span><span class="sxs-lookup"><span data-stu-id="3740c-145">Chinese (traditional)</span></span> | <span data-ttu-id="3740c-146">*zh-hant*</span><span class="sxs-lookup"><span data-stu-id="3740c-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="3740c-147">Francês</span><span class="sxs-lookup"><span data-stu-id="3740c-147">French</span></span>                | <span data-ttu-id="3740c-148">*fr*</span><span class="sxs-lookup"><span data-stu-id="3740c-148">*fr*</span></span>        |
   | <span data-ttu-id="3740c-149">Alemão</span><span class="sxs-lookup"><span data-stu-id="3740c-149">German</span></span>                | <span data-ttu-id="3740c-150">*de*</span><span class="sxs-lookup"><span data-stu-id="3740c-150">*de*</span></span>        |
   | <span data-ttu-id="3740c-151">Italiano</span><span class="sxs-lookup"><span data-stu-id="3740c-151">Italian</span></span>               | <span data-ttu-id="3740c-152">*it*</span><span class="sxs-lookup"><span data-stu-id="3740c-152">*it*</span></span>        |
   | <span data-ttu-id="3740c-153">Japonês</span><span class="sxs-lookup"><span data-stu-id="3740c-153">Japanese</span></span>              | <span data-ttu-id="3740c-154">*ja*</span><span class="sxs-lookup"><span data-stu-id="3740c-154">*ja*</span></span>        |
   | <span data-ttu-id="3740c-155">Coreano</span><span class="sxs-lookup"><span data-stu-id="3740c-155">Korean</span></span>                | <span data-ttu-id="3740c-156">*ko*</span><span class="sxs-lookup"><span data-stu-id="3740c-156">*ko*</span></span>        |
   | <span data-ttu-id="3740c-157">Russo</span><span class="sxs-lookup"><span data-stu-id="3740c-157">Russian</span></span>               | <span data-ttu-id="3740c-158">*ru*</span><span class="sxs-lookup"><span data-stu-id="3740c-158">*ru*</span></span>        |
   | <span data-ttu-id="3740c-159">Espanhol</span><span class="sxs-lookup"><span data-stu-id="3740c-159">Spanish</span></span>               | <span data-ttu-id="3740c-160">*es*</span><span class="sxs-lookup"><span data-stu-id="3740c-160">*es*</span></span>        |

1. <span data-ttu-id="3740c-161">Copie os arquivos *.xml* que você extraiu na etapa 3 para essa nova pasta.</span><span class="sxs-lookup"><span data-stu-id="3740c-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="3740c-162">Os arquivos *.xml* são divididos por pastas do SDK. Portanto, copie-os para o SDK correspondente que você escolheu na etapa 4.</span><span class="sxs-lookup"><span data-stu-id="3740c-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="3740c-163">Modificar o idioma do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3740c-163">Modify Visual Studio language</span></span>

<span data-ttu-id="3740c-164">Para que o Visual Studio use um idioma diferente para o IntelliSense, instale o pacote de idiomas apropriado.</span><span class="sxs-lookup"><span data-stu-id="3740c-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="3740c-165">Isso pode ser feito [durante a instalação](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) ou em um momento posterior, modificando a instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3740c-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="3740c-166">Se você já tiver o Visual Studio configurado para o idioma de sua escolha, a instalação do IntelliSense estará pronta.</span><span class="sxs-lookup"><span data-stu-id="3740c-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="3740c-167">Instalar o pacote de idiomas</span><span class="sxs-lookup"><span data-stu-id="3740c-167">Install the language pack</span></span>

<span data-ttu-id="3740c-168">Se você não instalou o pacote de idiomas desejado durante a instalação, atualize o Visual Studio da seguinte maneira para instalar o pacote de idiomas:</span><span class="sxs-lookup"><span data-stu-id="3740c-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3740c-169">Para instalar, atualizar ou modificar o Visual Studio, você deve fazer logon com uma conta que tenha permissão de administrador.</span><span class="sxs-lookup"><span data-stu-id="3740c-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="3740c-170">Para saber mais, confira [Permissões de usuário e Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="3740c-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="3740c-171">Localize o Instalador do Visual Studio no computador.</span><span class="sxs-lookup"><span data-stu-id="3740c-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="3740c-172">Por exemplo, em um computador que executa o Windows 10, selecione **Iniciar** e, em seguida, role até a letra **I**, onde ele está listado como **Instalador do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3740c-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![Abra o Instalador do Visual Studio no Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="3740c-174">Também é possível encontrar o Instalador do Visual Studio no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="3740c-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="3740c-175">Talvez você precise atualizar o instalador antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3740c-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="3740c-176">Nesse caso, siga os prompts.</span><span class="sxs-lookup"><span data-stu-id="3740c-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="3740c-177">No instalador, procure a edição do Visual Studio à qual você deseja adicionar o pacote de idiomas e escolha **Modificar**.</span><span class="sxs-lookup"><span data-stu-id="3740c-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![Atualizar ou modificar o Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="3740c-179">Se você não vir um botão **Modificar**, mas vir um **Atualizar**, será necessário atualizar seu Visual Studio antes de poder modificar sua instalação.</span><span class="sxs-lookup"><span data-stu-id="3740c-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="3740c-180">Depois que a atualização for concluída, o botão **Modificar** deverá ser exibido.</span><span class="sxs-lookup"><span data-stu-id="3740c-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="3740c-181">Na guia **Pacotes de idiomas**, selecione ou cancele a seleção dos idiomas que você deseja instalar ou desinstalar.</span><span class="sxs-lookup"><span data-stu-id="3740c-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Guia de pacotes de idiomas do Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="3740c-183">Escolha **Modificar**.</span><span class="sxs-lookup"><span data-stu-id="3740c-183">Choose **Modify**.</span></span> <span data-ttu-id="3740c-184">A atualização será iniciada.</span><span class="sxs-lookup"><span data-stu-id="3740c-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="3740c-185">Modificar as configurações de idioma no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3740c-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="3740c-186">Depois de instalar os pacotes de idiomas desejados, modifique suas configurações do Visual Studio para usar um idioma diferente:</span><span class="sxs-lookup"><span data-stu-id="3740c-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="3740c-187">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3740c-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="3740c-188">Na janela de início, escolha **Continuar sem código**.</span><span class="sxs-lookup"><span data-stu-id="3740c-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="3740c-189">Na barra de menus, selecione **ferramentas** > **Opções**.</span><span class="sxs-lookup"><span data-stu-id="3740c-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="3740c-190">A caixa de diálogo Opções é aberta.</span><span class="sxs-lookup"><span data-stu-id="3740c-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="3740c-191">No nó **ambiente** , escolha **configurações internacionais**.</span><span class="sxs-lookup"><span data-stu-id="3740c-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="3740c-192">No menu suspenso **Idioma**, selecione o idioma desejado.</span><span class="sxs-lookup"><span data-stu-id="3740c-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="3740c-193">Escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="3740c-193">Choose **OK**.</span></span>

1. <span data-ttu-id="3740c-194">Uma caixa de diálogo informa que você precisa reiniciar o Visual Studio para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="3740c-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="3740c-195">Escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="3740c-195">Choose **OK**.</span></span>

1. <span data-ttu-id="3740c-196">Reinicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3740c-196">Restart Visual Studio.</span></span>

<span data-ttu-id="3740c-197">Depois disso, seu IntelliSense deverá funcionar conforme o esperado quando você abrir um projeto do .NET Core que direciona a versão dos arquivos do IntelliSense que você acabou de instalar.</span><span class="sxs-lookup"><span data-stu-id="3740c-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="3740c-198">Confira também</span><span class="sxs-lookup"><span data-stu-id="3740c-198">See also</span></span>

- [<span data-ttu-id="3740c-199">IntelliSense no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3740c-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
