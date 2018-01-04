---
title: "Critérios de localização personalizados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b57a9535b34441a8f1c86beeffa94046cf8944f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-find-criteria"></a>Critérios de localização personalizados
Este exemplo demonstra como criar uma correspondência de escopo personalizado usando a lógica e como implementar um serviço de descoberta personalizado. Os clientes usam a funcionalidade de correspondência de escopo personalizado para refinar e tê ainda mais a funcionalidade de localização fornecida pelo sistema de descoberta do WCF. O cenário que abrange a este exemplo é o seguinte:  
  
1.  Um cliente está procurando por um serviço de cálculo.  
  
2.  Para refinar sua pesquisa, o cliente deve usar um regra de correspondência de escopo personalizado.  
  
3.  Acordo com esta regra, um serviço responde ao cliente se o seu ponto de extremidade corresponde a qualquer um dos escopos especificados pelo cliente.  
  
## <a name="demonstrates"></a>Demonstra  
  
-   Criando um serviço de descoberta personalizado.  
  
-   Implementando uma correspondência de escopo personalizado pelo algoritmo.  
  
## <a name="discussion"></a>Discussão  
 O cliente está procurando por tipo de "Ou" critérios de correspondência. Um serviço responde novamente se os escopos em seus pontos de extremidade correspondem a nenhum dos escopos fornecidos pelo cliente. Nesse caso, o cliente está procurando por um serviço de cálculo que tenha qualquer um dos escopos da lista a seguir:  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Para fazer isso, o cliente direciona os serviços para usar um regra de correspondência, passando uma correspondência de escopo personalizado pelo URI de escopo personalizado. Para facilitar a correspondência de escopo personalizado, o serviço deve usar um serviço de detecção personalizada que compreende a regra de correspondência de escopo personalizado e implementa a lógica de correspondência associada.  
  
 No projeto do cliente, abra o arquivo Program.cs. Observe que o `ScopeMatchBy` campo o `FindCriteria` objeto é definido como um URI específico. Esse identificador é enviado para o serviço. Se o serviço não entender a essa regra, ele ignora a solicitação do cliente localizar.  
  
 Abra o projeto de serviço. Três arquivos são usados para implementar o serviço de detecção personalizada:  
  
1.  **AsyncResult.cs**: esta é a implementação do `AsyncResult` que é exigido pelos métodos de descoberta.  
  
2.  **CustomDiscoveryService.cs**: este arquivo implementa o serviço de descoberta personalizado. A implementação estende o <xref:System.ServiceModel.Discovery.DiscoveryService> classe e substitui os métodos necessários. Observe a implementação de <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> método. O método verifica se a correspondência de escopo personalizado pela regra foi especificada pelo cliente. Este é o mesmo URI personalizado que o cliente especificado anteriormente. Se a regra personalizada for especificada, o caminho do código que implementa a lógica de correspondência de "OR" é seguido.  
  
     Essa lógica personalizada passa por todos os escopos em cada um dos pontos de extremidade que tem o serviço. Se qualquer um dos escopos do ponto de extremidade corresponder a qualquer um dos escopos fornecidos pelo cliente, o serviço de descoberta adiciona o ponto de extremidade para a resposta que é enviada de volta ao cliente.  
  
3.  **CustomDiscoveryExtension.cs**: é a última etapa na implementação do serviço de descoberta para se conectar a esta implementação personalizado descobrir o serviço para o host de serviço. A classe auxiliar usada aqui é o `CustomDiscoveryExtension` classe. Essa classe estende a <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> classe. O usuário deve substituir o <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> método. Nesse caso, o método retorna uma instância do serviço de descoberta personalizado que foi criado antes. `PublishedEndpoints`é um <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> que contém todos os pontos de extremidade de aplicativo que são adicionados para o <xref:System.ServiceModel.ServiceHost>. O serviço de descoberta personalizado usa isso para preencher sua lista interna. Um usuário pode para adicionar outros metadados do ponto de extremidade também.  
  
 Por fim, abra Program.cs. Observe que tanto o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e `CustomDiscoveryExtension` são adicionados ao host. Quando isso é feito e o host tem um ponto de extremidade através da qual receber mensagens de descoberta, o aplicativo pode usar o serviço de descoberta personalizado.  
  
 Observe que o cliente é capaz de encontrar o serviço sem saber o endereço.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra a solução que contém o projeto.  
  
2.  Compile o projeto.  
  
3.  Execute o aplicativo de serviço.  
  
4.  Execute o aplicativo cliente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
