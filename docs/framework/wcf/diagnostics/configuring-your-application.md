---
title: Configurando seu aplicativo
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: e096f4b64ada8b142e8b82c8877eec7f1b84637c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939805"
---
# <a name="configuring-your-application"></a>Configurando seu aplicativo
O Windows Communication Foundation (WCF) usa o sistema de configuração do .NET e permite que você configure serviços no escopo do computador e do aplicativo.  
  
 As definições de configuração definidas pelo WCF estão localizadas no grupo de `<system.serviceModel>` seções. Para obter mais informações sobre como configurar um serviço WCF, consulte os seguintes tópicos:  
  
- [Configurando serviços](../../../../docs/framework/wcf/configuring-services.md)  
  
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 As definições de configurações definidas pelo aplicativo são definidas `<appSettings>` no grupo de seções. Para obter mais informações sobre configurações de aplicativo em arquivos de configuração do .net, consulte [ \<appSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Usando o editor de configuração  
 A [ferramenta Editor de configuração do WCF (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) permite que administradores e desenvolvedores criem e modifiquem definições de configuração para serviços WCF usando uma interface gráfica do usuário. Com essa ferramenta, você pode gerenciar configurações para associações, comportamentos, serviços e diagnósticos do WCF sem editar diretamente os arquivos de configuração XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Editando arquivos de configuração no Visual Studio  
 Para editar o arquivo de configuração de um projeto de serviço WCF no Visual Studio, clique com o botão direito do mouse no **Gerenciador de soluções** e escolha o item de menu editar o contexto de **configuração do WCF** . Isso inicia a [ferramenta do editor de configuração (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
> Se você editar o arquivo de configuração de um projeto de serviço Web WCF no Visual Studio, clicando com o botão direito do mouse no **Gerenciador de soluções**, observe que o item de menu Editar contexto de **configuração do WCF** está ausente. Para solucionar esse problema, clique no menu **ferramentas** e escolha **Editor de configuração do serviço WCF**. Depois disso, você pode clicar com o botão direito do mouse em um arquivo de configuração e usar o item de menu de contexto **Editar configuração do WCF** .  
  
## <a name="see-also"></a>Consulte também

- [Ferramenta Editor de configuração (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Configurando serviços](../../../../docs/framework/wcf/configuring-services.md)
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
