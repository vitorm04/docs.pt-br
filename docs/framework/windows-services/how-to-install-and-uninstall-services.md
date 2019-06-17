---
title: 'Como: instalar e desinstalar serviços Windows'
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
ms.openlocfilehash: 4f6e25467e713263ab5cdecc08078153098fdede
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690685"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Como: instalar e desinstalar serviços Windows

Se você estiver desenvolvendo um serviço Windows usando o .NET Framework, instale rapidamente o aplicativo de serviço usando o utilitário de linha de comando [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md). Os desenvolvedores que desejam lançar um serviço Windows que os usuários possam instalar e desinstalar devem usar o InstallShield. Para obter mais informações, confira [Criar um pacote do instalador (cliente Windows)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).

> [!WARNING]
> Se você deseja desinstalar um serviço do seu computador, não execute as etapas neste artigo. Nesse caso, descubra qual pacote de software ou programa instalou o serviço e, em seguida, escolha **Aplicativos** em Configurações para desinstalar o programa. Observe que muitos serviços são partes integrais do Windows, se você removê-los, poderá causar instabilidade do sistema.

Para seguir as etapas neste artigo, primeiro você precisa adicionar um instalador de serviço no serviço Windows. Para obter mais informações, confira [Passo a passo: criando um aplicativo de serviço Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Não é possível executar projetos de serviço Windows diretamente no ambiente de desenvolvimento do Visual Studio pressionando F5. Antes de executar o projeto, você precisa instalar o serviço no projeto.

> [!TIP]
> Você pode usar o **Gerenciador de Servidores** para verificar se instalou ou desinstalou o serviço. Para obter mais informações, confira [Como usar o Gerenciador de Servidores no Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually"></a>Instalar o serviço manualmente

1. No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>** .

     O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.

2. Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.

3. Execute *InstallUtil.exe* do prompt de comando com o executável do projeto como um parâmetro:

    ```console
    installutil <yourproject>.exe
    ```

     Se você estiver usando o Prompt de Comando do Desenvolvedor para Visual Studio, *InstallUtil.exe* deverá estar no caminho do sistema. Caso contrário, você poderá adicioná-lo ao caminho ou usar o caminho totalmente qualificado para invocá-lo. Essa ferramenta é instalada com o .NET Framework em *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>* .

     Por exemplo:
     - para a versão de 32 bits do .NET Framework 4 ou 4.5 e posterior, se o diretório de instalação do Windows for *C:\Windows*, o caminho padrão será *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - para a versão de 64 bits do .NET Framework 4 ou 4.5 e posterior, o caminho padrão é *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually"></a>Desinstalar o serviço manualmente

1. No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>** .

     O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.

2. Execute *InstallUtil.exe* no prompt de comando com a saída do projeto como um parâmetro:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Depois que o executável de um serviço for excluído, o serviço ainda poderá estar presente no Registro. Nesse caso, use o comando [sc delete](/windows-server/administration/windows-commands/sc-delete) para remover a entrada do serviço do Registro.

## <a name="see-also"></a>Consulte também

- [Introdução aos aplicativos do serviço Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Como: criar serviços Windows](../windows-services/how-to-create-windows-services.md)
- [Como: adicionar instaladores ao aplicativo de serviço](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (ferramenta de instalação)](../tools/installutil-exe-installer-tool.md)
