---
title: Critérios de localização personalizados
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 699260fcef7680710f721d213dbf1126ebf7a896
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736212"
---
# <a name="custom-find-criteria"></a>Critérios de localização personalizados
Este exemplo demonstra como criar uma correspondência de escopo personalizado usando a lógica e como implementar um serviço de descoberta personalizada. Clientes usam a funcionalidade de correspondência de escopo personalizado para refinar e se baseiam ainda mais a funcionalidade de localização fornecidos pelo sistema de descoberta do WCF. O cenário que abrange esse exemplo é da seguinte maneira:  
  
1.  Um cliente está procurando por um serviço de calculadora.  
  
2.  Para refinar sua pesquisa, o cliente deve usar um regra de correspondência de escopo personalizado.  
  
3.  Acordo com esta regra, um serviço responde ao cliente se o seu ponto de extremidade corresponde a qualquer um dos escopos especificados pelo cliente.  
  
## <a name="demonstrates"></a>Demonstra  
  
-   Criando um serviço de descoberta personalizada.  
  
-   Implementando uma correspondência de escopo personalizado pelo algoritmo.  
  
## <a name="discussion"></a>Discussão  
 O cliente está procurando por tipo de "Ou" critérios de correspondência. Um serviço responde novamente se os escopos em seus pontos de extremidade correspondem a nenhum dos escopos fornecidos pelo cliente. Nesse caso, o cliente está procurando um serviço de calculadora que tenha qualquer um dos escopos na lista a seguir:  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Para fazer isso, o cliente direciona os serviços para usar um regra de correspondência, passando uma correspondência de escopo personalizado pelo URI de escopo personalizado. Para facilitar a correspondência de escopo personalizado, o serviço deve usar um serviço de descoberta personalizados que compreende a regra de correspondência de escopo personalizado e implementa a lógica de correspondência associada.  
  
 No projeto do cliente, abra o arquivo Program.cs. Observe que o `ScopeMatchBy` campo do `FindCriteria` objeto é definido como um URI específico. Esse identificador é enviado para o serviço. Se o serviço não entender essa regra, ele ignora a solicitação de localização do cliente.  
  
 Abra o projeto de serviço. Três arquivos são usados para implementar o serviço de descoberta personalizado:  
  
1.  **AsyncResult.cs**: esta é a implementação do `AsyncResult` que é exigido pelos métodos de descoberta.  
  
2.  **CustomDiscoveryService.cs**: esse arquivo implementa o serviço de descoberta personalizada. Estende a implementação de <xref:System.ServiceModel.Discovery.DiscoveryService> de classe e substitui os métodos necessários. Observe a implementação do <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> método. O método verifica se a correspondência de escopo personalizado pela regra foi especificada pelo cliente. Isso é o mesmo URI personalizado que o cliente especificou anteriormente. Se a regra personalizada for especificada, o caminho do código que implementa a lógica de correspondência de "Ou" será seguido.  
  
     Essa lógica personalizada passa por todos os escopos em cada um dos pontos de extremidade que tem o serviço. Se qualquer um dos escopos do ponto de extremidade corresponde a nenhum dos escopos fornecidos pelo cliente, o serviço de descoberta adiciona o ponto de extremidade à resposta que é enviada de volta ao cliente.  
  
3.  **CustomDiscoveryExtension.cs**: A última etapa na implementação do serviço de descoberta é para se conectar a essa implementação do personalizado descobrir serviço ao host de serviço. A classe auxiliar usada aqui é o `CustomDiscoveryExtension` classe. Essa classe estende a <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> classe. O usuário deve substituir o <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> método. Nesse caso, o método retorna uma instância do serviço de descoberta personalizada que foi criado antes. `PublishedEndpoints` é um <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> que contém todos os pontos de extremidade do aplicativo que são adicionados para o <xref:System.ServiceModel.ServiceHost>. O serviço de descoberta personalizado usa isso para preencher sua lista interna. Um usuário pode para adicionar outros metadados do ponto de extremidade também.  
  
 Por fim, abra Program.cs. Observe que tanto a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e `CustomDiscoveryExtension` são adicionados ao host. Depois que isso é feito e o host tem um ponto de extremidade ao longo do qual deseja receber mensagens de descoberta, o aplicativo pode usar o serviço de descoberta personalizada.  
  
 Observe que o cliente é capaz de encontrar o serviço sem saber seu endereço.  
  
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
