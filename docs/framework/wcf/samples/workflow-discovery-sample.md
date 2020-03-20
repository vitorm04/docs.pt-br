---
title: Exemplo de descoberta de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b3a2d88028f3854746d4e1d2fad80aae4f6be7be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143480"
---
# <a name="workflow-discovery-sample"></a>Exemplo de descoberta de fluxo de trabalho
Esta amostra demonstra como tornar um serviço de fluxo de trabalho desdescoberto e como criar uma atividade de código personalizada que busca um serviço específico.  
  
## <a name="demonstrates"></a>Demonstra  
 Descoberta encontrar uso de atividade e fluxo de trabalho  
  
## <a name="discussion"></a>Discussão  
 Na primeira parte da amostra, um serviço de fluxo de trabalho é descoberto usando a configuração. A configuração também pode ser usada para aplicar o serviço adequadamente com metadados personalizados (como escopos). No cliente, a amostra usa uma atividade de código personalizada, que usa o Discovery para procurar um serviço que corresponda a um determinado contrato. A atividade de código produz um URI, que é usado posteriormente por uma atividade de envio.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Esta amostra usa pontos finais HTTP, que devem ter ACLs de URL adequadas para executar (consulte [Configuração HTTP e HTTPS](../feature-details/configuring-http-and-https.md) para obter detalhes). A execução do seguinte comando em um prompt de comando elevado deve adicionar as ACLs apropriadas. Se o seu shell não entender o formato da variável, substitua seu Domínio e nome de usuário pelos seguintes argumentos.  
  
     **netsh http adicionar urlacl url=http://+:8000/ \\user=%DOMAIN% %UserName%**  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
