---
title: Sessões,instanciação e simultaneidade
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 994b95bb8ebc14a9997e1e9510389fdf16098d12
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229063"
---
# <a name="sessions-instancing-and-concurrency"></a>Sessões,instanciação e simultaneidade
Um *sessão* é uma correlação de todas as mensagens enviadas entre dois pontos de extremidade. *Instanciação* refere-se para controlar o tempo de vida de objetos de serviço definido pelo usuário e seus relacionados <xref:System.ServiceModel.InstanceContext> objetos. *Simultaneidade* é o termo dado ao controle do número de threads em execução em um <xref:System.ServiceModel.InstanceContext> ao mesmo tempo.  
  
 Este tópico descreve essas configurações, como usá-los e as várias interações entre eles.  
  
## <a name="sessions"></a>Sessões  
 Quando um contrato de serviço define a <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade para <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, esse contrato está dizendo que todas as chamadas (ou seja, as subjacente trocas de mensagens que oferecem suporte as chamadas) devem ser parte da mesma conversa. Se um contrato especifica que ele permite que as sessões, mas não exige um, os clientes podem se conectar e a estabelecer uma sessão ou não. Se a sessão termina e uma mensagem é enviada sobre o mesmo com base em sessão canal uma exceção é lançada.  
  
 As sessões WCF têm os seguintes recursos de conceituais principais:  
  
-   Eles são explicitamente iniciados e encerrados pelo aplicativo de chamada.  
  
-   Mensagens entregues durante uma sessão são processadas na ordem em que elas são recebidas.  
  
-   Sessões de correlação um grupo de mensagens em uma conversa. O significado dessa correlação é uma abstração. Por exemplo, um canal com base em sessão pode correlacionar mensagens com base em uma conexão de rede compartilhado, enquanto outro canal com base em sessão pode correlacionar mensagens com base em uma marca compartilhada no corpo da mensagem. Os recursos que podem ser derivados da sessão dependem da natureza da correlação.  
  
-   Não há nenhum armazenamento de dados gerais associado com uma sessão do WCF.  
  
 Se você estiver familiarizado com o <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> classe [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativos e a funcionalidade que ele fornece, você pode observar as seguintes diferenças entre esse tipo de sessão e as sessões WCF:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] as sessões são sempre iniciadas pelo servidor.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] as sessões são implicitamente não ordenadas.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] as sessões fornecem um mecanismo de armazenamento de dados geral em todas as solicitações.  
  
 Aplicativos cliente e aplicativos de serviço interagem com sessões de maneiras diferentes. Aplicativos cliente iniciam as sessões e, em seguida, recebem e processam as mensagens enviadas dentro da sessão. Aplicativos de serviço podem usar sessões como um ponto de extensibilidade para adicionar um comportamento adicional. Isso é feito ao trabalhar diretamente com o <xref:System.ServiceModel.InstanceContext> ou implementando um provedor de contexto personalizado de instância.  
  
## <a name="instancing"></a>Instanciação  
 O comportamento de instanciação (definido usando o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade) controles como o <xref:System.ServiceModel.InstanceContext> é criada em resposta às mensagens de entrada. Por padrão, cada <xref:System.ServiceModel.InstanceContext> está associado um objeto de serviço definido pelo usuário, então (no caso padrão) configuração de <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade também controla a instanciação de objetos de serviço definido pelo usuário. O <xref:System.ServiceModel.InstanceContextMode> enumeração define os modos de instanciação.  
  
 Modos de instanciação a seguir estão disponíveis:  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>: Um novo <xref:System.ServiceModel.InstanceContext> (e, portanto, o objeto de serviço) é criado para cada solicitação de cliente.  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>: Um novo <xref:System.ServiceModel.InstanceContext> (e, portanto, o objeto de serviço) é criado para cada nova sessão de cliente e mantido pelo tempo de vida da sessão em questão (Isso requer uma associação que dá suporte a sessões).  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>: Um único <xref:System.ServiceModel.InstanceContext> (e, portanto, o objeto de serviço) lida com todas as solicitações de cliente para o tempo de vida do aplicativo.  
  
 O exemplo de código a seguir mostra o padrão <xref:System.ServiceModel.InstanceContextMode> valor, <xref:System.ServiceModel.InstanceContextMode.PerSession> explicitamente que está sendo definida em uma classe de serviço.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 E enquanto o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade controla a frequência com que o <xref:System.ServiceModel.InstanceContext> é liberado, o <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> propriedades controlam quando o objeto de serviço é liberado.  
  
### <a name="well-known-singleton-services"></a>Serviços Singleton conhecido  
 Uma variação em objetos de única instância de serviço às vezes é útil: você pode criar um objeto de serviço por conta própria e criar o host de serviço usando esse objeto. Para fazer isso, você também deve definir a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade para <xref:System.ServiceModel.InstanceContextMode.Single> ou uma exceção é lançada quando o host de serviço é aberto.  
  
 Use o <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> construtor para criar esse tipo de serviço. Ele fornece uma alternativa à implementação de uma <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> quando você deseja fornecer uma instância de objeto específico para uso por um serviço singleton. Você pode usar essa sobrecarga ao seu tipo de implementação de serviço é difícil construir (por exemplo, se ele não implementa um construtor público padrão sem parâmetros).  
  
 Observe que quando um objeto é fornecido para esse construtor, alguns recursos relacionados para o Windows Communication Foundation (WCF) comportamento de instanciação funcionam de forma diferente. Por exemplo, chamar <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> não tem nenhum efeito quando uma instância do objeto de singleton é fornecida. Da mesma forma, qualquer outro mecanismo de versão da instância é ignorado. O <xref:System.ServiceModel.ServiceHost> sempre se comporta como se o <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> estiver definida como <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> para todas as operações.  
  
### <a name="sharing-instancecontext-objects"></a>Compartilhando objetos InstanceContext  
 Você também pode controlar qual canal de sessão ou chamada está associada com a qual <xref:System.ServiceModel.InstanceContext> objeto executando essa associação por conta própria.  
  
## <a name="concurrency"></a>Concorrência  
 Simultaneidade é o controle do número de threads ativos em um <xref:System.ServiceModel.InstanceContext> a qualquer momento. Isso é controlado usando o <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> com o <xref:System.ServiceModel.ConcurrencyMode> enumeração.  
  
 Os três modos de simultaneidade a seguir estão disponíveis:  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Single>: Cada contexto de instância tem permissão para ter um máximo de um thread de processamento de mensagens no contexto de instância por vez. Outros threads que queiram usar o mesmo contexto de instância devem bloquear até que o thread original será encerrado o contexto da instância.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Cada instância de serviço pode ter vários threads de processamento de mensagens simultaneamente. A implementação do serviço deve ser thread-safe para usar esse modo de simultaneidade.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Cada instância de serviço processa uma mensagem por vez, mas aceita chamadas reentrantes de operação. O serviço aceita somente essas chamadas quando ela é chamada por meio de um objeto de cliente do WCF.  
  
> [!NOTE]
>  Entender e desenvolver o código que usa com segurança a mais de um thread podem ser difícil de escrever com êxito. Antes de usar <xref:System.ServiceModel.ConcurrencyMode.Multiple> ou <xref:System.ServiceModel.ConcurrencyMode.Reentrant> valores, certifique-se de que seu serviço está corretamente projetado para esses modos. Para obter mais informações, consulte <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 O uso de simultaneidade está relacionado ao modo de instanciação. Na <xref:System.ServiceModel.InstanceContextMode.PerCall> instanciamento, simultaneidade não for relevante, porque cada mensagem é processada por um novo <xref:System.ServiceModel.InstanceContext> e, portanto, nunca mais de um thread está ativo no <xref:System.ServiceModel.InstanceContext>.  
  
 O exemplo de código a seguir demonstra a configuração de <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> propriedade para <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sessões de interagem com as configurações de InstanceContext  
 Sessões e <xref:System.ServiceModel.InstanceContext> interagir de acordo com a combinação do valor da <xref:System.ServiceModel.SessionMode> enumeração em um contrato e o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade sobre a implementação de serviço, que controla a associação entre canais e específicas objetos de serviço.  
  
 A tabela a seguir mostra o resultado de um canal de entrada que dão suporte a sessões ou não dar suporte a sessões a combinação dos valores de um serviço dada a <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade e o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade.  
  
|Valor InstanceContextMode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Comportamento com o canal de sessão: Uma sessão e <xref:System.ServiceModel.InstanceContext> para cada chamada.<br />-Comportamento com canal sem sessão: Uma exceção é gerada.|-Comportamento com o canal de sessão: Uma sessão e <xref:System.ServiceModel.InstanceContext> para cada chamada.<br />-Comportamento com canal sem sessão: Um <xref:System.ServiceModel.InstanceContext> para cada chamada.|-Comportamento com o canal de sessão: Uma exceção é gerada.<br />-Comportamento com canal sem sessão: Um <xref:System.ServiceModel.InstanceContext> para cada chamada.|  
|PerSession|-Comportamento com o canal de sessão: Uma sessão e <xref:System.ServiceModel.InstanceContext> para cada canal.<br />-Comportamento com canal sem sessão: Uma exceção é gerada.|-Comportamento com o canal de sessão: Uma sessão e <xref:System.ServiceModel.InstanceContext> para cada canal.<br />-Comportamento com canal sem sessão: Um <xref:System.ServiceModel.InstanceContext> para cada chamada.|-Comportamento com o canal de sessão: Uma exceção é gerada.<br />-Comportamento com canal sem sessão: Um <xref:System.ServiceModel.InstanceContext> para cada chamada.|  
|Simples|-Comportamento com o canal de sessão: Uma sessão e um <xref:System.ServiceModel.InstanceContext> para todas as chamadas.<br />-Comportamento com canal sem sessão: Uma exceção é gerada.|-Comportamento com o canal de sessão: Uma sessão e <xref:System.ServiceModel.InstanceContext> para o singleton criado ou especificado pelo usuário.<br />-Comportamento com canal sem sessão: Um <xref:System.ServiceModel.InstanceContext> para o singleton criado ou especificado pelo usuário.|-Comportamento com o canal de sessão: Uma exceção é gerada.<br />-Comportamento com canal sem sessão: Um <xref:System.ServiceModel.InstanceContext> para cada singleton criado ou para o singleton especificado pelo usuário.|  
  
## <a name="see-also"></a>Consulte também

- [Usando sessões](../../../../docs/framework/wcf/using-sessions.md)
- [Como: Criar um serviço que requer sessões](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Como: Controlar instanciação de serviço](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Simultaneidade](../../../../docs/framework/wcf/samples/concurrency.md)
- [Instanciação](../../../../docs/framework/wcf/samples/instancing.md)
- [Sessão](../../../../docs/framework/wcf/samples/session.md)
