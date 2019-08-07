---
title: Host do WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 88e4c6895039c84a57ed215a37a10a4b68851b2d
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817917"
---
# <a name="wpf-host-presentationhostexe"></a>Host do WPF (PresentationHost.exe)
Windows Presentation Foundation (WPF) host (PresentationHost. exe) é o aplicativo que permite [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] que os aplicativos sejam hospedados em navegadores compatíveis (incluindo o Microsoft Internet Explorer 6 e posterior). Por padrão, o host do Windows Presentation Foundation (WPF) é registrado como o [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] Shell e o manipulador para [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] conteúdo hospedado em navegador, o que inclui:  
  
- Arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) flexíveis (não compilados).  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Para arquivos desses tipos, Windows Presentation Foundation (WPF) host:  
  
- Inicia o manipulador HTML registrado para hospedar o conteúdo do Windows Presentation Foundation (WPF).  
  
- Carrega as versões corretas dos assemblies Common Language Runtime (CLR) e Windows Presentation Foundation (WPF) necessários.  
  
- Garante que os níveis de permissão apropriados para a zona de implantação estejam em vigor.  
  
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
|-launchApplication \<url>|Inicia um aplicativo ClickOnce autônomo a partir da URL especificada. A política de segurança do Internet Explorer e WinINet relacionada a aplicativos .NET são aplicadas.|  
  
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

- [Segurança](../security-wpf.md)
