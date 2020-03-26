---
title: Lidando com exceções e falhas
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 7fa045dc6fd6e31eccf29e22ae2e212f59dfaec0
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111862"
---
# <a name="handling-exceptions-and-faults"></a>Lidando com exceções e falhas
As exceções são usadas para comunicar erros localmente dentro do serviço ou na implementação do cliente. As falhas, por outro lado, são usadas para comunicar erros através dos limites de serviço, como do servidor para o cliente ou vice-versa. Além das falhas, os canais de transporte geralmente usam mecanismos específicos de transporte para comunicar erros no nível de transporte. Por exemplo, o transporte HTTP usa códigos de status como o 404 para comunicar uma URL de ponto final não existente (não há ponto final para enviar uma falha). Este documento consiste em três seções que fornecem orientação aos autores de canais personalizados. A primeira seção fornece orientações sobre quando e como definir e lançar exceções. A segunda seção fornece orientação sobre a geração e o consumo de falhas. A terceira seção explica como fornecer informações de rastreamento para ajudar o usuário de seu canal personalizado na solução de problemas em execução de aplicativos.  
  
## <a name="exceptions"></a>Exceções  
 Há duas coisas a ter em mente ao lançar uma exceção: Primeiro tem que ser de um tipo que permite que os usuários escrevam código correto que pode reagir adequadamente à exceção. Em segundo lugar, ele tem que fornecer informações suficientes para o usuário entender o que deu errado, o impacto da falha e como corrigi-lo. As seções a seguir dão orientações sobre tipos de exceção e mensagens para canais wcf (Windows Communication Foundation). Há também orientação geral em torno de exceções no .NET no documento Diretrizes de Design para Exceções.  
  
### <a name="exception-types"></a>Tipos de exceção  
 Todas as exceções lançadas <xref:System.TimeoutException?displayProperty=nameWithType>pelos <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>canais devem ser <xref:System.ServiceModel.CommunicationException>um , ou um tipo derivado de . (Exceções como <xref:System.ObjectDisposedException> também podem ser lançadas, mas apenas para indicar que o código de chamada usou indevidamente o canal. Se um canal for usado corretamente, ele só deve jogar as exceções dadas.) O WCF fornece sete <xref:System.ServiceModel.CommunicationException> tipos de exceção que derivam e são projetados para serem usados por canais. Existem <xref:System.ServiceModel.CommunicationException>outras exceções derivadas que são projetadas para serem usadas por outras partes do sistema. Esses tipos de exceção são:  
  
|Tipo de exceção|Significado|Conteúdo de exceção interna|Estratégia de recuperação|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|O endereço de ponto final especificado para ouvir já está em uso.|Se estiver presente, fornece mais detalhes sobre o erro de transporte que causou essa exceção. Por exemplo. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>ou <xref:System.Net.Sockets.SocketException>.|Tente um endereço diferente.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|O processo não é permitido acesso ao endereço de ponto final especificado para ouvir.|Se estiver presente, fornece mais detalhes sobre o erro de transporte que causou essa exceção. Por exemplo, <xref:System.IO.PipeException>, ou <xref:System.Net.HttpListenerException>.|Tente com credenciais diferentes.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|O <xref:System.ServiceModel.ICommunicationObject> que está sendo utilizado está no estado defeituoso (para obter mais informações, consulte [Entendendo alterações de estado](understanding-state-changes.md)). Observe que quando um objeto com várias chamadas pendentes transita para o estado com falha, apenas uma <xref:System.ServiceModel.CommunicationObjectFaultedException>chamada lança uma exceção relacionada à falha e o resto das chamadas lançam um . Essa exceção é normalmente lançada porque um aplicativo ignora alguma exceção e tenta usar um objeto já defeituoso, possivelmente em um segmento diferente daquele que pegou a exceção original.|Se presente fornecer detalhes sobre a exceção interna.|Crie um novo objeto. Observe que, dependendo <xref:System.ServiceModel.ICommunicationObject> do que causou a falha em primeiro lugar, pode haver outros trabalhos necessários para recuperar.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|O <xref:System.ServiceModel.ICommunicationObject> que está sendo utilizado foi abortado (para mais informações, consulte [Entendendo mudanças de estado](understanding-state-changes.md)). Semelhante <xref:System.ServiceModel.CommunicationObjectFaultedException>a , esta exceção <xref:System.ServiceModel.ICommunicationObject.Abort%2A> indica que o aplicativo chamou o objeto, possivelmente de outro segmento, e o objeto não é mais utilizável por esse motivo.|Se presente fornecer detalhes sobre a exceção interna.|Crie um novo objeto. Note que dependendo do <xref:System.ServiceModel.ICommunicationObject> que causou o aborto em primeiro lugar, pode haver outros trabalhos necessários para recuperar.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|O ponto final remoto do alvo não é ouvir. Isso pode resultar de qualquer parte do endereço do ponto final ser incorreta, irresolúvel ou o ponto final estar para baixo. Exemplos incluem erro de DNS, queue manager não disponível e serviço não executado.|A exceção interna fornece detalhes, tipicamente do transporte subjacente.|Tente um endereço diferente. Alternativamente, o remetente pode esperar um pouco e tentar novamente no caso de o serviço foi para baixo|  
|<xref:System.ServiceModel.ProtocolException>|Os protocolos de comunicação, como descrito pela política do ponto final, são incompatíveis entre os pontos finais. Por exemplo, enquadrar a incompatibilidade de tipo de conteúdo ou o tamanho máximo da mensagem excedido.|Se presente fornecer mais informações sobre o erro de protocolo específico. Por exemplo, <xref:System.ServiceModel.QuotaExceededException> é a exceção interna quando a causa de erro está excedendo MaxReceivedMessageSize.|Recuperação: Certifique-se de remetente e as configurações de protocolo recebidas coincidirem. Uma maneira de fazer isso é reimportar os metadados (política) do ponto final do serviço e usar a vinculação gerada para recriar o canal.|  
|<xref:System.ServiceModel.ServerTooBusyException>|O ponto final remoto é ouvir, mas não está preparado para processar mensagens.|Se estiver presente, a Exceção interna fornece os detalhes de falha soap ou de erro no nível de transporte.|Recuperação: Aguarde e tente novamente a operação mais tarde.|  
|<xref:System.TimeoutException>|A operação não foi concluída dentro do período de tempo.|Pode fornecer detalhes sobre o tempo hámenos.|Espere e tente novamente a operação mais tarde.|  
  
 Defina um novo tipo de exceção somente se esse tipo corresponder a uma estratégia de recuperação específica diferente de todos os tipos de exceção existentes. Se você definir um novo tipo de <xref:System.ServiceModel.CommunicationException> exceção, ele deve derivar de ou de uma de suas classes derivadas.  
  
### <a name="exception-messages"></a>Mensagens de Exceção  
 As mensagens de exceção são direcionadas ao usuário e não ao programa, por isso devem fornecer informações suficientes para ajudar o usuário a entender e resolver o problema. As três partes essenciais de uma boa mensagem de exceção são:  
  
 o que aconteceu. Forneça uma descrição clara do problema usando termos que se relacionam com a experiência do usuário. Por exemplo, uma mensagem de exceção ruim seria "Seção de configuração inválida". Isso deixa o usuário se perguntando qual seção de configuração está incorreta e por que ela está incorreta. Uma mensagem melhorada seria "Configuração inválida de configuração \<> vinculação". Uma mensagem ainda melhor seria "Não é possível adicionar o transporte chamado myTransport à vinculação chamada myBinding porque a vinculação já tem um transporte chamado myTransport". Esta é uma mensagem muito específica usando termos e nomes que o usuário pode identificar facilmente no arquivo de configuração do aplicativo. No entanto, ainda faltam alguns componentes-chave.  
  
 O significado do erro. A menos que a mensagem diga claramente o que o erro significa, é provável que o usuário se pergunte se é um erro fatal ou se pode ser ignorado. Em geral, as mensagens devem levar ao significado ou significado do erro. Para melhorar o exemplo anterior, a mensagem poderia ser "ServiceHost falhou em abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport à vinculação chamada myBinding porque a vinculação já tem um transporte chamado myTransport".  
  
 Como o usuário deve corrigir o problema. A parte mais importante da mensagem é ajudar o usuário a corrigir o problema. A mensagem deve incluir algumas orientações ou dicas sobre o que verificar ou corrigir para remediar o problema. Por exemplo, "ServiceHost falhou em abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport à vinculação chamada myBinding porque a vinculação já tem um transporte chamado myTransport. Por favor, certifique-se de que há apenas um transporte na ligação".  
  
## <a name="communicating-faults"></a>Falhas de comunicação  
 SOAP 1.1 e SOAP 1.2 definem uma estrutura específica para falhas. Existem algumas diferenças entre as duas especificações, mas, em geral, os tipos Mensagem e MensagemFalha são usados para criar e consumir falhas.  
  
 ![Lidar com exceções e falhas](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")  
SABÃO 1.2 Falha (esquerda) e SABÃO 1.1 Falha (direita). Observe que no SOAP 1.1 apenas o elemento Falha é qualificado para namespace.  
  
 Soap define uma mensagem de falha como uma mensagem que `<env:Fault>`contém apenas `<env:Body>`um elemento de falha (um elemento cujo nome é ) como uma criança de . O conteúdo do elemento de falha difere ligeiramente entre SOAP 1.1 e SOAP 1.2, conforme mostrado na figura 1. No entanto, a <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> classe normaliza essas diferenças em um modelo de objeto:  
  
```csharp
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 A `Code` propriedade corresponde `env:Code` ao `faultCode` (ou em SOAP 1.1) e identifica o tipo de falha. O SOAP 1.2 define cinco `faultCode` valores permitidos para (por exemplo, Remetente e Receptor) e define um `Subcode` elemento que pode conter qualquer valor de subcódigo. (Consulte a [especificação SOAP 1.2](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) para a lista de códigos de falha permitidos e seu significado.) O SOAP 1.1 tem um mecanismo `faultCode` ligeiramente diferente: ele define quatro valores (por exemplo, Cliente e Servidor) que podem ser `faultCodes`estendidos por meio da definição de notações totalmente novas ou usando a notação de ponto para criar mais específicos, por exemplo, Client.Authentication.  
  
 Quando você usa MessageFault para programar falhas, o FaultCode.Name e FaultCode.Namespace mapeia o nome e o namespace do SOAP 1.2 `env:Code` ou do SOAP 1.1 `faultCode`. O FaultCode.SubCode `env:Subcode` mapeia para SOAP 1.2 e é nulo para SOAP 1.1.  
  
 Você deve criar novos subcódigos de falha (ou novos códigos de falha se usar SOAP 1.1) se for interessante distinguir programáticamente uma falha. Isso é análogo à criação de um novo tipo de exceção. Você deve evitar usar a notação de ponto com códigos de falha SOAP 1.1. (O [Perfil Básico WS-I](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) também desencoraja o uso da notação de dot do código de falha.)  
  
```csharp
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 A `Reason` propriedade corresponde `env:Reason` à `faultString` (ou em SOAP 1.1) uma descrição de leitura humana da condição de erro análoga à mensagem de uma exceção. A `FaultReason` classe (e SOAP `env:Reason/faultString`) tem suporte embutido para ter múltiplas traduções no interesse da globalização.  
  
```csharp
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations
    {
       get;
    }  
  
 }  
```  
  
 O conteúdo de detalhes de falha é exposto `GetDetail` \<em `GetReaderAtDetailContents`MessageFault usando vários métodos, incluindo o> T e (). O detalhe da falha é um elemento opaco para carregar detalhes adicionais sobre a falha. Isso é útil se houver algum detalhe estruturado arbitrário que você deseja carregar com a falha.  
  
### <a name="generating-faults"></a>Gerando falhas  
 Esta seção explica o processo de gerar uma falha em resposta a uma condição de erro detectada em um canal ou em uma propriedade de mensagem criada pelo canal. Um exemplo típico é enviar de volta uma falha em resposta a uma mensagem de solicitação que contém dados inválidos.  
  
 Ao gerar uma falha, o canal personalizado não deve enviar a falha diretamente, pelo contrário, deve lançar uma exceção e deixar que a camada acima decida se converter essa exceção em uma falha e como enviá-la. Para ajudar nesta conversão, o `FaultConverter` canal deve fornecer uma implementação que pode converter a exceção lançada pelo canal personalizado para a falha apropriada. `FaultConverter` é definido como:  
  
```csharp
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,
                                   out Message message);  
}  
```  
  
 Cada canal que gera falhas `FaultConverter` personalizadas deve implementá-lo e devolvê-lo de uma chamada para `GetProperty<FaultConverter>`. A `OnTryCreateFaultMessage` implementação personalizada deve converter a exceção em uma `FaultConverter`falha ou delegar para o canal interno . Se o canal for um transporte, ele deve converter a `FaultConverter` exceção `FaultConverter` ou delegar para o codificador ou o padrão fornecido no WCF . O `FaultConverter` padrão converte erros correspondentes às mensagens de falha especificadas por WS-Endereçamento e SOAP. Aqui está `OnTryCreateFaultMessage` um exemplo de implementação.  
  
```csharp
public override bool OnTryCreateFaultMessage(Exception exception,
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,
                   out message);  
#else  
    FaultConverter inner =
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 Uma implicação deste padrão é que as exceções lançadas entre camadas para condições de erro que requerem falhas devem conter informações suficientes para o gerador de falhas correspondente para criar a falha correta. Como um autor de canal personalizado, você pode definir tipos de exceção que correspondem a diferentes condições de falha se tais exceções ainda não existirem. Observe que exceções que atravessam camadas de canal devem comunicar a condição de erro em vez de dados de falha opacos.  
  
### <a name="fault-categories"></a>Categorias de falhas  
 Há geralmente três categorias de falhas:  
  
1. Falhas que se espalharam por toda a pilha. Essas falhas podem ser encontradas em qualquer camada na pilha de canais, por exemplo, InvalidCardinalityAddressingException.  
  
2. Falhas que podem ser encontradas em qualquer lugar acima de uma determinada camada na pilha, por exemplo, alguns erros que pertencem a uma transação fluída ou a funções de segurança.  
  
3. Falhas direcionadas a uma única camada na pilha, por exemplo, erros como falhas numéricas de seqüência WS-RM.  
  
 Categoria 1. As falhas são geralmente falhas de Endereçamento ws e SOAP. A `FaultConverter` classe base fornecida pelo WCF converte erros correspondentes às mensagens de falha especificadas pelo WS-Endereçamento e pelo SOAP para que você não precise lidar com a conversão dessas exceções você mesmo.  
  
 Categoria 2. As falhas ocorrem quando uma camada adiciona uma propriedade à mensagem que não consome completamente informações de mensagem relativas a essa camada. Erros podem ser detectados mais tarde quando uma camada superior pede à propriedade da mensagem para processar ainda mais as informações da mensagem. Esses canais devem `GetProperty` implementar o especificado anteriormente para permitir que a camada superior envie de volta a falha correta. Um exemplo disso é o TransactionMessageProperty. Essa propriedade é adicionada à mensagem sem validar totalmente todos os dados no cabeçalho (isso pode envolver contato com o coordenador de transações distribuídas (DTC).  
  
 Categoria 3. As falhas são geradas e enviadas por uma única camada no processador. Portanto, todas as exceções estão contidas dentro da camada. Para melhorar a consistência entre os canais e facilitar a manutenção, seu canal personalizado deve usar o padrão especificado anteriormente para gerar mensagens de falha mesmo para falhas internas.  
  
### <a name="interpreting-received-faults"></a>Interpretando falhas recebidas  
 Esta seção fornece orientação para gerar a exceção apropriada ao receber uma mensagem de falha. A árvore de decisão para o processamento de uma mensagem em cada camada da pilha é a seguinte:  
  
1. Se a camada considerar a mensagem inválida, a camada deverá fazer seu processamento de 'mensagem inválida'. Esse processamento é específico para a camada, mas pode incluir deixar cair a mensagem, rastrear ou lançar uma exceção que é convertida em uma falha. Exemplos incluem o recebimento de uma mensagem que não está segura adequadamente ou o RM recebendo uma mensagem com um número de seqüência ruim.  
  
2. Caso contrário, se a mensagem for uma mensagem de falha que se aplica especificamente à camada e a mensagem não for significativa fora da interação da camada, a camada deve lidar com a condição de erro. Um exemplo disso é uma falha rm seqüenciada recusada que não tem sentido para camadas acima do canal RM e que implica a falha do canal RM e o lançamento de operações pendentes.  
  
3. Caso contrário, a mensagem deve ser devolvida de Solicitação() ou Receber(). Isso inclui casos em que a camada reconhece a falha, mas a falha apenas indica que uma solicitação falhou e não implica falhando no canal e jogando de operações pendentes. Para melhorar a usabilidade nesse caso, `GetProperty<FaultConverter>` a `FaultConverter` camada deve implementar e retornar uma classe `OnTryCreateException`derivada que pode converter a falha em uma exceção, substituindo .  
  
 O modelo de objeto a seguir suporta a conversão de mensagens em exceções:  
  
```csharp
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,
                                 MessageFault fault,
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,
                                 MessageFault fault,
                                 out Exception exception);  
}  
```  
  
 Uma camada de `GetProperty<FaultConverter>` canal pode ser implementada para suportar a conversão de mensagens de falha em exceções. Para isso, anule `OnTryCreateException` e inspecione a mensagem de falha. Se reconhecido, faça a conversão, caso contrário, peça ao canal interno para convertê-lo. Os canais de `FaultConverter.GetDefaultFaultConverter` transporte devem delegar para obter o Conversor de falhas de endereçamento de SABÃO/WS padrão.  
  
 Uma implementação típica é assim:  
  
```csharp
public override bool OnTryCreateException(  
                            Message message,
                            MessageFault fault,
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 Para condições específicas de falha que tenham cenários de `ProtocolException`recuperação distintos, considere definir uma classe derivada de .  
  
### <a name="mustunderstand-processing"></a>Deveentender processamento  
 Soap define uma falha geral para sinalizar que um cabeçalho necessário não foi compreendido pelo receptor. Essa falha é `mustUnderstand` conhecida como a falha. No WCF, canais `mustUnderstand` personalizados nunca geram falhas. Em vez disso, o WCF Dispatcher, que está localizado no topo da pilha de comunicação WCF, verifica se todos os cabeçalhos marcados como MustUnderstand=true foram compreendidos pela pilha subjacente. Se algum não foi `mustUnderstand` compreendido, uma falha é gerada nesse ponto. (O usuário pode optar `mustUnderstand` por desativar esse processamento e fazer com que o aplicativo receba todos os cabeçalhos de mensagem. Nesse caso, o aplicativo é `mustUnderstand` responsável pela realização do processamento.) A falha gerada inclui um cabeçalho Não Entendido que contém os nomes de todos os cabeçalhos com MustUnderstand=true que não foram compreendidos.  
  
 Se o seu canal de protocolo envia um `mustUnderstand` cabeçalho personalizado com MustUnderstand=true e recebe uma falha, ele deve descobrir se essa falha é devido ao cabeçalho enviado. Há dois membros `MessageFault` na classe que são úteis para isso:  
  
```csharp
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,
        string name, string ns) { }  
    ...  
  
}  
```  
  
 `IsMustUnderstandFault`retorna `true` se a `mustUnderstand` falha for uma falha. `WasHeaderNotUnderstood`retorna `true` se o cabeçalho com o nome e o namespace especificados estiver incluído na falha como um cabeçalho Não Entendido.  Caso contrário, ele retornará `false`.  
  
 Se um canal emite um cabeçalho marcado MustUnderstand = true, então essa `mustUnderstand` camada também deve implementar o padrão de API de geração de exceção e deve converter falhas causadas por esse cabeçalho para uma exceção mais útil como descrito anteriormente.  
  
## <a name="tracing"></a>Rastreamento  
 O .NET Framework fornece um mecanismo para rastrear a execução do programa como uma forma de ajudar a diagnosticar aplicações de produção ou problemas intermitentes onde não é possível apenas anexar um depurador e passar pelo código. Os componentes principais deste <xref:System.Diagnostics?displayProperty=nameWithType> mecanismo estão no namespace e consistem em:  
  
- <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, que é a fonte de <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>informações de rastreamento a serem escritas, que é uma <xref:System.Diagnostics.TraceSource> classe base abstrata para ouvintes concretos que recebem as informações a serem rastreadas a partir da e a saída para um destino específico do ouvinte. Por exemplo, <xref:System.Diagnostics.XmlWriterTraceListener> as saídas rastreiam informações para um arquivo XML. Finalmente, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>o que permite ao usuário do aplicativo controlar a verbosidade de rastreamento e é tipicamente especificado na configuração.  
  
- Além dos componentes principais, você pode usar a [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) para visualizar e pesquisar traços WCF. A ferramenta foi projetada especificamente para rastrear arquivos <xref:System.Diagnostics.XmlWriterTraceListener>gerados pelo WCF e escritos usando . A figura a seguir mostra os vários componentes envolvidos no rastreamento.  
  
 ![Lidar com exceções e falhas](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Rastreamento de um canal personalizado  
 Os canais personalizados devem escrever mensagens de rastreamento para ajudar no diagnóstico de problemas quando não é possível anexar um depurador ao aplicativo em execução. Isso envolve duas tarefas de alto <xref:System.Diagnostics.TraceSource> nível: instanciar um e chamar seus métodos para escrever traços.  
  
 Ao instanciar <xref:System.Diagnostics.TraceSource>um , a seqüência especificada torna-se o nome dessa fonte. Este nome é usado para configurar (ativar/desativar/definir o nível de rastreamento) a fonte de rastreamento. Também aparece na própria saída de rastreamento. Os canais personalizados devem usar um nome de origem exclusivo para ajudar os leitores da saída de rastreamento a entender de onde as informações de rastreamento vêm. Usar o nome da assembléia que está escrevendo a informação como o nome da fonte de rastreamento é a prática comum. Por exemplo, o WCF usa system.serviceModel como fonte de rastreamento de informações escritas a partir do conjunto System.ServiceModel.  
  
 Uma vez que você tenha <xref:System.Diagnostics.TraceSource.TraceData%2A>uma <xref:System.Diagnostics.TraceSource.TraceEvent%2A>fonte <xref:System.Diagnostics.TraceSource.TraceInformation%2A> de rastreamento, você chama seus métodos ou métodos para escrever entradas de rastreamento para os ouvintes de rastreamento. Para cada entrada de rastreamento que você escreve, você precisa classificar <xref:System.Diagnostics.TraceEventType>o tipo de evento como um dos tipos de evento definidos em . Esta classificação e a configuração do nível de rastreamento na configuração determinam se a entrada de rastreamento é saída para o ouvinte. Por exemplo, definir o nível `Warning` `Warning`de `Error` `Critical` rastreamento na configuração permite e rastrear entradas a serem escritas, mas bloqueia informações e entradas Verbose. Aqui está um exemplo de instanciar uma fonte de rastreamento e escrever uma entrada no nível de informação:  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> É altamente recomendável que você especifique um nome de origem de rastreamento exclusivo do seu canal personalizado para ajudar os leitores de saída a rastrear a entender de onde a saída veio.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integrando-se com o Trace Viewer  
 Os traços gerados pelo seu canal podem ser produzidos em um formato legível pela <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> Service Trace Viewer Tool [(SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) usando como ouvinte de rastreamento. Isso não é algo que você, como desenvolvedor de canais, precisa fazer. Em vez disso, é o usuário do aplicativo (ou a pessoa que soluciona o aplicativo) que precisa configurar esse ouvinte de rastreamento no arquivo de configuração do aplicativo. Por exemplo, as seguintes saídas <xref:System.ServiceModel?displayProperty=nameWithType> `Microsoft.Samples.Udp` de configuração `TraceEventsFile.e2e`rastreiam informações de ambos e para o arquivo nomeado:  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a>Rastreamento de dados estruturados  
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>tem <xref:System.Diagnostics.TraceSource.TraceData%2A> um método que leva um ou mais objetos que devem ser incluídos na entrada de rastreamento. Em geral, <xref:System.Object.ToString%2A?displayProperty=nameWithType> o método é chamado em cada objeto e a seqüência resultante é escrita como parte da entrada de rastreamento. Ao <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> usar para rastrear saque, você pode passar um <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> como objeto de dados para <xref:System.Diagnostics.TraceSource.TraceData%2A>. A entrada de rastreamento resultante inclui o <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>XML fornecido pelo . Aqui está um exemplo de entrada com dados do aplicativo XML:  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 O visualizador de rastreamento WCF entende `TraceRecord` o esquema do elemento mostrado anteriormente e extrai os dados de seus elementos infantis e os exibe em um formato tabular. Seu canal deve usar esse esquema ao rastrear dados estruturados do aplicativo para ajudar os usuários do Svctraceviewer.exe a ler os dados.
