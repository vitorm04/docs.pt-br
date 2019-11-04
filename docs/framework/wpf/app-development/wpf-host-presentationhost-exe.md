---
title: Host do WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 981e518a55f179c2fbf44534783c80fb230e4ecf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421119"
---
# <a name="wpf-host-presentationhostexe"></a>Host do WPF (PresentationHost.exe)
Windows Presentation Foundation (WPF) host (PresentationHost. exe) é o aplicativo que permite que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos sejam hospedados em navegadores compatíveis (incluindo o Microsoft Internet Explorer 6 e posterior). Por padrão, o host do Windows Presentation Foundation (WPF) é registrado como o Shell e o manipulador de MIME para conteúdo de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hospedado no navegador, que inclui:  
  
- Arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) flexíveis (não compilados).  
  
- Aplicativo de navegador XAML (XBAP) (. XBAP).  
  
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
|filename|O caminho do arquivo a ser ativado. Também pode ser um URI.|  
|-debug|Ao ativar um aplicativo, não o confirme, nem o execute por meio do repositório. Isso só funciona quando um arquivo local é ativado.|  
|-debugSecurityZoneURL \<url>|Usado com um valor de URL para indicar ao PresentationHost. exe que um aplicativo deve ser depurado como se fosse implantado a partir da URL especificada. Isso determina a zona de implantação e o site de origem.|  
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

- [Security](../security-wpf.md)
