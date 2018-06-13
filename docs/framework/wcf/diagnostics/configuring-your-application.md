---
title: Configurando seu aplicativo
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 1844c20ef961f191fb667e31d548518b193a7134
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803644"
---
# <a name="configuring-your-application"></a>Configurando seu aplicativo
Windows Communication Foundation (WCF) usa o sistema de configuração do .NET e permite que você configure serviços no escopo máquina e do aplicativo.  
  
 Configurações definidas pelo WCF estão localizadas no `<system.serviceModel>` grupo da seção. Para obter mais informações sobre como configurar um serviço WCF, consulte os tópicos a seguir:  
  
-   [Configurando serviços](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 As definições de configuração definido pelo aplicativo estão definidas no `<appSettings>` grupo da seção. Para obter mais informações sobre configurações de aplicativo em arquivos de configuração do .NET, consulte [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Usando o Editor de configuração  
 O WCF[ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) permite que os administradores e desenvolvedores criar e modificar definições de configuração para serviços WCF usando uma interface gráfica do usuário. Com essa ferramenta, você pode gerenciar as configurações para associações do WCF, comportamentos, serviços e diagnóstico sem editar diretamente os arquivos de configuração XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Editando arquivos de configuração no Visual Studio  
 Para editar o arquivo de configuração de um projeto de serviço do WCF no Visual Studio, clique com botão direito no **Solution Explorer** e escolha o **Editar configuração do WCF** item de menu de contexto. Isso inicia o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Se você editar o arquivo de configuração de um projeto de serviço Web WCF no Visual Studio clicando em **Solution Explorer**, observe que o **Editar configuração do WCF** item de menu de contexto está ausente. Para solucionar esse problema, clique no **ferramentas** menu e escolha **Editor de configuração de serviço do WCF**. Depois disso, selecione o arquivo de configuração e use o **Editar configuração do WCF** item de menu de contexto.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta Editor de configuração (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Configurando serviços](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
