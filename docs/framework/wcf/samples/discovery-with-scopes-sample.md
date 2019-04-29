---
title: Exemplos de descoberta com escopos
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 9ad20e63e00464ed615620b9d0ec83fb90d07444
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789370"
---
# <a name="discovery-with-scopes-sample"></a>Exemplos de descoberta com escopos
Este exemplo mostra como usar escopos para categorizar os pontos de extremidade podem ser descobertos como bem como usar <xref:System.ServiceModel.Discovery.DiscoveryClient> para executar uma pesquisa assíncrona para pontos de extremidade. No serviço, este exemplo mostra como personalizar a descoberta para cada ponto de extremidade, adicionando um comportamento de ponto de extremidade de descoberta e usá-lo para adicionar um escopo para o ponto de extremidade bem como controlar a capacidade de descoberta do ponto de extremidade. No cliente, a amostra passa sobre como os clientes podem criar uma <xref:System.ServiceModel.Discovery.DiscoveryClient> e ajustar parâmetros incluir escopos adicionando escopos de pesquisa a <xref:System.ServiceModel.Discovery.FindCriteria>. Este exemplo também mostra como os clientes podem restringir as respostas com a adição de um critério de término.  
  
## <a name="service-features"></a>Recursos do serviço  
 Este projeto mostra dois pontos de extremidade de serviço que está sendo adicionados a um <xref:System.ServiceModel.ServiceHost>. Cada ponto de extremidade tem um <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> associados a ele. Esse comportamento é usado para adicionar escopos URI para os pontos de extremidade. Escopos são usados para distinguir cada um desses pontos de extremidade para que os clientes podem ajustar a pesquisa. Para o segundo ponto de extremidade, a capacidade de descoberta pode ser desabilitada definindo a <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> propriedade para `false`. Isso garante que os metadados de descoberta associados a esse ponto de extremidade não será enviado como parte de todas as mensagens de descoberta.  
  
## <a name="client-features"></a>Recursos do cliente  
 O `FindCalculatorServiceAddress()` método mostra como usar um <xref:System.ServiceModel.Discovery.DiscoveryClient> e passe um <xref:System.ServiceModel.Discovery.FindCriteria> com duas restrições. Um escopo é adicionado aos critérios e o <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> estiver definida como 1. O escopo limita os resultados para somente os serviços que publicam o mesmo escopo. Definindo <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> como 1 limita as respostas a <xref:System.ServiceModel.Discovery.DiscoveryClient> aguarda para, no máximo, 1 ponto de extremidade. O <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> chamada é uma operação síncrona que bloqueia o thread até que um tempo limite for atingido ou um ponto de extremidade for encontrado.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1. Este exemplo usa pontos de extremidade HTTP e para executar este exemplo, o URL apropriado ACLs deve ser adicionado. Ver [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes. Executando o seguinte comando para um nível de privilégio elevado deve adicionar as ACLs apropriado. Você talvez queira substituir o seu domínio e nome de usuário para os argumentos a seguir, se o comando não funcionar conforme é: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Compile a solução.  
  
3. Execute o executável do serviço de diretório de compilação.  
  
4. Execute o executável do cliente. Observe que o cliente é capaz de localizar o serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
