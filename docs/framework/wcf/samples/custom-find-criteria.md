---
title: Critérios de localização personalizados
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 3bafe89f5c114106eece02c41599cf485591c1cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183854"
---
# <a name="custom-find-criteria"></a>Critérios de localização personalizados
Esta amostra demonstra como criar uma correspondência de escopo personalizada usando lógica e como implementar um serviço de detecção personalizado. Os clientes usam a funcionalidade de correspondência de escopo personalizada para refinar e construir ainda mais em cima da funcionalidade de encontrar o WCF Discovery fornecido pelo sistema. O cenário que esta amostra abrange é o seguinte:  
  
1. Um cliente está procurando um serviço de calculadora.  
  
2. Para refinar sua pesquisa, o cliente deve usar uma regra de correspondência de escopo personalizada.  
  
3. De acordo com essa regra, um serviço responde ao cliente se seu ponto final corresponder a qualquer um dos escopos especificados pelo cliente.  
  
## <a name="demonstrates"></a>Demonstra  
  
- Criando um serviço de descoberta personalizado.  
  
- Implementando uma correspondência de escopo personalizada por algoritmo.  
  
## <a name="discussion"></a>Discussão  
 O cliente está procurando por critérios de correspondência do tipo "OR". Um serviço responde se os escopos em seus pontos finais corresponderem a qualquer um dos escopos fornecidos pelo cliente. Neste caso, o cliente está procurando um serviço de calculadora que tenha qualquer um dos escopos da lista a seguir:  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Para isso, o cliente direciona os serviços a usar uma regra de correspondência de escopo personalizada, passando em uma correspondência de escopo personalizada por URI. Para facilitar a correspondência de escopo personalizada, o serviço deve usar um serviço de detecção personalizado que entenda a regra de correspondência de escopo personalizada e implemente a lógica de correspondência associada.  
  
 No projeto do cliente, abra o arquivo Program.cs. Observe que `ScopeMatchBy` o `FindCriteria` campo do objeto está definido como um URI específico. Este identificador é enviado para o serviço. Se o serviço não entende essa regra, ele ignora a solicitação de achado do cliente.  
  
 Abra o projeto de serviço. Três arquivos são usados para implementar o Serviço de Detecção Personalizada:  
  
1. **AsyncResult.cs**: Esta é `AsyncResult` a implementação do que é exigido pelos métodos Discovery.  
  
2. **CustomDiscoveryService.cs**: Este arquivo implementa o serviço de detecção personalizado. A implementação <xref:System.ServiceModel.Discovery.DiscoveryService> amplia a classe e substitui os métodos necessários. Observe a implementação do <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> método. O método verifica se a correspondência de escopo personalizado por regra foi especificada pelo cliente. Este é o mesmo URI personalizado que o cliente especificou anteriormente. Se a regra personalizada for especificada, o caminho de código que implementa a lógica de correspondência "OR" será seguido.  
  
     Essa lógica personalizada passa por todos os escopos em cada um dos pontos finais que o serviço possui. Se algum dos escopos do ponto final corresponder a qualquer um dos escopos fornecidos pelo cliente, o serviço de descoberta adiciona esse ponto final à resposta enviada de volta ao cliente.  
  
3. **CustomDiscoveryExtension.cs**: O último passo na implementação do serviço de descoberta é conectar essa implementação do serviço de descoberta personalizada ao host de serviço. A classe de ajudantes `CustomDiscoveryExtension` usada aqui é a classe. Essa aula <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> estende a aula. O usuário deve <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> substituir o método. Neste caso, o método retorna uma instância do serviço de detecção personalizado que foi criado antes. `PublishedEndpoints`é <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> um que contém todos os pontos finais <xref:System.ServiceModel.ServiceHost>do aplicativo que são adicionados ao . O serviço de detecção personalizado usa isso para preencher sua lista interna. Um usuário pode adicionar outros metadados de ponto final também.  
  
 Por último, abra Program.cs. Observe que <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> tanto `CustomDiscoveryExtension` o e são adicionados ao host. Uma vez feito isso e o host tem um ponto final sobre o qual receber mensagens de descoberta, o aplicativo pode usar o serviço de detecção personalizado.  
  
 Observe que o cliente é capaz de encontrar o serviço sem saber seu endereço.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Abra a solução que contém o projeto.  
  
2. Compile o projeto.  
  
3. Execute o aplicativo de serviço.  
  
4. Execute o aplicativo cliente.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
