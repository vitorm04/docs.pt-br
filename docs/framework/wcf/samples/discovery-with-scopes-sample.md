---
title: Exemplos de descoberta com escopos
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: ee6fdb69f6417e6c43d671c7c76bda8af067d5a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502194"
---
# <a name="discovery-with-scopes-sample"></a>Exemplos de descoberta com escopos
Este exemplo mostra como usar escopos para categorizar os pontos de extremidade detectáveis como também como usar <xref:System.ServiceModel.Discovery.DiscoveryClient> para executar uma pesquisa assíncrona para pontos de extremidade. Sobre o serviço, este exemplo mostra como personalizar a descoberta para cada ponto de extremidade ao adicionar um comportamento de ponto de extremidade de descoberta e usá-lo para adicionar um escopo para o ponto de extremidade bem como controlar o uso do ponto de extremidade. No cliente, o exemplo passa sobre como os clientes podem criar um <xref:System.ServiceModel.Discovery.DiscoveryClient> e pesquisar parâmetros para incluir escopos adicionando escopos a ajustar o <xref:System.ServiceModel.Discovery.FindCriteria>. Este exemplo também mostra como os clientes podem restringir respostas adicionando um critério de encerramento.  
  
## <a name="service-features"></a>Recursos de serviço  
 Este projeto mostra dois pontos de extremidade de serviço que está sendo adicionados a um <xref:System.ServiceModel.ServiceHost>. Cada ponto de extremidade tem um <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> associados a ele. Esse comportamento é usado para adicionar os escopos URI para os pontos de extremidade. Escopos são usados para distinguir cada um desses pontos de extremidade para que os clientes podem ajustar a pesquisa. O segundo ponto de extremidade, a capacidade de descoberta pode ser desabilitada, definindo o <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> propriedade `false`. Isso garante que os metadados de detecção associado a esse ponto de extremidade não são enviados como parte de qualquer mensagem de descoberta.  
  
## <a name="client-features"></a>Recursos do cliente  
 O `FindCalculatorServiceAddress()` método mostra como usar um <xref:System.ServiceModel.Discovery.DiscoveryClient> e passar uma <xref:System.ServiceModel.Discovery.FindCriteria> com duas restrições. Um escopo é adicionado aos critérios e <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> propriedade é definida como 1. O escopo limita os resultados a apenas os serviços que publica o mesmo escopo. Configuração <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> para 1 limita as respostas a <xref:System.ServiceModel.Discovery.DiscoveryClient> aguarda para, no máximo, 1 ponto de extremidade. O <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> chamada é uma operação síncrona que bloqueia o thread até que um tempo limite for atingido ou um ponto de extremidade foi encontrado.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Este exemplo usa pontos de extremidade HTTP e para executar este exemplo, as ACLs adequadas de URL deve ser adicionado. Consulte [Configurando HTTP e HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes. Executando o seguinte comando em um privilégio elevado deve adicionar as ACLs corretas. Convém substituir seu domínio e nome de usuário para os argumentos a seguir, se o comando não funcionar conforme é: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Compile a solução.  
  
3.  Execute o executável do serviço de diretório de compilação.  
  
4.  Execute o executável do cliente. Observe que o cliente é capaz de localizar o serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
  
## <a name="see-also"></a>Consulte também
