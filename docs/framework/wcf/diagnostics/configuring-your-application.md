---
title: Configurando seu aplicativo
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 7dfd662fafa636e0fa97f118217ad1786d5aa444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-your-application"></a>Configurando seu aplicativo
Windows Communication Foundation (WCF) usa o sistema de configuração do .NET e permite que você configure serviços no escopo máquina e do aplicativo.  
  
 Configurações definidas por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estão localizados no `<system.serviceModel>` grupo da seção. Para obter mais informações sobre como configurar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço, consulte os tópicos a seguir:  
  
-   [Configurando serviços](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 As definições de configuração definido pelo aplicativo estão definidas no `<appSettings>` grupo da seção. Para obter mais informações sobre configurações de aplicativo em arquivos de configuração do .NET, consulte [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Usando o Editor de configuração  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) permite que os administradores e desenvolvedores criar e modificar definições de configuração para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços usando a interface gráfica do usuário. Com essa ferramenta, você pode gerenciar configurações para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações, comportamentos, serviços e diagnósticos sem editar diretamente os arquivos de configuração XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Editando arquivos de configuração no Visual Studio  
 Para editar o arquivo de configuração de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço de projeto no Visual Studio, clique com botão direito no **Solution Explorer** e escolha o **Editar configuração do WCF** item de menu de contexto. Isso inicia o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Se você editar o arquivo de configuração de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projeto de serviço da Web no Visual Studio clicando em **Solution Explorer**, observe que o **Editar configuração do WCF** item de menu de contexto está ausente. Para solucionar esse problema, clique no **ferramentas** menu e escolha **Editor de configuração de serviço do WCF**. Depois disso, selecione o arquivo de configuração e use o **Editar configuração do WCF** item de menu de contexto.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta Editor de configuração (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Configurando serviços](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
