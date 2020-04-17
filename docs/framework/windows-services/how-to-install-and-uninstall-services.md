---
title: 'Como: Instalar e desinstalar serviços do Windows'
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 8937ef8b4007253b06444e59b292395084e4df2f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607913"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Como: Instalar e desinstalar serviços do Windows

Se você estiver desenvolvendo um serviço do Windows com o .NET Framework, você pode instalar rapidamente seu aplicativo de serviço usando o utilitário de linha de comando [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) ou [PowerShell](/powershell/scripting/overview). Os desenvolvedores que desejam lançar um serviço Windows que os usuários possam instalar e desinstalar devem usar o InstallShield. Para obter mais informações, consulte [Criar um pacote de instalação (desktop Windows)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

> [!WARNING]
> Se você deseja desinstalar um serviço do seu computador, não execute as etapas neste artigo. Nesse caso, descubra qual pacote de software ou programa instalou o serviço e, em seguida, escolha **Aplicativos** em Configurações para desinstalar o programa. Observe que muitos serviços são partes integrais do Windows, se você removê-los, poderá causar instabilidade do sistema.

Para seguir as etapas neste artigo, primeiro você precisa adicionar um instalador de serviço no serviço Windows. Para obter mais informações, consulte [Passo a Passo: Criando um aplicativo de serviço do Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Não é possível executar projetos de serviço Windows diretamente no ambiente de desenvolvimento do Visual Studio pressionando F5. Antes de executar o projeto, você precisa instalar o serviço no projeto.

> [!TIP]
> Você pode usar o **Gerenciador de Servidores** para verificar se instalou ou desinstalou o serviço. Para obter mais informações, confira [Como usar o Gerenciador de Servidores no Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually-using-installutilexe-utility"></a>Instale seu serviço manualmente usando o utilitário InstallUtil.exe

1. No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>**.

     O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.

2. Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.

3. Execute *InstallUtil.exe* do prompt de comando com o executável do projeto como um parâmetro:

    ```console
    installutil <yourproject>.exe
    ```

     Se você estiver usando o Prompt de Comando do Desenvolvedor para Visual Studio, *InstallUtil.exe* deverá estar no caminho do sistema. Caso contrário, você poderá adicioná-lo ao caminho ou usar o caminho totalmente qualificado para invocá-lo. Esta ferramenta está instalada com o .NET Framework em *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.

     Por exemplo:
     - para a versão de 32 bits do .NET Framework 4 ou 4.5 e posterior, se o diretório de instalação do Windows for *C:\Windows*, o caminho padrão será *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - para a versão de 64 bits do .NET Framework 4 ou 4.5 e posterior, o caminho padrão é *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>Desinstale seu serviço manualmente usando o utilitário InstallUtil.exe

1. No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>**.

     O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.

2. Execute *InstallUtil.exe* no prompt de comando com a saída do projeto como um parâmetro:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Depois que o executável de um serviço for excluído, o serviço ainda poderá estar presente no Registro. Nesse caso, use o comando [sc delete](/windows-server/administration/windows-commands/sc-delete) para remover a entrada do serviço do Registro.

### <a name="install-your-service-manually-using-powershell"></a>Instale seu serviço manualmente usando o PowerShell

1. No menu **Iniciar,** selecione o diretório **Windows PowerShell** e selecione **O Windows PowerShell**.

2. Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.

3. Execute o cmdlet [**do New-Service**](/powershell/module/microsoft.powershell.management/new-service) com a saída do seu projeto e um nome de serviço como parâmetros:

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>Desinstale seu serviço manualmente usando o PowerShell

1. No menu **Iniciar,** selecione o diretório **Windows PowerShell** e selecione **O Windows PowerShell**.

2. Execute o cmdlet [**remove-service**](/powershell/module/microsoft.powershell.management/remove-service) com o nome do seu serviço como parâmetro:

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. Depois que o executável de um serviço for excluído, o serviço ainda poderá estar presente no Registro. Nesse caso, use o comando [sc delete](/windows-server/administration/windows-commands/sc-delete) para remover a entrada do serviço do Registro.

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>Confira também

- [Introdução aos aplicativos do serviço Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Como: Criar serviços do Windows](../windows-services/how-to-create-windows-services.md)
- [Como: Adicionar instaladores ao seu aplicativo de serviço](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (Ferramenta de Instalação)](../tools/installutil-exe-installer-tool.md)
