---
title: Host do WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: ca8198e17bec62866b6a58e6fd14ea468308f48b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552682"
---
# <a name="wpf-host-presentationhostexe"></a>Host do WPF (PresentationHost.exe)
Host do Windows Presentation Foundation (WPF) (PresentationHost.exe) é o aplicativo que permite [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos sejam hospedados em navegadores compatíveis (incluindo [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] e posterior). Por padrão, o Host do Windows Presentation Foundation (WPF) é registrado como o shell e [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] hospedados pelo navegador manipulador [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] conteúdo, que inclui:  
  
-   Arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) flexíveis (não compilados).  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Para arquivos desses tipos, o Host do Windows Presentation Foundation (WPF):  
  
-   Inicia o registrado [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] manipulador para hospedar o conteúdo do Windows Presentation Foundation (WPF).  
  
-   Carrega as versões corretas do necessários [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] e assemblies do Windows Presentation Foundation (WPF).  
  
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
