---
title: Rastreamento de variável e argumento
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: 45ed3761cd7ead82650023b93a2f32a43e847339
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990811"
---
# <a name="variable-and-argument-tracking"></a>Rastreamento de variável e argumento
Para controlar a execução de um fluxo de trabalho, geralmente é útil extrair dados. Isso fornece um contexto extra para acessar uma execução de postagem de registro de rastreamento. Em [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], você pode extrair qualquer variável ou argumento visível no escopo de qualquer atividade em um fluxo de trabalho usando o rastreamento. Controlando os perfis facilitam extrair dados.  
  
## <a name="variables-and-arguments"></a>Variáveis e argumentos  
 Variáveis e os argumentos são extraídos quando uma atividade se emite um ActivityStateRecord.  Uma variável está disponível para a extração somente se está no escopo da atividade. Uma variável para ser extraído dentro de uma atividade é especificado da seguinte maneira:  
  
-   Se uma variável é especificado pelo nome de variável, então o rastreamento para a variável dentro da atividade sendo controlada e em atividades pai. A variável é procurada no escopo da atividade atual e o escopo pai.  
  
-   Se as variáveis a ser extraídos são especificadas usando o nome = "*", em seguida, todas as variáveis dentro da atividade atual que está sendo controlado são extraídas. Variáveis que estão no escopo mas são definidos em atividades pai não são extraídos nesse caso.  
  
 Para extrair argumentos, os argumentos extraídos dependem de estado da atividade. Quando o estado de uma atividade é executado, então somente `InArguments` está disponível para a extração. Para qualquer outro estado da atividade (zipado, criticado, cancelado), todos os argumentos, InArguments e OutArguments, estão disponíveis para a extração.  
  
 O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida. Variáveis e os argumentos podem ser extraídos somente com <xref:System.Activities.Tracking.ActivityStateRecord> e são assinados bem em um perfil de rastreamento usando <xref:System.Activities.Tracking.ActivityStateQuery>.  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>Informações de proteção armazenada em variáveis e os argumentos  
 Uma variável ou um argumento controlado por padrão são feitas visível no tempo de execução de WF. Um desenvolvedor de fluxo de trabalho de protegê-lo pode ser acessado colocando as seguintes etapas:  
  
1.  Criptografar o valor de uma variável.  
  
2.  Controle a criação de um perfil de rastreamento para evitar a extração de uma variável ou um argumento.  
  
3.  Para participantes personalizados de rastreamento certifique-se de que o código de WF não divulgue informações sigilosas que é armazenada em variáveis ou nos argumentos.  
  
## <a name="see-also"></a>Consulte também  
 [Monitoramento do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitoramento de aplicativos com a malha de aplicativos](https://go.microsoft.com/fwlink/?LinkId=201275)
