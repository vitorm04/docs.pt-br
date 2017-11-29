---
title: Configurando seu aplicativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f22fac02616070ecd6498ad0e158782001681ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-your-application"></a>Configurando seu aplicativo
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]usa o sistema de configuração do .NET e permite que você configure serviços no escopo máquina e do aplicativo.  
  
 Configurações definidas por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estão localizados no `<system.serviceModel>` grupo da seção. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como configurar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço, consulte os tópicos a seguir:  
  
-   [Configuring Services](../../../../docs/framework/wcf/configuring-services.md) (Configurando serviços)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 As definições de configuração definido pelo aplicativo estão definidas no `<appSettings>` grupo da seção. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]configurações do aplicativo em arquivos de configuração do .NET, consulte [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Usando o Editor de configuração  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) permite que os administradores e desenvolvedores criar e modificar definições de configuração para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços usando a interface gráfica do usuário. Com essa ferramenta, você pode gerenciar configurações para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações, comportamentos, serviços e diagnósticos sem editar diretamente os arquivos de configuração XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Editando arquivos de configuração no Visual Studio  
 Para editar o arquivo de configuração de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projeto de serviço no [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], clique com botão direito no **Solution Explorer** e escolha o **Editar configuração do WCF** item de menu de contexto. Isso inicia o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Se você editar o arquivo de configuração de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projeto de serviço da Web em [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] clicando no **Solution Explorer**, observe que o **Editar configuração do WCF** item de menu de contexto está ausente . Para solucionar esse problema, clique no **ferramentas** menu e escolha **Editor de configuração de serviço do WCF**. Depois disso, selecione o arquivo de configuração e use o **Editar configuração do WCF** item de menu de contexto.  
  
## <a name="see-also"></a>Consulte também  
 [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) (Ferramenta Editor de configuração (SvcConfigEditor.exe))  
 [Configuring Services](../../../../docs/framework/wcf/configuring-services.md) (Configurando serviços)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
