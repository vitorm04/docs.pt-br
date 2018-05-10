---
title: Lidando com exceções e falhas
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 494a0665f5bad2c7da3998cf77ced79314ca2f36
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="handling-exceptions-and-faults"></a>Lidando com exceções e falhas
Exceções são usadas para comunicar erros localmente dentro do serviço ou a implementação de cliente. Falhas, por outro lado, são usadas para comunicar erros em limites de serviços, como do servidor para o cliente ou vice-versa. Além de falhas, canais de transporte geralmente usam mecanismos de transporte específicos para comunicar erros de nível de transporte. Por exemplo, o transporte HTTP usa códigos de status como 404 para comunicar uma URL de ponto de extremidade não existente (não há nenhum ponto de extremidade para enviar de volta uma falha). Este documento consiste em três seções que fornecem orientação para os autores de canal personalizado. A primeira seção fornece orientações sobre quando e como definir e gerar exceções. A segunda seção fornece orientações sobre como gerar e consumir falhas. A terceira seção explica como fornecer informações de rastreamento para ajudar o usuário do seu canal personalizado na solução de aplicativos em execução.  
  
## <a name="exceptions"></a>Exceções  
 Há duas coisas que ter em mente ao lançar uma exceção: primeiro deve ser de um tipo que permite aos usuários escrever código correto que possa reagir corretamente a exceção. Em segundo lugar, ele deve fornecer informações suficientes para o usuário para entender o que deu errado, o impacto da falha e como corrigi-lo. As seções a seguir fornecem orientações sobre tipos de exceção e mensagens de canais do Windows Communication Foundation (WCF). Também há orientação geral sobre exceções no .NET nas diretrizes de Design para o documento de exceções.  
  
### <a name="exception-types"></a>Tipos de exceção  
 Todas as exceções lançadas pelos canais devem ser um <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, ou um tipo derivado de <xref:System.ServiceModel.CommunicationException>. (Exceções como <xref:System.ObjectDisposedException> também pode ser acionada, mas apenas para indicar que o código de chamada foi usado incorretamente o canal. Se um canal está sendo usado corretamente, ela deve apenas lançar exceções determinadas.) O WCF oferece sete tipos de exceções que derivam de <xref:System.ServiceModel.CommunicationException> e são projetados para ser usados pelos canais. Há outros <xref:System.ServiceModel.CommunicationException>-derivado exceções que são projetadas para ser usado por outras partes do sistema. Esses tipos de exceção são:  
  
|Tipo de exceção|Significado|Conteúdo de exceção interna|Estratégia de recuperação|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|O endereço de ponto de extremidade especificado para escuta já está em uso.|Se estiver presente, fornece mais detalhes sobre o erro de transporte que provocou essa exceção. Por exemplo: <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, ou <xref:System.Net.Sockets.SocketException>.|Tente um endereço diferente.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|O processo não tem permissão de acesso para o endereço de ponto de extremidade especificado para escuta.|Se estiver presente, fornece mais detalhes sobre o erro de transporte que provocou essa exceção. Por exemplo, <xref:System.IO.PipeException>, ou <xref:System.Net.HttpListenerException>.|Tente com credenciais diferentes.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|O <xref:System.ServiceModel.ICommunicationObject> que está sendo usado está no estado com falha (para obter mais informações, consulte [Noções básicas sobre alterações de estado](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Observe que, quando um objeto com vários pendentes transições de chamadas para o estado com falha, apenas uma chamada gera uma exceção que está relacionada a falha e o restante das chamadas throw um <xref:System.ServiceModel.CommunicationObjectFaultedException>. Essa exceção é lançada normalmente porque um aplicativo overlooks uma exceção e tenta usar um objeto já com defeito, possivelmente em um thread diferente daquele que detectado a exceção original.|Se houver fornece detalhes sobre a exceção interna.|Crie um novo objeto. Observe que, dependendo do que causou o <xref:System.ServiceModel.ICommunicationObject> para falhas em primeiro lugar, pode haver outro trabalho necessário para recuperar.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|O <xref:System.ServiceModel.ICommunicationObject> que está sendo usado foi anulado (para obter mais informações, consulte [Noções básicas sobre alterações de estado](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Semelhante ao <xref:System.ServiceModel.CommunicationObjectFaultedException>, sua exceção indica que o aplicativo tiver chamado <xref:System.ServiceModel.ICommunicationObject.Abort%2A> no objeto, possivelmente de outro thread, e o objeto não será mais utilizável por esse motivo.|Se houver fornece detalhes sobre a exceção interna.|Crie um novo objeto. Observe que, dependendo do que causou o <xref:System.ServiceModel.ICommunicationObject> para anular em primeiro lugar, pode haver outro trabalho necessário para recuperar.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|O ponto de extremidade remoto de destino não está escutando. Isso pode resultar de qualquer parte do endereço de ponto de extremidade que está sendo incorreta, pode resolver ou o ponto de extremidade que está sendo pressionada. Os exemplos incluem erros DNS, o Gerenciador de fila não está disponível e o serviço não está em execução.|A exceção interna fornece detalhes, normalmente de transporte subjacente.|Tente um endereço diferente. Como alternativa, o remetente pode Aguarde um pouco e tente novamente, caso o serviço foi desativado|  
|<xref:System.ServiceModel.ProtocolException>|Os protocolos de comunicação, conforme descrito pela política do ponto de extremidade, são incompatíveis entre pontos de extremidade. Por exemplo, quadros de incompatibilidade de tipo de conteúdo ou o tamanho de mensagem máximo excedido.|Se houver fornece mais informações sobre o erro de protocolo específico. Por exemplo, <xref:System.ServiceModel.QuotaExceededException> é a exceção interna ao MaxReceivedMessageSize excedido é a causa do erro.|Recuperação: Certifique-se de remetente e o protocolo recebido configurações correspondem. Uma maneira de fazer isso é importar novamente os metadados do ponto de extremidade de serviço (política) e usar a associação gerada para recriar o canal.|  
|<xref:System.ServiceModel.ServerTooBusyException>|O ponto de extremidade remoto está escutando, mas não está preparado para processar mensagens.|Se estiver presente, a exceção interna fornece os detalhes do erro de nível de transporte ou falha de SOAP.|Recuperação: Aguarde e tente novamente a operação mais tarde.|  
|<xref:System.TimeoutException>|A operação não foi concluída dentro do período de tempo limite.|Pode fornecer detalhes sobre o tempo limite.|Aguarde e tente novamente a operação mais tarde.|  
  
 Defina um novo tipo de exceção somente se esse tipo corresponde a uma estratégia de recuperação específico diferente de todos os tipos de exceção existente. Se você definir um novo tipo de exceção, ele deve derivar de <xref:System.ServiceModel.CommunicationException> ou uma de suas classes derivadas.  
  
### <a name="exception-messages"></a>Mensagens de exceção  
 Mensagens de exceção são destinadas o usuários não o programa para que eles devem fornecer informações suficientes para ajudar o usuário a compreender e solucionar o problema. As três partes essenciais de uma mensagem de exceção BOM são:  
  
 O que aconteceu. Forneça uma descrição clara do problema usando os termos relacionados a experiência do usuário. Por exemplo, uma mensagem de exceção incorreto seria "seção de configuração inválido". Isso deixa o usuário se perguntando qual seção de configuração está incorreta e por que é incorreto. Uma mensagem de melhor seria "seção de configuração inválido \<customBinding >". Uma mensagem ainda melhor seria "não é possível adicionar o transporte chamado myTransport para a associação denominada myBinding porque a associação já tem um transporte denominado myTransport". Esta é uma mensagem de muito específica usando nomes que o usuário pode identificar facilmente e termos no arquivo de configuração do aplicativo. No entanto, há ainda alguns componentes-chave ausente.  
  
 O significado do erro. A menos que a mensagem informa claramente o que significa que o erro, o usuário é provável que você esteja se perguntando se é um erro fatal ou se ele pode ser ignorado. Em geral, as mensagens devem começar com o significado ou a significância do erro. Para melhorar o exemplo anterior, a mensagem pode ser "ServiceHost falha ao abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport para a associação denominada myBinding porque a associação já tem um transporte denominado myTransport".  
  
 Como o usuário deve corrigir o problema. A parte mais importante da mensagem está ajudando a correção do problema do usuário. A mensagem deve incluir algumas diretrizes ou dicas sobre o que verificar ou corrigir para corrigir o problema. Por exemplo, "ServiceHost falha ao abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport para a associação denominada myBinding porque a associação já tem um transporte denominado myTransport. Verifique se há apenas um transporte na associação".  
  
## <a name="communicating-faults"></a>Falhas de comunicação  
 SOAP 1.1 e SOAP 1.2 definem uma estrutura específica para falhas. Há algumas diferenças entre as duas especificações, mas em geral, os tipos de mensagem e MessageFault são usados para criar e consumir falhas.  
  
 ![Tratando exceções e falhas](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")  
SOAP 1.2 falha (à esquerda) e (à direita) Falha do SOAP 1.1. Observe que apenas o elemento de falhas de SOAP 1.1 é namespace qualificado.  
  
 O SOAP define uma mensagem de falha como uma mensagem que contém apenas um elemento de falha (um elemento cujo nome é `<env:Fault>`) como um filho de `<env:Body>`. O conteúdo do elemento falhas diferem ligeiramente SOAP 1.1 e SOAP 1.2 conforme mostrado na Figura 1. No entanto, a <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> classe normaliza essas diferenças em um modelo de objetos:  
  
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
  
 O `Code` propriedade corresponde do `env:Code` (ou `faultCode` em SOAP 1.1) e identifica o tipo da falha. SOAP 1.2 define cinco valores permitidos para `faultCode` (por exemplo, o remetente e o destinatário) e define um `Subcode` elemento que pode conter qualquer valor subcódigo. (Consulte o [especificação SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=95176) para a lista de códigos de falha permitido e seus significados.) SOAP 1.1 tem um mecanismo ligeiramente diferentes: define quatro `faultCode` valores (por exemplo, o cliente e servidor) que podem ser estendidos definindo inteiramente novos ou usando a notação de ponto para criar mais específico `faultCodes`, por exemplo, Client.Authentication.  
  
 Quando você usa MessageFault a falhas do programa, o FaultCode.Name e FaultCode.Namespace mapeia para o nome e o namespace de SOAP 1.2 `env:Code` ou SOAP 1.1 `faultCode`. O FaultCode.SubCode é mapeado para `env:Subcode` para SOAP 1.2 e é nula para SOAP 1.1.  
  
 Você deve criar o novo subcódigos de falha (ou novos códigos de falha se usando SOAP 1.1) se é interessante distinguir programaticamente uma falha. Isso equivale a criar um novo tipo de exceção. Você deve evitar usar a notação de ponto com códigos de falha de SOAP 1.1. (O [WS-I Basic Profile](http://go.microsoft.com/fwlink/?LinkId=95177) também não recomenda o uso da notação de ponto de código de falha.)  
  
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
  
 O `Reason` propriedade corresponde do `env:Reason` (ou `faultString` em SOAP 1.1) uma descrição legível da condição de erro semelhante à mensagem da exceção. O `FaultReason` classe (e SOAP `env:Reason/faultString`) tem suporte interno para ter várias traduções para fins de globalização.  
  
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
  
 O conteúdo de detalhes de falha é exposto no MessageFault usando vários métodos incluindo o `GetDetail` \<T > e `GetReaderAtDetailContents`(). O detalhe da falha é um elemento opaco para carregar os detalhes adicionais sobre a falha. Isso é útil se houver alguns detalhes estruturado arbitrária que você deseja realizar com a falha.  
  
### <a name="generating-faults"></a>Gerar falhas  
 Esta seção explica o processo de geração de uma falha em resposta a uma condição de erro detectada em um canal ou em uma propriedade de mensagem criada pelo canal. Um exemplo típico está retornando uma falha em resposta a uma mensagem de solicitação que contém dados inválidos.  
  
 Ao gerar uma falha, o canal personalizado não deve enviar a falha diretamente, em vez disso, ele deve lançar uma exceção e permitir que a camada acima decidir se deve converter essa exceção em uma falha e como enviá-lo. Para ajudar nessa conversão, o canal deve fornecer um `FaultConverter` implementação que pode converter a exceção lançada pelo canal personalizado para a falha apropriada. `FaultConverter` é definido como:  
  
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
  
 Cada canal que gera falhas personalizadas deve implementar `FaultConverter` e retorná-lo de uma chamada para `GetProperty<FaultConverter>`. Personalizado `OnTryCreateFaultMessage` implementação deve converter a exceção em uma falha ou delegar para o canal interno `FaultConverter`. Se o canal é um transporte ele deve converter a exceção ou delegar para o codificador `FaultConverter` ou o padrão `FaultConverter` fornecido no WCF. O padrão `FaultConverter` converte erros correspondente ao especificado por WS-Addressing e SOAP de mensagens de falha. Aqui está um exemplo `OnTryCreateFaultMessage` implementação.  
  
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
  
 Uma implicação deste padrão é que exceções lançadas entre camadas para condições de erro que exigem falhas devem conter informações suficientes para o gerador de falhas correspondente criar o correto de falha. Como criar um canal personalizado, você pode definir os tipos de exceção que correspondem às condições de falha diferentes se essas exceções ainda não existir. Observe a exceções atravessando camadas de canal devem se comunicar a condição de erro em vez de dados de falhas opaco.  
  
### <a name="fault-categories"></a>Categorias de falhas  
 Geralmente há três categorias de falhas:  
  
1.  Falhas que são difundidas em toda a pilha inteira. Essas falhas podem ser encontradas em qualquer camada da pilha de canal, por exemplo InvalidCardinalityAddressingException.  
  
2.  Falhas que podem ser encontraram em qualquer lugar acima certa camada da pilha por exemplo, alguns erros que pertencem a uma transação que fluiu ou funções de segurança.  
  
3.  Falhas que são direcionadas a uma única camada da pilha, por exemplo erros como falhas de número de sequência WS-RM.  
  
 Categoria de 1. Falhas geralmente são WS-Addressing e falhas de SOAP. A base de `FaultConverter` classe fornecida pelo WCF converte erros correspondentes para mensagens de falha especificada pelo WS-Addressing e SOAP para que você não precisa lidar com conversão dessas exceções por conta própria.  
  
 Categoria de 2. Falhas ocorrem quando uma camada adiciona uma propriedade na mensagem que não consuma completamente informações de mensagem que pertencem a essa camada. Erros podem ser detectados mais tarde, quando a propriedade de mensagem para processar ainda mais informações sobre a mensagem de solicitar uma camada superior. Esses canais devem implementar o `GetProperty` especificado anteriormente para habilitar a camada superior devolver correto de falha. Um exemplo disso é o TransactionMessageProperty. Essa propriedade é adicionada à mensagem sem validar completamente todos os dados no cabeçalho (fazer isso pode envolver a entrar em contato com o coordenador de transações distribuídas (DTC).  
  
 Categoria de 3. Falhas só são geradas e enviadas por uma única camada no processador. Portanto, todas as exceções estão contidas dentro da camada. Para melhorar a consistência entre os canais e facilidade de manutenção, o canal personalizado deve usar o padrão especificado anteriormente para gerar mensagens de falha mesmo para falhas internas.  
  
### <a name="interpreting-received-faults"></a>Interpretando falhas recebidas  
 Esta seção fornece orientação para a geração de exceção apropriada ao receber uma mensagem de falha. A árvore de decisão para processar uma mensagem em cada camada da pilha é o seguinte:  
  
1.  Se a camada considera a mensagem a ser inválido, a camada deve fazer o seu processamento 'message inválido'. Esse processamento é específico à camada, mas pode incluir a descartar a mensagem de rastreamento, ou gerar uma exceção que é convertido em uma falha. Exemplos incluem segurança receber uma mensagem que não está protegida adequadamente ou RM receber uma mensagem com um número de sequência incorreta.  
  
2.  Caso contrário, se a mensagem é uma mensagem de falha que se aplicam especificamente à camada, e a mensagem não é significativa fora interação da camada, a camada deve lidar com a condição de erro. Um exemplo disso é uma falha recusado do RM sequência que não faz sentido para as camadas acima do canal do RM e que implica haver falha no canal RM e lançando a partir das operações pendentes.  
  
3.  Caso contrário, a mensagem deve ser retornada de Request() ou Receive(). Isso inclui os casos em que a camada reconhece a falha, mas a falha apenas indica que uma solicitação falha e não implica a haver falha no canal e lançando a partir das operações pendentes. Para melhorar a usabilidade, nesse caso, a camada deve implementar `GetProperty<FaultConverter>` e retornar um `FaultConverter` derivado da classe que pode converter a falha em uma exceção, substituindo `OnTryCreateException`.  
  
 O seguinte modelo de objeto oferece suporte a mensagens de conversão para exceções:  
  
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
  
 Uma camada de canal pode implementar `GetProperty<FaultConverter>` para oferecer suporte a mensagens de falha de conversão para exceções. Para fazer isso, substitua `OnTryCreateException` e verifique se a mensagem de falha. Se reconhecido, fazer a conversão, caso contrário, peça interna de canais para convertê-lo. Canais de transporte devem delegar ao `FaultConverter.GetDefaultFaultConverter` para obter o padrão FaultConverter SOAP/WS-Addressing.  
  
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
  
 Para condições de falha específico com cenários de recuperação diferentes, considere definir uma classe derivada de `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>Processamento de MustUnderstand  
 O SOAP define uma falha geral para sinalizar que um cabeçalho necessário não foi entendido pelo destinatário. Essa falha é conhecida como o `mustUnderstand` falha. No WCF, canais personalizados geram nunca `mustUnderstand` falhas. Em vez disso, o Dispatcher de WCF, que está localizado na parte superior da pilha de comunicação WCF, verifica que todos os cabeçalhos que foram marcados como MustUndestand = true foram entendidas pela pilha de subjacente. Se qualquer não foram entendidas, um `mustUnderstand` falha é gerada nesse ponto. (O usuário pode optar por desativar isso `mustUnderstand` processamento e que o aplicativo receber todos os cabeçalhos de mensagem. In that Case o aplicativo é responsável pela execução `mustUnderstand` processamento.) A falha gerada inclui um cabeçalho de NotUnderstood que contém os nomes de todos os cabeçalhos com MustUnderstand = true não foram entendidas.  
  
 Se o canal de protocolo envia um cabeçalho personalizado com MustUnderstand = true e recebe um `mustUnderstand` falha, ele deve descobrir se essa falha é devida ao cabeçalho enviado por ele. Existem dois membros de `MessageFault` classe são úteis para isso:  
  
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
  
 Se um canal emite um cabeçalho que está marcado como MustUnderstand = true, essa camada também deve implementar o padrão de API de geração de exceção e deve converter `mustUnderstand` falhas causadas por esse cabeçalho para uma exceção mais úteis, como descrito anteriormente.  
  
## <a name="tracing"></a>Rastreamento  
 O .NET Framework fornece um mecanismo para rastrear a execução de programa como uma forma de ajudar a diagnosticar aplicativos de produção ou problemas intermitentes onde não é possível simplesmente anexar um depurador e percorrer o código. Os componentes principais desse mecanismo estão no <xref:System.Diagnostics?displayProperty=nameWithType> namespace e consistem em:  
  
-   <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, que é a origem das informações de rastreamento a ser gravado, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, que é uma classe base abstrata para os ouvintes concretas que receberá as informações a serem rastreadas do <xref:System.Diagnostics.TraceSource> e enviá-lo para um destino específica do ouvinte. Por exemplo, <xref:System.Diagnostics.XmlWriterTraceListener> informações para um arquivo XML de rastreamento de saídas. Por fim, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, que permite que o usuário do aplicativo controlar o nível de detalhes de rastreamento e geralmente é especificado na configuração.  
  
-   Além dos componentes principais, você pode usar o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) exibir e pesquisar WCF rastreamentos. A ferramenta é projetada especificamente para arquivos de rastreamento gerados pelo WCF e gravadas usando <xref:System.Diagnostics.XmlWriterTraceListener>. A figura a seguir mostra os vários componentes envolvidos no rastreamento.  
  
 ![Tratando exceções e falhas](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Rastreamento de um canal personalizado  
 Canais personalizados devem gravar mensagens de rastreamento para auxiliar no diagnóstico de problemas quando não é possível anexar um depurador ao aplicativo em execução. Isso envolve duas tarefas de alto níveis: Criando um <xref:System.Diagnostics.TraceSource> e chamar seus métodos para gravar rastreamentos.  
  
 Ao instanciar um <xref:System.Diagnostics.TraceSource>, a cadeia de caracteres que você especificar se torna o nome dessa fonte. Esse nome é usado para configurar a origem de rastreamento de (nível de rastreamento de habilitar/desabilitar/set). Ele também aparece na saída em si. Canais personalizados devem usar um nome de origem exclusivo para ajudar os leitores a saída de rastreamento entender de onde vêm as informações de rastreamento. Usando o nome do assembly que está gravando as informações como o nome da fonte de rastreamento é uma prática comum. Por exemplo, o WCF usa o System. ServiceModel como a origem de rastreamento para obter informações gravadas do assembly System. ServiceModel.  
  
 Uma vez que uma origem de rastreamento, você chama seu <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, ou <xref:System.Diagnostics.TraceSource.TraceInformation%2A> métodos para gravar entradas de rastreamento para os ouvintes de rastreamento. Para cada entrada de rastreamento gravação, você precisa classificar o tipo de evento como um dos tipos de evento definidos no <xref:System.Diagnostics.TraceEventType>. Essa classificação e a configuração de nível de rastreamento na configuração de determinam se a entrada de rastreamento é enviado para o ouvinte. Por exemplo, definindo o nível de rastreamento na configuração para `Warning` permite `Warning`, `Error` e `Critical` entradas a serem gravados mas blocos de informações e detalhado de entradas de rastreamento. Aqui está um exemplo de instanciação de uma origem de rastreamento e gravar uma entrada no nível de informações:  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  É altamente recomendável que você especificar um nome de origem de rastreamento que é exclusivo para o canal personalizado para ajudar a entender de onde veio a saída de leitores de saída de rastreamento.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integração com o Visualizador de rastreamento  
 Rastreamentos gerados pelo seu canal podem ser a saída em um formato legível pelo [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) usando <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> como o ouvinte de rastreamento. Isso não é algo que você, como desenvolvedor de canal, precisa fazer. Em vez disso, ele é o usuário do aplicativo (ou a pessoa que o aplicativo de solução de problemas) que precisa configurar este ouvinte de rastreamento no arquivo de configuração do aplicativo. Por exemplo, a configuração a seguir gera informações de rastreamento de ambos <xref:System.ServiceModel?displayProperty=nameWithType> e `Microsoft.Samples.Udp` para o arquivo chamado `TraceEventsFile.e2e`:  
  
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
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> tem um <xref:System.Diagnostics.TraceSource.TraceData%2A> método que usa um ou mais objetos que devem ser incluídas na entrada de rastreamento. Em geral, o <xref:System.Object.ToString%2A?displayProperty=nameWithType> método é chamado em cada objeto e a cadeia de caracteres resultante é gravada como parte da entrada de rastreamento. Ao usar <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> para rastreamentos de saída, você pode passar um <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> como o objeto de dados <xref:System.Diagnostics.TraceSource.TraceData%2A>. A entrada de rastreamento resultante inclui o XML fornecido pelo <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Aqui está um exemplo de entrada com os dados de aplicativo XML:  
  
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
  
 O Visualizador de rastreamento do WCF entende o esquema do `TraceRecord` elemento mostrado anteriormente e extrai os dados de seus elementos filho e o exibe em um formato tabular. O canal deve usar esse esquema quando o rastreamento de dados de aplicativo estruturado para ajudar usuários Svctraceviewer.exe ler os dados.
