---
title: Host do WPF (PresentationHost.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c5a9df438353701932a3e732d6df28b08402ee8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-host-presentationhostexe"></a>Host do WPF (PresentationHost.exe)
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host (PresentationHost.exe) é o aplicativo que habilita aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sejam hospedados em navegadores compatíveis (incluindo [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] e posterior). Por padrão, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host é registrado como shell e o manipulador [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] para conteúdo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hospedado em navegador, que inclui:  
  
-   Arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) flexíveis (não compilados).  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Para esses tipos de arquivos, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host:  
  
-   Inicia o manipulador [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] registrado para hospedar o conteúdo [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
-   Carrega as versões corretas dos assemblies [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] e [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] necessários.  
  
-   Garante que os níveis de permissão apropriados para a zona de implantação estejam em vigor.  
  
 Este tópico descreve os parâmetros de linha de comando que podem ser usados com PresentationHost.exe.  
  
## <a name="usage"></a>Uso  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|filename|O caminho do arquivo a ser ativado. Também pode ser um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|-debug|Ao ativar um aplicativo, não o confirme, nem o execute por meio do repositório. Isso só funciona quando um arquivo local é ativado.|  
|-debugSecurityZoneURL \<url>|Usado com um valor [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] para indicar ao PresentationHost.exe que um aplicativo deve ser depurado como se ele fosse implantado por meio do [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] especificado. Isso determina a zona de implantação e o site de origem.|  
|-embedding|Exigido pelo OLE. Se o parâmetro `-event` ou `-debug` estiver especificado, não será necessário especificar o parâmetro `-embedding`, já que esse parâmetro é definido internamente.|  
|-event \<eventname>|Abra o evento com este nome e o sinalize quando o PresentationHost.exe for inicializado e estiver pronto para hospedar conteúdo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. O PresentationHost.exe será encerrado se houver um erro ao abrir o evento, tal como se ele ainda não tiver sido criado.|  
|-launchApplication \<url>|Inicia um aplicativo [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] autônomo da URL especificada. [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] e a política de segurança de WinINet sobre aplicativos .NET são aplicadas.|  
  
## <a name="scenarios"></a>Cenários  
  
### <a name="shell-handler"></a>Manipulador de shell  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>Manipulador MIME  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Depuração do Visual Studio  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Depuração do Visual Studio na Zona  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Consulte também  
 [Segurança](../../../../docs/framework/wpf/security-wpf.md)
