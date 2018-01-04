---
title: "Administração e diagnósticos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d26386a0669c92b1b21559474c8f5f61862e6de7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="administration-and-diagnostics"></a>Administração e diagnósticos
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Fornece um rico conjunto de funcionalidades que podem ajudá-lo a monitorar os diferentes estágios de vida do aplicativo. Por exemplo, você pode usar a configuração para configurar serviços e clientes na implantação. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]inclui um grande conjunto de contadores de desempenho para ajudá-lo a avaliar o desempenho do aplicativo. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]também expõe dados de inspeção de um serviço em tempo de execução por meio de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provedor do Windows Management Instrumentation (WMI). Quando o aplicativo apresenta uma falha ou inicia funcionando incorretamente, você pode usar o Log de eventos para ver se algo significativo ocorreu. Você também pode usar a mensagem de log e rastreamento para ver quais eventos estão acontecendo ponta em seu aplicativo. Esses recursos ajudar os desenvolvedores e profissionais de TI para solucionar problemas de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo quando ele não está funcionando corretamente.  
  
> [!NOTE]
>  Se você estiver recebendo falhas sem informações de detalhe específico, você deve habilitar o `includeExceptionDetailInFaults` atributo o [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) elemento de configuração. Isso instrui [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] enviar detalhes da exceção para clientes, o que permite que você detecte muitos problemas comuns sem a necessidade de diagnóstico mais avançado. Para obter mais informações, consulte [enviando e recebendo falhas](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Recursos de diagnóstico fornecidos pelo WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece os recursos de diagnóstico a seguir:  
  
-   Rastreamento ponta a ponta fornece dados de instrumentação para solucionar problemas de um aplicativo sem usar um depurador. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]gera rastreamentos de etapas do processo, bem como mensagens de erro. Isso pode incluir a abertura de uma fábrica de canais ou enviar e receber mensagens por um host de serviço. O rastreamento pode ser habilitado para um aplicativo em execução monitorar seu progresso. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]o [rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/index.md) tópico. Para entender como você pode usar o rastreamento para depurar seu aplicativo, consulte o [usando o rastreamento para solucionar problemas de seu aplicativo](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) tópico.  
  
-   Log de mensagens permite que você veja a aparência de mensagens antes e após a transmissão. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]o [Message Logging](../../../../docs/framework/wcf/diagnostics/message-logging.md) tópico.  
  
-   Rastreamento de eventos grava os eventos no Log de eventos para problemas importantes. Você pode usar o Visualizador de eventos para examinar qualquer anomalia. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]o [log de eventos](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) tópico.  
  
-   Contadores de desempenho expostos por meio do Monitor de desempenho permitem monitorar a integridade do sistema e seu aplicativo. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]o [contadores de desempenho](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) tópico.  
  
-   O <xref:System.ServiceModel.Configuration> namespace permite carregar arquivos de configuração e configurar um ponto de extremidade de serviço ou cliente. Você pode usar o modelo de objeto para alterações de script para muitos aplicativos quando as atualizações devem ser implantadas em vários computadores. Como alternativa, você pode usar o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) para editar as definições de configuração usando um Assistente de interface gráfica do usuário. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]o [configurando seu aplicativo](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) tópico.  
  
-   WMI permite que você descubra quais serviços estão escutando em um computador e as associações que estão em uso. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]o [usando o Windows Management Instrumentation para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md) tópico.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]também fornece várias ferramentas de linha de comando e GUI para tornar mais fácil de criar, implantar e gerenciar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Ferramentas do Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Por exemplo, você pode usar o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) para criar e editar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] definições de configuração usando um assistente, em vez de editar o XML diretamente. Você também pode usar o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para exibir, agrupar e filtrar as mensagens de rastreamento para que você pode diagnosticar, reparar e verificar problemas com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.  
  
## <a name="see-also"></a>Consulte também  
 [Configurar seu aplicativo](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [Serviços de implantação](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [Referência de exceções](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [Registro de eventos em log](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [Registro de mensagens em log](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Ferramenta Editor de configuração (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Ferramenta de registro de ServiceModel](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [Rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando a Instrumentação de Gerenciamento do Windows para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [Contadores de desempenho](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Ferramentas do Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)
