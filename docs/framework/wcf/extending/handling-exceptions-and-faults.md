---
title: Lidando com exceções e falhas
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: c51d78bb982ec0748cd74a67a4f4b747526a4b42
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483902"
---
# <a name="handling-exceptions-and-faults"></a>Lidando com exceções e falhas
As exceções são usadas para comunicar erros localmente dentro do serviço ou a implementação do cliente. Falhas, por outro lado, são usadas para comunicar erros entre limites de serviço, como a do servidor para o cliente ou vice-versa. Além das falhas, os canais de transporte geralmente usam mecanismos de transporte específicos para comunicar erros de nível de transporte. Por exemplo, o transporte HTTP usa códigos de status como 404 para comunicar uma URL de ponto de extremidade não existente (não há nenhum ponto de extremidade para enviar de volta uma falha). Este documento consiste em três seções que fornecem orientação para os autores de canal personalizado. A primeira seção fornece orientação sobre quando e como definir e lançar exceções. A segunda seção fornece orientação sobre como gerar e consumir falhas. A terceira seção explica como fornecer informações de rastreamento para ajudar o usuário do seu canal personalizado na solução de problemas de aplicativos em execução.  
  
## <a name="exceptions"></a>Exceções  
 Há duas coisas para ter em mente ao lançar uma exceção: primeiro ele deve ser de um tipo que permite aos usuários escrever código correto pode reagir adequadamente a exceção. Em segundo lugar, ele deve fornecer informações suficientes para que o usuário para entender o que deu errado, o impacto da falha e como corrigi-lo. As seções a seguir oferecem orientação sobre tipos de exceção e mensagens para os canais do Windows Communication Foundation (WCF). Também há orientação geral sobre exceções no .NET nas diretrizes de Design para o documento de exceções.  
  
### <a name="exception-types"></a>Tipos de exceção  
 Todas as exceções geradas pelos canais devem ser um <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, ou um tipo derivado de <xref:System.ServiceModel.CommunicationException>. (Exceções, como <xref:System.ObjectDisposedException> também pode ser lançada, mas apenas para indicar que o código de chamada tem usado indevidamente o canal. Se um canal for usado corretamente, ele deve apenas lançar as exceções de determinado.) O WCF fornece sete tipos de exceções que derivam de <xref:System.ServiceModel.CommunicationException> e foram projetados para ser usado pelos canais. Há outros <xref:System.ServiceModel.CommunicationException>-derivado exceções que são projetadas para ser usado por outras partes do sistema. Esses tipos de exceção são:  
  
|Tipo de exceção|Significado|Conteúdo da exceção interna|Estratégia de recuperação|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|O endereço de ponto de extremidade especificado para escuta já está em uso.|Se estiver presente, fornece mais detalhes sobre o erro de transporte que provocou essa exceção. Por exemplo: <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, ou <xref:System.Net.Sockets.SocketException>.|Tente um endereço diferente.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|O processo não é permitido o acesso ao endereço do ponto de extremidade especificado para escuta.|Se estiver presente, fornece mais detalhes sobre o erro de transporte que provocou essa exceção. Por exemplo, <xref:System.IO.PipeException>, ou <xref:System.Net.HttpListenerException>.|Tente com credenciais diferentes.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|O <xref:System.ServiceModel.ICommunicationObject> que está sendo usada está no estado com falha (para obter mais informações, consulte [Noções básicas sobre as alterações de estado](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Observe que, quando um objeto com vários pendentes transições de chamadas para o estado de falha, apenas uma chamada gera uma exceção que está relacionada a falha e o restante do arremesso chamadas um <xref:System.ServiceModel.CommunicationObjectFaultedException>. Essa exceção é lançada normalmente porque ignora completamente uma exceção de um aplicativo e tenta usar um objeto já com defeito, possivelmente em um thread diferente daquele que capturou a exceção original.|Se estiver presente fornece detalhes sobre a exceção interna.|Crie um novo objeto. Observe que, dependendo do que causou o <xref:System.ServiceModel.ICommunicationObject> para falhas em primeiro lugar, pode haver outro trabalho necessário para recuperar.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|O <xref:System.ServiceModel.ICommunicationObject> que está sendo usado foi anulado (para obter mais informações, consulte [Noções básicas sobre as alterações de estado](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Semelhante ao <xref:System.ServiceModel.CommunicationObjectFaultedException>, sua exceção indica que o aplicativo tiver chamado <xref:System.ServiceModel.ICommunicationObject.Abort%2A> no objeto, possivelmente a partir de outro thread, e o objeto não é mais utilizável por esse motivo.|Se estiver presente fornece detalhes sobre a exceção interna.|Crie um novo objeto. Observe que, dependendo do que causou o <xref:System.ServiceModel.ICommunicationObject> para anular em primeiro lugar, pode haver outro trabalho necessário para recuperar.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|O ponto de extremidade remoto de destino não está escutando. Isso pode resultar de qualquer parte do endereço do ponto de extremidade que está sendo incorreta, pode resolver ou o ponto de extremidade que está sendo pressionada. Os exemplos incluem erros DNS, Gerenciador de fila não está disponível e o serviço não está em execução.|A exceção interna fornece detalhes, normalmente de transporte subjacente.|Tente um endereço diferente. Como alternativa, o remetente pode Aguarde alguns instantes e tente novamente, caso o serviço foi desativado|  
|<xref:System.ServiceModel.ProtocolException>|Os protocolos de comunicação, conforme descrito pela política do ponto de extremidade, são incompatíveis entre pontos de extremidade. Por exemplo, de enquadramento incompatibilidade de tipo de conteúdo ou o tamanho máximo de mensagem excedido.|Se estiver presente fornece mais informações sobre o erro de protocolo específico. Por exemplo, <xref:System.ServiceModel.QuotaExceededException> é a exceção interna à causa do erro é exceder MaxReceivedMessageSize.|Recuperação: Certifique-se o remetente e o protocolo recebido configurações correspondem. Uma maneira de fazer isso é importar novamente os metadados do ponto de extremidade de serviço (política) e usar a ligação gerada para recriar o canal.|  
|<xref:System.ServiceModel.ServerTooBusyException>|O ponto de extremidade remoto está escutando, mas não está preparado para processar mensagens.|Se estiver presente, a exceção interna fornece os detalhes do erro de nível de transporte ou falha de SOAP.|Recuperação: Aguarde e repita a operação mais tarde.|  
|<xref:System.TimeoutException>|A operação não foi concluída dentro do período de tempo limite.|Pode fornecer detalhes sobre o tempo limite.|Aguarde e repita a operação mais tarde.|  
  
 Defina um novo tipo de exceção apenas se tipo corresponde a uma estratégia de recuperação específico diferente de todos os tipos de exceção existente. Se você definir um novo tipo de exceção, ele deve derivar de <xref:System.ServiceModel.CommunicationException> ou uma de suas classes derivadas.  
  
### <a name="exception-messages"></a>Mensagens de exceção  
 Mensagens de exceção destinam-se o usuário não o programa para que eles devem fornecer informações suficientes para ajudar o usuário a entender e resolver o problema. As três partes essenciais de uma mensagem de exceção boa são:  
  
 O que aconteceu. Forneça uma descrição clara do problema usando termos que se relacionam com a experiência do usuário. Por exemplo, uma mensagem de exceção incorreto seria "seção de configuração inválido". Isso deixa o usuário está se perguntando qual seção de configuração está incorreta e por que ele está incorreto. Uma melhor mensagem seria "seção de configuração inválido \<customBinding >". Uma mensagem ainda melhor seria "não é possível adicionar o transporte chamado myTransport para a associação denominada myBinding porque a associação já tem um transporte chamado myTransport". Esta é uma mensagem muito específica usando nomes que o usuário pode identificar facilmente e termos no arquivo de configuração do aplicativo. No entanto, há ainda alguns componentes-chave ausente.  
  
 O significado do erro. A menos que a mensagem informa claramente o que significa que o erro, o usuário é provável que você esteja se perguntando se ele é um erro fatal ou se ele pode ser ignorado. Em geral, as mensagens devem começar com o significado ou a significância do erro. Para melhorar o exemplo anterior, a mensagem poderia ser "ServiceHost falha ao abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport para a associação denominada myBinding porque a associação já tem um transporte chamado myTransport".  
  
 Como o usuário deve corrigir o problema. A parte mais importante da mensagem está ajudando a correção do problema do usuário. A mensagem deve incluir algumas diretrizes ou dicas sobre o que verificar ou corrigir para corrigir o problema. Por exemplo, "ServiceHost falha ao abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport para a associação denominada myBinding porque a associação já tem um transporte chamado myTransport. Verifique se há apenas um transporte na associação".  
  
## <a name="communicating-faults"></a>Falhas de comunicação  
 SOAP 1.1 e SOAP 1.2 definem uma estrutura específica para falhas. Há algumas diferenças entre as duas especificações, mas em geral, os tipos de mensagem e MessageFault são usados para criar e consumir falhas.  
  
 ![Tratando exceções e falhas](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")  
SOAP 1.2 falha (à esquerda) e falha (à direita) do SOAP 1.1. Observe que, apenas o elemento de falha de SOAP 1.1, é o namespace qualificado.  
  
 O SOAP define uma mensagem de falha como uma mensagem que contém apenas um elemento de falha (um elemento cujo nome é `<env:Fault>`) como um filho de `<env:Body>`. O conteúdo do elemento de falha diferem ligeiramente SOAP 1.1 e SOAP 1.2 conforme mostrado na Figura 1. No entanto, o <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> classe normaliza essas diferenças em um modelo de objetos:  
  
```  
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
  
 O `Code` propriedade corresponde à `env:Code` (ou `faultCode` em SOAP 1.1) e identifica o tipo de falha. O SOAP 1.2 define cinco valores possíveis para o `faultCode` (por exemplo, o remetente e receptor) e define um `Subcode` elemento que pode conter qualquer valor subcódigo. (Consulte a [especificação SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=95176) para a lista de códigos de falha permitidos e seus significados.) SOAP 1.1 tem um mecanismo ligeiramente diferente: ele define quatro `faultCode` valores (por exemplo, cliente e servidor) que podem ser estendidas definindo totalmente novos ou usando a notação de ponto para criar mais específicos `faultCodes`, por exemplo, Client.Authentication.  
  
 Quando você usa MessageFault para falhas do programa, o FaultCode.Name e FaultCode.Namespace mapeia para o nome e namespace de SOAP 1.2 `env:Code` ou o SOAP 1.1 `faultCode`. O FaultCode.SubCode é mapeado para `env:Subcode` para SOAP 1.2 e é nula para SOAP 1.1.  
  
 Você deve criar o novo subcódigos de falha (ou novos códigos de falha se usando o SOAP 1.1) se ele é interessante distinguir programaticamente uma falha. Isso é análogo ao criar um novo tipo de exceção. Você deve evitar usar a notação de ponto com códigos de falha de SOAP 1.1. (O [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) também desencoraja o uso da notação de ponto de código de falha.)  
  
```  
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
  
 O `Reason` propriedade corresponde à `env:Reason` (ou `faultString` em SOAP 1.1) uma descrição legível por humanos da condição de erro semelhante a mensagem de uma exceção. O `FaultReason` classe (e o SOAP `env:Reason/faultString`) tem suporte interno para ter várias traduções com o intuito de globalização.  
  
```  
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
  
 O conteúdo de detalhe de falha é exposto na MessageFault usando vários métodos incluindo o `GetDetail` \<T > e `GetReaderAtDetailContents`(). O detalhe da falha é um elemento opaco para carregar os detalhes adicionais sobre a falha. Isso é útil quando há alguns detalhes estruturados arbitrária que você deseja realizar com a falha.  
  
### <a name="generating-faults"></a>Gerar falhas  
 Esta seção explica o processo de geração de uma falha em resposta a uma condição de erro detectada em um canal ou em uma propriedade de mensagem criada pelo canal. Um exemplo típico é enviar novamente uma falha em resposta a uma mensagem de solicitação que contém dados inválidos.  
  
 Ao gerar uma falha, o canal personalizado não deve enviar a falha diretamente, em vez disso, ele deve lançar uma exceção e permitir que a camada acima decidir se deve converter essa exceção para uma falha e como enviá-lo. Para auxiliar nessa conversão, o canal deve fornecer um `FaultConverter` implementação que pode converter a exceção lançada pelo canal personalizado para a falha apropriada. `FaultConverter` é definido como:  
  
```  
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
  
 Cada canal que gera falhas personalizadas deve implementar `FaultConverter` e retorná-lo de uma chamada para `GetProperty<FaultConverter>`. O custom `OnTryCreateFaultMessage` implementação deve converter a exceção em uma falha ou delegar para o canal interno `FaultConverter`. Se o canal é um transporte ele deve converter a exceção ou delegar para o codificador `FaultConverter` ou o padrão `FaultConverter` fornecido no WCF. O padrão `FaultConverter` converte erros correspondentes a mensagens de falha especificadas por WS-Addressing e SOAP. Aqui está um exemplo `OnTryCreateFaultMessage` implementação.  
  
```  
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
  
 Uma implicação desse padrão é que as exceções lançadas entre camadas para condições de erro que exigem falhas devem conter informações suficientes para que o gerador de falha correspondentes criar a falha corretos. Como um autor de canal personalizado, você pode definir tipos de exceção que correspondem às condições de falha diferentes, se essas exceções ainda não existir. Observe que exceções percorrendo as camadas do canal devem se comunicar a condição de erro em vez de dados de falha opaco.  
  
### <a name="fault-categories"></a>Categorias de falhas  
 Normalmente, há três categorias de falhas:  
  
1.  Falhas que são difundidas em toda a pilha inteira. Essas falhas pode ser encontradas em qualquer camada na pilha de canais, por exemplo InvalidCardinalityAddressingException.  
  
2.  Falhas que podem ser encontraram em qualquer lugar acima de um determinado camada da pilha por exemplo, alguns erros que pertencem a uma transação fluída ou para funções de segurança.  
  
3.  Falhas que são direcionadas a uma única camada da pilha, por exemplo erros como falhas de número de sequência WS-RM.  
  
 Categoria de 1. As falhas são geralmente WS-Addressing e falhas de SOAP. A base de `FaultConverter` classe fornecido pelo WCF erros converte correspondente a mensagens de falha especificado por WS-Addressing e SOAP para que você não precise lidar com essas exceções conversão por conta própria.  
  
 Categoria 2. As falhas ocorrem quando uma camada adiciona uma propriedade para a mensagem que não consome completamente as informações de mensagem que pertencem a essa camada. Erros podem ser detectados mais tarde, quando uma camada superior pergunta a propriedade de mensagem para processar ainda mais informações sobre a mensagem. Esses canais devem implementar o `GetProperty` especificado anteriormente para habilitar a camada superior enviar de volta a falha corretos. Um exemplo disso é o TransactionMessageProperty. Essa propriedade é adicionada à mensagem sem validar completamente todos os dados no cabeçalho (fazer isso pode envolver a entrar em contato com o coordenador de transações distribuídas (DTC).  
  
 Categoria de 3. Falhas somente são geradas e enviadas por uma única camada no processador. Portanto todas as exceções estão contidas dentro da camada. Para melhorar a consistência entre os canais e facilidade de manutenção, o seu canal personalizado deve usar o padrão especificado anteriormente para gerar mensagens de falha, mesmo para as falhas internas.  
  
### <a name="interpreting-received-faults"></a>Interpretando falhas recebidas  
 Esta seção fornece orientação para gerar a exceção apropriada ao receber uma mensagem de falha. A árvore de decisão para processar uma mensagem em todas as camadas da pilha é da seguinte maneira:  
  
1.  Se a camada considera a mensagem a ser inválido, a camada deve fazer seu processamento 'mensagem inválida'. Tal processamento é específico para a camada, mas poderia incluir a descartar a mensagem, rastreamento, ou gerar uma exceção que será convertida em uma falha. Exemplos incluem segurança recebendo uma mensagem que não está devidamente protegida ou RM receber uma mensagem com um número de sequência incorreta.  
  
2.  Caso contrário, se a mensagem é uma mensagem de falha que se aplica especificamente à camada, e a mensagem não faz sentida fora de interação da camada, a camada deve lidar com a condição de erro. Um exemplo disso é uma falha de sequência de RM recusada que não faz sentido para as camadas acima o canal do RM e isso implica que o canal do RM a falha e lançando a partir das operações pendentes.  
  
3.  Caso contrário, a mensagem deve ser retornada do Request () ou Receive (). Isso inclui os casos em que a camada reconhece a falha, mas a falha apenas indica que uma solicitação falhou e não implica a haver falha no canal e lançando a partir das operações pendentes. Para melhorar a usabilidade, nesse caso, a camada deve implementar `GetProperty<FaultConverter>` e retornar um `FaultConverter` derivado da classe que pode converter a falha em uma exceção, substituindo `OnTryCreateException`.  
  
 O modelo de objeto a seguir dá suporte a mensagens converter exceções:  
  
```  
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
  
 Uma camada de canais pode implementar `GetProperty<FaultConverter>` para dar suporte a mensagens de falha de conversão para exceções. Para fazer isso, substitua `OnTryCreateException` e inspecionar a mensagem de falha. Se reconhecidas, fazer a conversão, caso contrário, pergunte o canal interno para convertê-lo. Canais de transporte devem delegar ao `FaultConverter.GetDefaultFaultConverter` para obter o padrão FaultConverter SOAP/WS-Addressing.  
  
 Uma implementação típica tem esta aparência:  
  
```  
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
  
 Para condições de falha específicos que têm os cenários de recuperação distintos, considere definir uma classe derivada de `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>Processamento de MustUnderstand  
 O SOAP define uma falha geral para sinalizar que um cabeçalho necessário não foi entendido pelo destinatário. Essa falha é conhecida como o `mustUnderstand` falha. No WCF, canais personalizados nunca geram `mustUnderstand` falhas. Em vez disso, o Dispatcher WCF, que está localizado na parte superior da pilha de comunicação do WCF, verifica que todos os cabeçalhos que foram marcados como MustUndestand = true foram entendidos pela pilha subjacente. Se qualquer não foram compreendidos, um `mustUnderstand` falha é gerada nesse ponto. (O usuário pode optar por desativar isso `mustUnderstand` de processamento e fazer com que o aplicativo receber todos os cabeçalhos de mensagem. Nesse caso, o aplicativo é responsável por executar `mustUnderstand` de processamento.) A falha gerada inclui um cabeçalho de NotUnderstood que contém os nomes de todos os cabeçalhos com MustUnderstand = true não foi compreendido.  
  
 Se o seu canal do protocolo envia um cabeçalho personalizado com MustUnderstand = true e recebe um `mustUnderstand` falha, ele deve descobrir se essa falha é devida ao cabeçalho enviado por ele. Há dois membros no `MessageFault` classe são úteis para isso:  
  
```  
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,   
        string name, string ns) { }  
    ...  
  
}  
```  
  
 `IsMustUnderstandFault` Retorna `true` se a falha é um `mustUnderstand` falha. `WasHeaderNotUnderstood` Retorna `true` se o cabeçalho com o nome especificado e o namespace está incluído na falha como um cabeçalho de NotUnderstood.  Caso contrário, retornará `false`.  
  
 Se um canal emite um cabeçalho que está marcado como MustUnderstand = true, em seguida, essa camada também deve implementar o padrão de API de geração de exceção e deve converter `mustUnderstand` falhas causadas por aquele cabeçalho a uma exceção mais úteis, como descrito anteriormente.  
  
## <a name="tracing"></a>Rastreamento  
 O .NET Framework fornece um mecanismo para rastrear a execução de programa como uma maneira de ajudar a diagnosticar aplicativos de produção ou problemas intermitentes onde não é possível simplesmente anexar um depurador e percorrer o código. Os principais componentes desse mecanismo estão no <xref:System.Diagnostics?displayProperty=nameWithType> namespace e consistem em:  
  
-   <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, que é a origem das informações de rastreamento a serem gravados <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, que é uma classe base abstrata para os ouvintes concretas que recebem as informações a ser rastreado do <xref:System.Diagnostics.TraceSource> e fazê-lo para um destino específica do ouvinte. Por exemplo, <xref:System.Diagnostics.XmlWriterTraceListener> informações para um arquivo XML de rastreamento de saídas. Por fim, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, que permite que o usuário do aplicativo controlar o nível de detalhes de rastreamento e geralmente é especificado na configuração.  
  
-   Além dos componentes principais, você pode usar o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para exibir e pesquisar WCF rastreamentos. A ferramenta foi criada especificamente para arquivos de rastreamento gerados pelo WCF e escritos usando <xref:System.Diagnostics.XmlWriterTraceListener>. A figura a seguir mostra os vários componentes envolvidos no rastreamento.  
  
 ![Tratando exceções e falhas](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Rastreamento de um canal personalizado  
 Canais personalizados devem gravar mensagens de rastreamento para auxiliar no diagnóstico de problemas quando não é possível anexar um depurador ao aplicativo em execução. Isso envolve duas tarefas de alto níveis: instanciar um <xref:System.Diagnostics.TraceSource> e chamando seus métodos para gravar rastreamentos.  
  
 Ao instanciar um <xref:System.Diagnostics.TraceSource>, a cadeia de caracteres que você especifique se torna o nome dessa fonte. Esse nome é usado para configurar a origem de rastreamento de (nível de rastreamento de habilitar/desabilitar/set). Ele também aparece na saída em si. Canais personalizados devem usar um nome exclusivo de origem para ajudar os leitores da saída do rastreamento entender de onde vêm as informações de rastreamento. Usando o nome do assembly que está gravando as informações como o nome da origem de rastreamento é a prática comum. Por exemplo, o WCF usa o System. ServiceModel como a origem de rastreamento de informações gravadas do assembly System. ServiceModel.  
  
 Depois de uma origem de rastreamento, você chama seu <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, ou <xref:System.Diagnostics.TraceSource.TraceInformation%2A> métodos para gravar entradas de rastreamento nos ouvintes de rastreamento. Para cada entrada de rastreamento escrever, você precisa classificar o tipo de evento como um dos tipos de evento definidos no <xref:System.Diagnostics.TraceEventType>. Essa classificação e a configuração de nível de rastreamento na configuração determinam se a entrada de rastreamento é enviado para o ouvinte. Por exemplo, definindo o nível de rastreamento na configuração para `Warning` permite `Warning`, `Error` e `Critical` entradas a serem gravados, mas blocos de informações e detalhado de entradas de rastreamento. Aqui está um exemplo de como criar uma instância de uma origem de rastreamento e gravar uma entrada no nível de informações:  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  É altamente recomendável que você especifique um nome de origem de rastreamento que é exclusivo para seu canal personalizado para ajudar os leitores de saída de rastreamento a entender de onde veio a saída.  
  
#### <a name="integrating-with-the-trace-viewer"></a>A integração com o Visualizador de rastreamento  
 Rastreamentos gerados pelo seu canal podem ser a saída em um formato legível pela [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) usando <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> como o ouvinte de rastreamento. Isso não é algo que você, como desenvolvedor de canal, precisa fazer. Em vez disso, ele é o usuário do aplicativo (ou a pessoa que o aplicativo de solução de problemas) que precisa para configurar este ouvinte de rastreamento no arquivo de configuração do aplicativo. Por exemplo, a configuração a seguir gera informações de rastreamento de ambos <xref:System.ServiceModel?displayProperty=nameWithType> e `Microsoft.Samples.Udp` para o arquivo chamado `TraceEventsFile.e2e`:  
  
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
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> tem um <xref:System.Diagnostics.TraceSource.TraceData%2A> método que usa um ou mais objetos que devem ser incluídos na entrada de rastreamento. Em geral, o <xref:System.Object.ToString%2A?displayProperty=nameWithType> método é chamado em cada objeto e a cadeia de caracteres resultante é gravada como parte da entrada de rastreamento. Ao usar <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> para produzir rastreamentos, você pode passar uma <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> como o objeto de dados à <xref:System.Diagnostics.TraceSource.TraceData%2A>. A entrada de rastreamento resultante inclui o XML fornecido pelo <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Aqui está um exemplo de entrada com os dados de aplicativo de XML:  
  
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
  
 O Visualizador de rastreamento do WCF compreende o esquema do `TraceRecord` elemento mostrado anteriormente e extrai os dados de seus elementos filho e o exibe em um formato tabular. Seu canal deve usar este esquema quando o rastreamento de dados estruturados de aplicativo para ajudar usuários Svctraceviewer.exe ler os dados.
