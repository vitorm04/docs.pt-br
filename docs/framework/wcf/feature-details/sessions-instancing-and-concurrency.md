---
title: Sessões,instanciação e simultaneidade
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: a7466d819e15f3bfe8def2d9407dcf2c6e0c7346
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184439"
---
# <a name="sessions-instancing-and-concurrency"></a>Sessões,instanciação e simultaneidade
Uma *sessão* é uma correlação de todas as mensagens enviadas entre dois pontos finais. *Instancing* refere-se ao controle da vida útil de <xref:System.ServiceModel.InstanceContext> objetos de serviço definidos pelo usuário e seus objetos relacionados. *Conmoeda* é o termo dado ao controle do número <xref:System.ServiceModel.InstanceContext> de threads executados em um ao mesmo tempo.  
  
 Este tópico descreve essas configurações, como usá-las e as várias interações entre elas.  
  
## <a name="sessions"></a>Sessões  
 Quando um contrato <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> de <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>serviço define a propriedade para , esse contrato está dizendo que todas as chamadas (ou seja, as trocas de mensagens subjacentes que suportam as chamadas) devem fazer parte da mesma conversa. Se um contrato especificar que permite sessões, mas não requer uma, os clientes podem se conectar e estabelecer uma sessão ou não. Se a sessão terminar e uma mensagem for enviada pelo mesmo canal baseado em sessão, uma exceção será lançada.  
  
 As sessões de WCF têm as seguintes características conceituais principais:  
  
- Eles são explicitamente iniciados e encerrados pelo aplicativo de chamada.  
  
- As mensagens entregues durante uma sessão são processadas na ordem em que são recebidas.  
  
- As sessões correlacionam um grupo de mensagens em uma conversa. O significado dessa correlação é uma abstração. Por exemplo, um canal baseado em sessão pode correlacionar mensagens com base em uma conexão de rede compartilhada, enquanto outro canal baseado em sessão pode correlacionar mensagens com base em uma tag compartilhada no corpo de mensagens. As características que podem ser derivadas da sessão dependem da natureza da correlação.  
  
- Não há um armazenamento geral de dados associado a uma sessão wcf.  
  
 Se você estiver <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> familiarizado com a classe em ASP.NET aplicativos e a funcionalidade que ele fornece, você pode notar as seguintes diferenças entre esse tipo de sessão e sessões de WCF:  
  
- ASP.NET sessões são sempre iniciadas pelo servidor.  
  
- ASP.NET sessões são implicitamente desordenadas.  
  
- ASP.NET sessões fornecem um mecanismo geral de armazenamento de dados entre as solicitações.  
  
 Aplicativos clientes e aplicativos de serviço interagem com as sessões de diferentes maneiras. Os aplicativos clientes iniciam sessões e, em seguida, recebem e processam as mensagens enviadas dentro da sessão. Os aplicativos de serviço podem usar as sessões como um ponto de extensibilidade para adicionar comportamento adicional. Isso é feito trabalhando <xref:System.ServiceModel.InstanceContext> diretamente com o ou implementando um provedor de contexto de instância personalizada.  
  
## <a name="instancing"></a>Instanciação  
 O comportamento de instancing <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> (definido pelo uso <xref:System.ServiceModel.InstanceContext> da propriedade) controla como o é criado em resposta às mensagens recebidas. Por padrão, <xref:System.ServiceModel.InstanceContext> cada um está associado a um objeto de serviço definido <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> pelo usuário, então (no caso padrão) a configuração da propriedade também controla a entrada de objetos de serviço definidos pelo usuário. A <xref:System.ServiceModel.InstanceContextMode> enumeração define os modos de instancing.  
  
 Os seguintes modos de instancing estão disponíveis:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Um <xref:System.ServiceModel.InstanceContext> novo objeto de serviço (e, portanto, de serviço) é criado para cada solicitação do cliente.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Um <xref:System.ServiceModel.InstanceContext> novo objeto de serviço (e, portanto, de serviço) é criado para cada nova sessão de cliente e mantido durante toda a vida dessa sessão (isso requer uma vinculação que suporte as sessões).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Um <xref:System.ServiceModel.InstanceContext> único (e, portanto, objeto de serviço) lida com todas as solicitações do cliente durante a vida útil do aplicativo.  
  
 O exemplo de código <xref:System.ServiceModel.InstanceContextMode> a <xref:System.ServiceModel.InstanceContextMode.PerSession> seguir mostra o valor padrão, sendo explicitamente definido em uma classe de serviço.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorInstance
{
    ...  
}  
```  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> E enquanto a propriedade <xref:System.ServiceModel.InstanceContext> controla a <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> frequência com que o é liberado, o controle e <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> propriedades quando o objeto de serviço é liberado.  
  
### <a name="well-known-singleton-services"></a>Serviços bem conhecidos de Singleton  
 Uma variação em objetos de serviço de instância única às vezes é útil: você pode criar um objeto de serviço sozinho e criar o host de serviço usando esse objeto. Para isso, você também deve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> definir <xref:System.ServiceModel.InstanceContextMode.Single> a propriedade para ou uma exceção é lançada quando o host de serviço é aberto.  
  
 Use <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> o construtor para criar tal serviço. Ele fornece uma alternativa para <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> implementar um personalizado quando você deseja fornecer uma instância específica de objeto para uso por um serviço singleton. Você pode usar essa sobrecarga quando seu tipo de implementação de serviço é difícil de construir (por exemplo, se ele não implementar um construtor público sem parâmetros).  
  
 Observe que quando um objeto é fornecido a este construtor, alguns recursos relacionados ao Comportamento de Instancing da Windows Communication Foundation (WCF) funcionam de forma diferente. Por exemplo, <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> a chamada não tem efeito quando uma instância de objeto singleton é fornecida. Da mesma forma, qualquer outro mecanismo de liberação de instâncias é ignorado. O <xref:System.ServiceModel.ServiceHost> sempre se comporta <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> como se <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> a propriedade estivesse definida para todas as operações.  
  
### <a name="sharing-instancecontext-objects"></a>Compartilhando objetos de contexto de instância  
 Você também pode controlar qual canal ou <xref:System.ServiceModel.InstanceContext> chamada está associado a qual objeto realizando essa associação você mesmo.  
  
## <a name="concurrency"></a>Simultaneidade  
 Conmoeda é o controle do número de <xref:System.ServiceModel.InstanceContext> threads ativos em um a qualquer momento. Isso é controlado <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> usando <xref:System.ServiceModel.ConcurrencyMode> o com a enumeração.  
  
 Os três modos de concorrência a seguir estão disponíveis:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: Cada contexto de instância é permitido ter um máximo de um segmento processando mensagens no contexto de instância de cada vez. Outros segmentos que desejam usar o mesmo contexto de instância devem ser bloqueados até que o segmento original saia do contexto de instância.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Cada instância de serviço pode ter vários threads processando mensagens simultaneamente. A implementação do serviço deve ser segura para threads para usar este modo de concorrência.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Cada instância de serviço processa uma mensagem por vez, mas aceita chamadas de operação de reentrada. O serviço só aceita essas chamadas quando está chamando através de um objeto cliente WCF.  
  
> [!NOTE]
> Entender e desenvolver códigos que usem com segurança mais de um segmento pode ser difícil de escrever com sucesso. Antes <xref:System.ServiceModel.ConcurrencyMode.Multiple> de <xref:System.ServiceModel.ConcurrencyMode.Reentrant> usar ou valorizar, certifique-se de que seu serviço foi projetado adequadamente para esses modos. Para obter mais informações, consulte <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 O uso de simultuou-se em relação ao modo de instancing. Em <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, a concorrência não é relevante, pois <xref:System.ServiceModel.InstanceContext> cada mensagem é processada por um novo <xref:System.ServiceModel.InstanceContext>e, portanto, nunca mais de um segmento está ativo no .  
  
 O exemplo de código <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a <xref:System.ServiceModel.ConcurrencyMode.Multiple>seguir demonstra a configuração da propriedade para .  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]
public class CalculatorService : ICalculatorConcurrency
{
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>As sessões interagem com as configurações do contexto de instância  
 Sessões <xref:System.ServiceModel.InstanceContext> e interagir dependendo da combinação <xref:System.ServiceModel.SessionMode> do valor da enumeração em um contrato e da <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade na implementação do serviço, que controla a associação entre canais e objetos de serviço específicos.  
  
 A tabela a seguir mostra o resultado de um canal de entrada, apoiando sessões ou não suportando sessões, dada a combinação de um serviço dos valores da <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade e da <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade.  
  
|ExemploContextoModo valor|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Percall|- Comportamento com canal de <xref:System.ServiceModel.InstanceContext> sessão: Uma sessão e para cada chamada.<br />- Comportamento com canal sem sessão: Uma exceção é lançada.|- Comportamento com canal de <xref:System.ServiceModel.InstanceContext> sessão: Uma sessão e para cada chamada.<br />- Comportamento com canal <xref:System.ServiceModel.InstanceContext> sem sessão: Um para cada chamada.|- Comportamento com canal de sessão: Uma exceção é lançada.<br />- Comportamento com canal <xref:System.ServiceModel.InstanceContext> sem sessão: Um para cada chamada.|  
|Persession|- Comportamento com canal de <xref:System.ServiceModel.InstanceContext> sessão: Uma sessão e para cada canal.<br />- Comportamento com canal sem sessão: Uma exceção é lançada.|- Comportamento com canal de <xref:System.ServiceModel.InstanceContext> sessão: Uma sessão e para cada canal.<br />- Comportamento com canal <xref:System.ServiceModel.InstanceContext> sem sessão: Um para cada chamada.|- Comportamento com canal de sessão: Uma exceção é lançada.<br />- Comportamento com canal <xref:System.ServiceModel.InstanceContext> sem sessão: Um para cada chamada.|  
|Single|- Comportamento com canal de sessão: Uma sessão e uma <xref:System.ServiceModel.InstanceContext> para todas as chamadas.<br />- Comportamento com canal sem sessão: Uma exceção é lançada.|- Comportamento com canal de <xref:System.ServiceModel.InstanceContext> sessão: Uma sessão e para o singleton criado ou especificado pelo usuário.<br />- Comportamento com canal <xref:System.ServiceModel.InstanceContext> sem sessão: Um singleton criado ou especificado pelo usuário.|- Comportamento com canal de sessão: Uma exceção é lançada.<br />- Comportamento com canal <xref:System.ServiceModel.InstanceContext> sem sessão: Um para cada singleton criado ou para o singleton especificado pelo usuário.|  
  
## <a name="see-also"></a>Confira também

- [Usando sessões](../../../../docs/framework/wcf/using-sessions.md)
- [Como criar um serviço que requer sessões](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Como controlar instanciação de serviço](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Simultaneidade](../../../../docs/framework/wcf/samples/concurrency.md)
- [Instanciação](../../../../docs/framework/wcf/samples/instancing.md)
- [Sessão](../../../../docs/framework/wcf/samples/session.md)
