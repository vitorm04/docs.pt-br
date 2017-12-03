---
title: "Sessões,instanciação e simultaneidade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 44aebb701eb7222773c030994fbaa9c0109dce70
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="sessions-instancing-and-concurrency"></a>Sessões,instanciação e simultaneidade
Um *sessão* é uma correlação de todas as mensagens enviadas entre dois pontos de extremidade. *Instanciação* refere-se para controlar o tempo de vida de objetos de serviço definido pelo usuário e seus relacionados <xref:System.ServiceModel.InstanceContext> objetos. *Simultaneidade* é o termo dado ao controle do número de threads em execução em um <xref:System.ServiceModel.InstanceContext> ao mesmo tempo.  
  
 Este tópico descreve essas configurações, como usam e as várias interações entre eles.  
  
## <a name="sessions"></a>Sessões  
 Quando um contrato de serviço define o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, esse contrato é dizer que todas as chamadas (ou seja, as subjacente trocas de mensagens que oferecem suporte as chamadas) devem ser parte da mesma conversa. Se um contrato especifica que ele permite que as sessões, mas não exige um, os clientes podem se conectar e a estabelecer uma sessão ou não. Se a sessão é encerrada e uma mensagem é enviada pelo mesmo baseadas em sessão canal uma exceção é gerada.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]as sessões têm os seguintes recursos conceituais principais:  
  
-   Eles são explicitamente iniciados e finalizados pelo aplicativo de chamada.  
  
-   Mensagens entregues durante uma sessão são processadas na ordem em que são recebidos.  
  
-   Sessões de correlação um grupo de mensagens em uma conversa. O significado da correlação de que é uma abstração. Por exemplo, um canal de sessão pode correlacionar as mensagens com base em uma conexão de rede compartilhada enquanto outro canal baseadas em sessão pode correlacionar as mensagens com base em uma marca compartilhada no corpo da mensagem. Os recursos que podem ser derivados da sessão dependem da natureza da correlação.  
  
-   Há um repositório de dados gerais associado com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessão.  
  
 Se você estiver familiarizado com o <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> classe em [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativos e a funcionalidade que ela fornece, você observará as seguintes diferenças entre esse tipo de sessão e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessões:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]as sessões são sempre iniciadas pelo servidor.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]as sessões são implicitamente não ordenadas.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]sessões fornecem um mecanismo de armazenamento de dados gerais em solicitações.  
  
 Aplicativos cliente e aplicativos de serviço interagem com sessões de maneiras diferentes. Aplicativos cliente iniciam sessões e, em seguida, recebem e processam as mensagens enviadas na sessão. Aplicativos de serviço podem usar sessões como um ponto de extensibilidade para adicionar outro comportamento. Isso é feito ao trabalhar diretamente com o <xref:System.ServiceModel.InstanceContext> ou implementando um provedor de contexto de instância personalizada.  
  
## <a name="instancing"></a>Instanciação  
 O comportamento de instância (definido por meio de <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade) controles como o <xref:System.ServiceModel.InstanceContext> é criada em resposta a mensagens de entrada. Por padrão, cada <xref:System.ServiceModel.InstanceContext> está associado um objeto de serviço definido pelo usuário, configuração caso (no caso padrão) o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade também controla a instanciação de objetos de serviço definido pelo usuário. O <xref:System.ServiceModel.InstanceContextMode> enumeração define os modos de instância.  
  
 Os seguintes modos de instância estão disponíveis:  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>: Um novo <xref:System.ServiceModel.InstanceContext> (e, portanto, o objeto de serviço) é criado para cada solicitação de cliente.  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>: Um novo <xref:System.ServiceModel.InstanceContext> (e, portanto, o objeto de serviço) é criado para cada nova sessão de cliente e mantido pela duração da sessão (Isso requer uma associação que dá suporte a sessões).  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>: Um único <xref:System.ServiceModel.InstanceContext> (e, portanto, o objeto de serviço) trata todas as solicitações de cliente para o tempo de vida do aplicativo.  
  
 O exemplo de código a seguir mostra o padrão <xref:System.ServiceModel.InstanceContextMode> valor, <xref:System.ServiceModel.InstanceContextMode.PerSession> seja explicitamente definida em uma classe de serviço.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 E enquanto o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade controla com que frequência o <xref:System.ServiceModel.InstanceContext> for lançada, o <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> propriedades que controlam quando o objeto de serviço é liberado.  
  
### <a name="well-known-singleton-services"></a>Serviços de Singleton conhecido  
 Uma variação em objetos de única instância de serviço às vezes é útil: você pode criar um objeto de serviço por conta própria e crie o host de serviço usando o objeto. Para fazer isso, você também deve definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade <xref:System.ServiceModel.InstanceContextMode.Single> ou uma exceção é lançada quando o host de serviço é aberto.  
  
 Use o <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> construtor para criar um serviço. Ele fornece uma alternativa à implementação de uma <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> quando você deseja fornecer uma instância de objeto específico para uso por um serviço de singleton. Você pode usar essa sobrecarga ao seu tipo de implementação de serviço é difícil construir (por exemplo, se ele não implementa um construtor público padrão sem parâmetros).  
  
 Observe que quando um objeto é fornecido para esse construtor, alguns recursos relacionados a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] instância trabalho comportamento diferente. Por exemplo, chamar <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> não tem nenhum efeito quando uma instância do objeto singleton é fornecida. Da mesma forma, qualquer outro mecanismo de versão de instância é ignorado. O <xref:System.ServiceModel.ServiceHost> sempre se comporta como se o <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> está definida como <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> para todas as operações.  
  
### <a name="sharing-instancecontext-objects"></a>Compartilhamento InstanceContext objetos  
 Você também pode controlar qual canal de sessão ou chamada está associada com a qual <xref:System.ServiceModel.InstanceContext> objeto executando essa associação por conta própria.  
  
## <a name="concurrency"></a>Concorrência  
 Simultaneidade é o controle do número de threads ativos em um <xref:System.ServiceModel.InstanceContext> a qualquer momento. Isso é controlado usando o <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> com o <xref:System.ServiceModel.ConcurrencyMode> enumeração.  
  
 Os três modos de simultaneidade a seguir estão disponíveis:  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Single>: Contexto cada instância tem permissão para ter um máximo de um thread de processamento de mensagens no contexto de instância por vez. Outros threads que deseja usar o mesmo contexto de instância devem bloquear até que o thread original será encerrado o contexto da instância.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Cada instância de serviço pode ter vários threads que processam mensagens simultaneamente. A implementação do serviço deve ser thread-safe para usar o modo de simultaneidade.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Cada instância de serviço processa uma mensagem por vez, mas aceita chamadas reentrantes operação. O serviço aceita somente essas chamadas quando ela é chamada por meio de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objeto cliente.  
  
> [!NOTE]
>  Entendendo e desenvolvimento de código com segurança usa mais de um thread podem ser difícil de escrever com êxito. Antes de usar <xref:System.ServiceModel.ConcurrencyMode.Multiple> ou <xref:System.ServiceModel.ConcurrencyMode.Reentrant> valores, certifique-se de que seu serviço corretamente é criado para esses modos. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 O uso de simultaneidade está relacionado ao modo de instanciamento. Em <xref:System.ServiceModel.InstanceContextMode.PerCall> instanciamento, simultaneidade não é relevante, porque cada mensagem é processada por um novo <xref:System.ServiceModel.InstanceContext> e, portanto, nunca mais de um thread está ativo no <xref:System.ServiceModel.InstanceContext>.  
  
 O exemplo de código a seguir mostra a configuração de <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> propriedade <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sessões de interagem com as configurações do InstanceContext  
 Sessões e <xref:System.ServiceModel.InstanceContext> interagir de acordo com a combinação do valor da <xref:System.ServiceModel.SessionMode> enumeração em um contrato e o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade sobre a implementação de serviço, que controla a associação entre específicas e canais objetos de serviço.  
  
 A tabela a seguir mostra o resultado de um canal de entrada o suporte a sessões ou não suportar sessões a combinação dos valores de um serviço dada a <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade e o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade.  
  
|Valor InstanceContextMode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Um comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> para cada chamada.<br />-Comportamento com canal sem sessão: uma exceção será lançada.|-Um comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> para cada chamada.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada chamada.|-Um comportamento com o canal de sessão: uma exceção será lançada.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada chamada.|  
|PerSession|-Um comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> de cada canal.<br />-Comportamento com canal sem sessão: uma exceção será lançada.|-Um comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> de cada canal.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada chamada.|-Um comportamento com o canal de sessão: uma exceção será lançada.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada chamada.|  
|Simples|-Um comportamento com o canal de sessão: uma sessão e um <xref:System.ServiceModel.InstanceContext> para todas as chamadas.<br />-Comportamento com canal sem sessão: uma exceção será lançada.|-Um comportamento com o canal de sessão: uma sessão e <xref:System.ServiceModel.InstanceContext> para o singleton criado ou usuário especificado.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para o singleton criado ou usuário especificado.|-Um comportamento com o canal de sessão: uma exceção será lançada.<br />-Comportamento com canal sem sessão: um <xref:System.ServiceModel.InstanceContext> para cada singleton criado ou para o singleton especificado pelo usuário.|  
  
## <a name="see-also"></a>Consulte também  
 [Using Sessions](../../../../docs/framework/wcf/using-sessions.md) (Usando sessões)  
 [Como: criar um serviço que requer sessões](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)  
 [Como: controlar instanciação de serviço](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)  
 [Simultaneidade](../../../../docs/framework/wcf/samples/concurrency.md)  
 [Criação de instância](../../../../docs/framework/wcf/samples/instancing.md)  
 [Sessão](../../../../docs/framework/wcf/samples/session.md)
