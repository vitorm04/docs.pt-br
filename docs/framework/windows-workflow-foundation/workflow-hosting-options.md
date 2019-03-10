---
title: Opções de hospedagem de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 2a03c7b5e15b76eabc714f44624f04d3385720d4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713313"
---
# <a name="workflow-hosting-options"></a>Opções de hospedagem de fluxo de trabalho
A maioria dos exemplos do Windows Workflow Foundation (WF) usa fluxos de trabalho que são hospedados em um aplicativo de console, mas isso não é um cenário realista para fluxos de trabalho do mundo real. Os fluxos de trabalho em aplicativos comerciais reais serão hospedados em processos persistentes: um serviço do Windows criado pelo desenvolvedor ou um aplicativo de servidor como [!INCLUDE[iisver](../../../includes/iisver-md.md)] ou AppFabric. As diferenças entre essas abordagens são as seguintes.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Fluxos de trabalho de hospedagem no IIS com o Windows AppFabric  
 Usar o IIS com AppFabric é o host preferido para fluxos de trabalho. O aplicativo de host para fluxos de trabalho que usam AppFabric é o WAS (Serviços de Ativação do Windows), que remove a dependência de HTTP em IIS somente.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Fluxos de trabalho de hospedagem apenas no IIS  
 Usar apenas o [!INCLUDE[iisver](../../../includes/iisver-md.md)] não é recomendado, pois há ferramentas de gerenciamento e monitoramento disponíveis com o AppFabric que facilitam a manutenção de aplicativos em execução. Os fluxos de trabalho somente devem ser hospedados no [!INCLUDE[iisver](../../../includes/iisver-md.md)] apenas se houver preocupações de infraestrutura sobre mover para o AppFabric.  
  
> [!WARNING]
>  O [!INCLUDE[iisver](../../../includes/iisver-md.md)] recicla pools de aplicativos periodicamente por várias razões. Quando um pool de aplicativos é reciclado, o IIS para de aceitar mensagens para o pool antigo e cria uma instância de um pool de aplicativos para aceitar novas solicitações. Se um fluxo de trabalho continua funcionando depois de enviar uma resposta, o [!INCLUDE[iisver](../../../includes/iisver-md.md)] não estará ciente do trabalho que está sendo feito e poderá reciclar o pool de aplicativos de hospedagem. Se isso acontecer, o fluxo de trabalho será anulada e serviços de controle serão gravado um [1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md) mensagem com um campo de motivo vazio.  
>   
>  Se a persistência for usada, o host deverá reiniciar explicitamente as instâncias anuladas a partir do último ponto de persistência.  
>   
>  Se o AppFabric for usado, o serviço de gerenciamento de fluxo de trabalho finalmente retomará o fluxo de trabalho a partir do último ponto de persistência bem-sucedido se a persistência tiver sido usada. Se nenhuma persistência tiver sido usada e o fluxo de trabalho executar operações fora de um padrão de solicitação/resposta, os dados serão perdidos quando o fluxo de trabalho for anulado.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hospedando um fluxo de trabalho em um serviço do Windows personalizado  
 Criar um serviço de fluxo de trabalho personalizado para hospedar o fluxo de trabalho exigirá que o desenvolvedor duplique muito da funcionalidade fornecida pronta pelo AppFabric, mas permitirá mais flexibilidade com funcionalidade personalizada. Essa opção somente deverá ser considerada se o AppFabric provar não ser uma opção.
