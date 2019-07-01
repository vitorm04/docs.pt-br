---
title: Opções de hospedagem de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: b0cd9748c28cd6206e1fedffc5772b2849462dba
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487362"
---
# <a name="workflow-hosting-options"></a>Opções de hospedagem de fluxo de trabalho
A maioria dos exemplos do Windows Workflow Foundation (WF) usa fluxos de trabalho que são hospedados em um aplicativo de console, mas isso não é um cenário realista para fluxos de trabalho do mundo real. Fluxos de trabalho em aplicativos de negócios real serão hospedados em processos persistentes: um serviço Windows criado pelo desenvolvedor ou um aplicativo de servidor, como o IIS 7.0 ou AppFabric. As diferenças entre essas abordagens são as seguintes.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Fluxos de trabalho de hospedagem no IIS com o Windows AppFabric  
 Usar o IIS com AppFabric é o host preferido para fluxos de trabalho. O aplicativo de host para fluxos de trabalho que usam AppFabric é o WAS (Serviços de Ativação do Windows), que remove a dependência de HTTP em IIS somente.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Fluxos de trabalho de hospedagem apenas no IIS  
 Não é recomendável usar o IIS 7.0 sozinho, pois há gerenciamento e ferramentas de monitoramento disponíveis com o AppFabric que facilitam a manutenção de aplicativos em execução. Fluxos de trabalho somente devem ser hospedados no IIS 7.0 apenas se houver preocupações de infraestrutura sobre mover para o AppFabric.  
  
> [!WARNING]
>  O IIS 7.0 recicla pools de aplicativos periodicamente por vários motivos. Quando um pool de aplicativos é reciclado, o IIS para de aceitar mensagens para o pool antigo e cria uma instância de um pool de aplicativos para aceitar novas solicitações. Se um fluxo de trabalho continua funcionando depois de enviar uma resposta, o IIS 7.0 não estará ciente de que o trabalho sendo feito e poderá reciclar o pool de aplicativos de hospedagem. Se isso acontecer, o fluxo de trabalho será anulada e serviços de controle serão gravado um [1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md) mensagem com um campo de motivo vazio.  
>   
>  Se a persistência for usada, o host deverá reiniciar explicitamente as instâncias anuladas a partir do último ponto de persistência.  
>   
>  Se o AppFabric for usado, o serviço de gerenciamento de fluxo de trabalho finalmente retomará o fluxo de trabalho a partir do último ponto de persistência bem-sucedido se a persistência tiver sido usada. Se nenhuma persistência tiver sido usada e o fluxo de trabalho executar operações fora de um padrão de solicitação/resposta, os dados serão perdidos quando o fluxo de trabalho for anulado.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hospedando um fluxo de trabalho em um serviço do Windows personalizado  
 Criar um serviço de fluxo de trabalho personalizado para hospedar o fluxo de trabalho exigirá que o desenvolvedor duplique muito da funcionalidade fornecida pronta pelo AppFabric, mas permitirá mais flexibilidade com funcionalidade personalizada. Essa opção somente deverá ser considerada se o AppFabric provar não ser uma opção.
