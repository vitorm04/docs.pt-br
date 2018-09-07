---
title: Exemplo de descoberta de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1076e7045ca546fed7e6902f69406bfc002c4c26
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44069745"
---
# <a name="workflow-discovery-sample"></a>Exemplo de descoberta de fluxo de trabalho
Este exemplo demonstra como tornar um serviço de fluxo de trabalho detectável e como criar uma atividade de código personalizado que procura por um serviço específico.  
  
## <a name="demonstrates"></a>Demonstra  
 Atividade de descoberta de localização e o uso de fluxo de trabalho  
  
## <a name="discussion"></a>Discussão  
 Na primeira parte do exemplo, um serviço de fluxo de trabalho é feito detectável usando a configuração. Configuração também pode ser usada para aplicar o serviço adequadamente com metadados personalizados (como escopos). No cliente, o exemplo usa uma atividade de código personalizado, que usa a descoberta para pesquisar para um serviço de correspondência de um determinado contrato. A atividade de código gera um URI, que é posteriormente usado por uma atividade de envio.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Este exemplo usa pontos de extremidade HTTP, que devem ter o URL apropriado ACLs para ser executado (consulte [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes). Executando o seguinte comando em um prompt de comando elevado deve adicionar as ACLs apropriado. Substitua o seu domínio e nome de usuário para os argumentos a seguir se o seu shell não entende o formato de variável.  
  
     **Netsh http adicionar url urlacl =http://+:8000/ usuário = % domínio %\\% UserName %**  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
