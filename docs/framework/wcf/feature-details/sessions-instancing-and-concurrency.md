---
title: Sessões,instanciação e simultaneidade
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: b8c0b40ca67de92f4f1b481298a8a26d96e887d4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976085"
---
# <a name="sessions-instancing-and-concurrency"></a>Sessões,instanciação e simultaneidade
Uma *sessão* é uma correlação de todas as mensagens enviadas entre dois pontos de extremidade. A *instanciação* refere-se ao controle do tempo de vida de objetos de serviço definidos pelo usuário e seus objetos <xref:System.ServiceModel.InstanceContext> relacionados. *Simultaneidade* é o termo dado ao controle do número de threads em execução em um <xref:System.ServiceModel.InstanceContext> ao mesmo tempo.  
  
 Este tópico descreve essas configurações, como usá-las e as várias interações entre elas.  
  
## <a name="sessions"></a>Sessões  
 Quando um contrato de serviço define a propriedade <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> como <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, esse contrato diz que todas as chamadas (ou seja, as trocas de mensagens subjacentes que dão suporte às chamadas) devem fazer parte da mesma conversa. Se um contrato especifica que ele permite sessões, mas não requer uma, os clientes podem se conectar e estabelecer uma sessão ou não. Se a sessão terminar e uma mensagem for enviada pelo mesmo canal baseado em sessão, uma exceção será lançada.  
  
 As sessões do WCF têm os seguintes recursos conceituais principais:  
  
- Elas são explicitamente iniciadas e terminadas pelo aplicativo de chamada.  
  
- As mensagens entregues durante uma sessão são processadas na ordem em que são recebidas.  
  
- As sessões correlacionam um grupo de mensagens em uma conversa. O significado dessa correlação é uma abstração. Por exemplo, um canal baseado em sessão pode correlacionar mensagens com base em uma conexão de rede compartilhada enquanto outro canal baseado em sessão pode correlacionar mensagens com base em uma marca compartilhada no corpo da mensagem. Os recursos que podem ser derivados da sessão dependem da natureza da correlação.  
  
- Não há nenhum repositório de dados geral associado a uma sessão WCF.  
  
 Se você estiver familiarizado com a classe <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> em aplicativos ASP.NET e a funcionalidade que ele fornece, você poderá observar as seguintes diferenças entre esse tipo de sessão e sessões do WCF:  
  
- As sessões ASP.NET são sempre iniciadas pelo servidor.  
  
- As sessões ASP.NET são implicitamente desordenadas.  
  
- As sessões ASP.NET fornecem um mecanismo de armazenamento de dados geral entre solicitações.  
  
 Aplicativos cliente e aplicativos de serviço interagem com sessões de maneiras diferentes. Os aplicativos cliente iniciam sessões e recebem e processam as mensagens enviadas dentro da sessão. Os aplicativos de serviço podem usar sessões como um ponto de extensibilidade para adicionar um comportamento adicional. Isso é feito trabalhando diretamente com o <xref:System.ServiceModel.InstanceContext> ou implementando um provedor de contexto de instância personalizado.  
  
## <a name="instancing"></a>Instanciação  
 O comportamento de instanciação (definido usando a propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType>) controla como o <xref:System.ServiceModel.InstanceContext> é criado em resposta a mensagens de entrada. Por padrão, cada <xref:System.ServiceModel.InstanceContext> é associada a um objeto de serviço definido pelo usuário, portanto (no caso padrão) definir a propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> também controla a instanciação de objetos de serviço definidos pelo usuário. A enumeração <xref:System.ServiceModel.InstanceContextMode> define os modos de instanciação.  
  
 Os seguintes modos de instanciação estão disponíveis:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: um novo <xref:System.ServiceModel.InstanceContext> (e, portanto, objeto de serviço) é criado para cada solicitação do cliente.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: um novo <xref:System.ServiceModel.InstanceContext> (e, portanto, objeto de serviço) é criado para cada nova sessão de cliente e mantido durante o tempo de vida dessa sessão (isso requer uma ligação que dê suporte a sessões).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: um único <xref:System.ServiceModel.InstanceContext> (e, portanto, o objeto de serviço) trata todas as solicitações do cliente durante o tempo de vida do aplicativo.  
  
 O exemplo de código a seguir mostra o valor de <xref:System.ServiceModel.InstanceContextMode> padrão <xref:System.ServiceModel.InstanceContextMode.PerSession> ser explicitamente definido em uma classe de serviço.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 E, embora a propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> controle com que frequência a <xref:System.ServiceModel.InstanceContext> é liberada, as propriedades <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> são controladas quando o objeto de serviço é liberado.  
  
### <a name="well-known-singleton-services"></a>Serviços singleton conhecidos  
 Às vezes, uma variação em objetos de serviço de instância única é útil: você pode criar um objeto de serviço por conta própria e criar o host de serviço usando esse objeto. Para fazer isso, você também deve definir a propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> como <xref:System.ServiceModel.InstanceContextMode.Single> ou uma exceção é lançada quando o host de serviço é aberto.  
  
 Use o Construtor <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> para criar um serviço desse tipo. Ele fornece uma alternativa à implementação de um <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> personalizado quando você deseja fornecer uma instância de objeto específica para uso por um serviço singleton. Você pode usar essa sobrecarga quando o tipo de implementação de serviço for difícil de construir (por exemplo, se ele não implementar um construtor público sem parâmetros).  
  
 Observe que, quando um objeto é fornecido a esse construtor, alguns recursos relacionados ao comportamento de instanciação do Windows Communication Foundation (WCF) funcionam de maneira diferente. Por exemplo, chamar <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> não tem efeito quando uma instância de objeto singleton é fornecida. Da mesma forma, qualquer outro mecanismo de liberação de instância é ignorado. O <xref:System.ServiceModel.ServiceHost> sempre se comporta como se a propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> estiver definida como <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> para todas as operações.  
  
### <a name="sharing-instancecontext-objects"></a>Compartilhando objetos InstanceContext  
 Você também pode controlar qual canal ou chamada de sessão está associado a qual <xref:System.ServiceModel.InstanceContext> objeto executando a associação por conta própria.  
  
## <a name="concurrency"></a>Concorrência  
 A simultaneidade é o controle do número de threads ativos em um <xref:System.ServiceModel.InstanceContext> a qualquer momento. Isso é controlado usando o <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> com a enumeração <xref:System.ServiceModel.ConcurrencyMode>.  
  
 Os três modos de simultaneidade a seguir estão disponíveis:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: cada contexto de instância tem permissão para ter um máximo de um thread processando mensagens no contexto de instância por vez. Outros threads que desejam usar o mesmo contexto de instância devem ser bloqueados até que o thread original saia do contexto da instância.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: cada instância de serviço pode ter vários threads processando mensagens simultaneamente. A implementação do serviço deve ser thread-safe para usar esse modo de simultaneidade.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: cada instância de serviço processa uma mensagem por vez, mas aceita chamadas de operação reentrante. O serviço só aceita essas chamadas quando está chamando por meio de um objeto de cliente WCF.  
  
> [!NOTE]
> Compreender e desenvolver código que usa com segurança mais de um thread pode ser difícil de gravar com êxito. Antes de usar <xref:System.ServiceModel.ConcurrencyMode.Multiple> ou valores de <xref:System.ServiceModel.ConcurrencyMode.Reentrant>, verifique se o serviço foi projetado corretamente para esses modos. Para obter mais informações, consulte <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 O uso da simultaneidade está relacionado ao modo de instanciação. Em <xref:System.ServiceModel.InstanceContextMode.PerCall> instanciação, a simultaneidade não é relevante, pois cada mensagem é processada por um novo <xref:System.ServiceModel.InstanceContext> e, portanto, nunca mais de um thread está ativo no <xref:System.ServiceModel.InstanceContext>.  
  
 O exemplo de código a seguir demonstra a definição da propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> como <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sessões interagem com configurações de InstanceContext  
 As sessões e <xref:System.ServiceModel.InstanceContext> interagem dependendo da combinação do valor da enumeração <xref:System.ServiceModel.SessionMode> em um contrato e da propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> na implementação do serviço, que controla a associação entre canais e objetos de serviço específicos.  
  
 A tabela a seguir mostra o resultado de um canal de entrada que dá suporte a sessões ou não suporte a sessões, dada a combinação de um serviço dos valores da propriedade <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> e da propriedade <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType>.  
  
|Valor de InstanceContextmode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> para cada chamada.<br />-Comportamento com canal sem sessão: uma exceção é lançada.|-Comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> para cada chamada.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada chamada.|-Comportamento com o canal de sessão: uma exceção é lançada.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada chamada.|  
|PerSession|-Comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> para cada canal.<br />-Comportamento com canal sem sessão: uma exceção é lançada.|-Comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> para cada canal.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada chamada.|-Comportamento com o canal de sessão: uma exceção é lançada.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada chamada.|  
|Simples|-Comportamento com o canal de sessão: uma sessão e uma <xref:System.ServiceModel.InstanceContext> para todas as chamadas.<br />-Comportamento com canal sem sessão: uma exceção é lançada.|-Comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> para o singleton criado ou especificado pelo usuário.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para o singleton criado ou especificado pelo usuário.|-Comportamento com o canal de sessão: uma exceção é lançada.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada singleton criado ou para o singleton especificado pelo usuário.|  
  
## <a name="see-also"></a>Consulte também

- [Usando sessões](../../../../docs/framework/wcf/using-sessions.md)
- [Como criar um serviço que requer sessões](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Como controlar instanciação de serviço](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Simultaneidade](../../../../docs/framework/wcf/samples/concurrency.md)
- [Instanciação](../../../../docs/framework/wcf/samples/instancing.md)
- [Sessão](../../../../docs/framework/wcf/samples/session.md)
