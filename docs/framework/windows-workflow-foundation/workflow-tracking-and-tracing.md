---
title: Rastreamento e rastreamento de fluxo de trabalho
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: 9f887babec5c070eed2fb3c7e4d8d35cdfb3f488
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837474"
---
# <a name="workflow-tracking-and-tracing"></a>Rastreamento e rastreamento de fluxo de trabalho
O rastreamento de fluxo de trabalho do Windows é um recurso de [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] projetado para fornecer a visibilidade no fluxo de trabalho. Fornece uma infraestrutura de rastreamento para controlar a execução de uma instância de fluxo de trabalho. De WF de rastreamento de infraestrutura os implementa transparente um fluxo de trabalho para emitir os registros que refletem eventos chave durante a execução. Essa funcionalidade está disponível por padrão para qualquer fluxo de trabalho [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] . Nenhuma alteração é necessária para ser feita a um fluxo de trabalho para acompanhar [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] que ocorra. É apenas uma questão de decidir quanto dados de acompanhamento você deseja receber. Quando inicia de uma instância de fluxo de trabalho ou tiver terminado, seus registros de acompanhamento de processamento são emitidas. O rastreamento também pode extrair os dados negócio- relevantes associados com variáveis de fluxo de trabalho. Por exemplo, se o fluxo de trabalho representa um sistema de processamento de aplicativos, a identificação do pedido pode ser extraído juntamente com o objeto de <xref:System.Activities.Tracking.TrackingRecord> . Geralmente, ative o rastreamento de WF facilita diagnóstico ou dados de análise de negócio a ser acessados de uma execução de fluxo de trabalho.  
  
 Esses componentes de acompanhamento são equivalentes ao serviço de rastreamento no WinFX. Em [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], o desempenho foi aprimorado e o modelo de programação foi simplificado para o recurso de rastreamento de WF. Os implementa de rastreamento uma instância de fluxo de trabalho para emitir eventos relacionados ao ciclo de vida de trabalho, para atividades de trabalho e eventos personalizados.  
  
 A tela de aplicativo Windows Server também fornece a capacidade de monitorar a execução do windows e serviços de fluxo de trabalho. Para obter mais informações, consulte aplicativos de monitoramento e monitoramento do [Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10)) [com o Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))  
  
 Para solucionar o runtime de fluxo de trabalho, você pode ativar o rastreamento diagnóstico de fluxo de trabalho. Para obter mais informações, consulte [rastreamento de fluxo de trabalho](workflow-tracing.md).  
  
 Para entender o modelo de programação, os componentes principais de infraestrutura de rastreamento são abordados neste tópico:  
  
- objetos de<xref:System.Activities.Tracking.TrackingRecord> emissores do runtime de fluxo de trabalho. Para obter mais informações, consulte [Tracking Records](tracking-records.md).  
  
- os objetos de<xref:System.Activities.Tracking.TrackingParticipant> a autenticação <xref:System.Activities.Tracking.TrackingRecord> objetos. Os participantes de rastreamento contém a lógica para processar a carga útil dos objetos de <xref:System.Activities.Tracking.TrackingRecord> (por exemplo, poderia escolher gravar em um arquivo). Para obter mais informações, consulte [rastrear participantes](tracking-participants.md).  
  
- os registros de acompanhamento de filtro de objetos de<xref:System.Activities.Tracking.TrackingProfile> emissores de um fluxo de trabalho instância. Para obter mais informações, consulte [perfis de rastreamento](tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Infraestrutura de acompanhamento de fluxo de trabalho  
 A infraestrutura de acompanhamento de fluxo de trabalho segue um paradigma publicar-e- assinatura. A instância de fluxo de trabalho é o editor de registros de rastreamento, quando os assinantes de registros de rastreamento são registrados como extensões para o fluxo de trabalho. Essas extensões que assina a <xref:System.Activities.Tracking.TrackingRecord> objetos são chamadas controlar participantes. Os participantes de rastreamento são os pontos de extensibilidade no qual acessar objetos de <xref:System.Activities.Tracking.TrackingRecord> e os processar o que são escritos maneira para fazer isso. A infraestrutura de rastreamento permite o aplicativo de um filtro os registros de saída do rastreamento permitir que um participante assine a um subconjunto de registros. Esse mecanismo de filtragem é feito através de um arquivo de perfil de rastreamento.  
  
 Uma exibição de alto nível da infraestrutura de rastreamento é mostrada na ilustração a seguir:  
  
 ![Captura de tela que mostra a infraestrutura de rastreamento de fluxo de trabalho.](./media/workflow-tracking-and-tracing/workflow-tracking-infrastructure.gif "WV")  
  
## <a name="in-this-section"></a>Nesta seção  
 [Acompanhando registros](tracking-records.md)  
 Descreve os registros de rastreamento que o runtime de fluxo de trabalho se emite.  
  
 [Acompanhando perfis](tracking-profiles.md)  
 Discute como controlando os perfis são usados.  
  
 [Acompanhando participantes](tracking-participants.md)  
 Descreve como usar o sistema forneceu participante de rastreamento ou como criar participantes personalizados de rastreamento.  
  
 [Configurando o acompanhamento para um fluxo de trabalho](configuring-tracking-for-a-workflow.md)  
 Descreve como configurar o rastreamento para um fluxo de trabalho.  
  
 [Acompanhamento de fluxo de trabalho](workflow-tracing.md)  
 Descreve as duas maneiras para ativar o rastreamento de depuração para um fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também

- [Acompanhamento de SQL](./samples/sql-tracking.md)
