---
title: Como instalar e desinstalar serviços
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
manager: douge
ms.openlocfilehash: 9d8e84280b5821f8d8df36694198bd85fb8470d4
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46698383"
---
# <a name="how-to-install-and-uninstall-services"></a>Como instalar e desinstalar serviços
Se você estiver desenvolvendo um serviço Windows usando o .NET Framework, você pode rapidamente instalar seu aplicativo de serviço usando um utilitário de linha de comando chamado InstallUtil.exe. Se você for um desenvolvedor que deseja liberar um serviço Windows que os usuários possam instalar e desinstalar, você deve usar o InstallShield. Confira [Implantação do Windows Installer](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
> [!WARNING]
>  Se você deseja desinstalar um serviço do seu computador, não execute as etapas neste artigo. Nesse caso, descubra qual pacote de software ou programa instalou o serviço e escolha **Adicionar ou remover programas** no Painel de Controle para desinstalar o programa. Observe que muitos serviços são partes integrais do Windows, se você removê-los, poderá causar instabilidade do sistema.  
  
 Para usar as etapas neste artigo, primeiro é necessário adicionar um instalador de serviço para o serviço Windows. Confira [Passo a passo: criando um aplicativo de Serviço Windows no designer de componentes](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Projetos de serviço Windows não podem ser executados diretamente do ambiente de desenvolvimento do Visual Studio pressionando F5. Isso ocorre porque o serviço no projeto deve ser instalado antes de executar o projeto.  
  
> [!TIP]
>  Você pode iniciar o **Gerenciador de Servidores** e verificar se o serviço foi instalado ou desinstalado. Para obter mais informações, consulte Como acessar e inicializar o Gerenciador de Servidores/Gerenciador de Banco de Dados.  
  
### <a name="to-install-your-service-manually"></a>Para instalar o serviço manualmente  
  
1.  No menu **Iniciar** ou na tela **Iniciar** do Windows, escolha **Visual Studio**, **Ferramentas do Visual Studio**, **Prompt de Comando do Desenvolvedor**.  
  
     É exibido um prompt de comando do Visual Studio.  
  
2.  Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.  
  
3.  Execute o InstallUtil.exe no prompt de comando com o executável do projeto como um parâmetro:  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Se você estiver usando o prompt de comando do Visual Studio, o InstallUtil.exe deve estar no caminho do sistema. Caso contrário, você pode adicioná-lo ao caminho ou usar o caminho totalmente qualificado para invocá-lo. Essa ferramenta é instalada com o .NET Framework e o caminho é `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`. Por exemplo, para a versão de 32 bits do .NET Framework 4 ou 4.5.*, se o diretório de instalação do Windows for C:\Windows, o caminho é `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`. Para a versão de 64 bits do .NET Framework 4 ou 4.5.\*, o caminho padrão é `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.  
  
### <a name="to-uninstall-your-service-manually"></a>Para desinstalar o serviço manualmente  
  
1.  No menu **Iniciar** ou na tela **Iniciar** do Windows, escolha **Visual Studio**, **Ferramentas do Visual Studio**, **Prompt de Comando do Desenvolvedor**.  
  
     É exibido um prompt de comando do Visual Studio.  
  
2.  Execute o InstallUtil.exe no prompt de comando com a saída do projeto como um parâmetro:  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  Às vezes, depois que o executável de um serviço é excluído, o serviço ainda pode estar presente no registro. Nesse caso, use o comando [sc delete](https://technet.microsoft.com/library/cc742045.aspx) para remover a entrada para o serviço do registro.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Como criar Serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Como adicionar instaladores no seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Installutil.exe (Ferramenta de Instalação)](../../../docs/framework/tools/installutil-exe-installer-tool.md)
