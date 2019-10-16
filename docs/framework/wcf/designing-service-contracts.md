---
title: Criando contratos de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 27f867bbf079c2e202d93425ddb951fc0df7784a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318389"
---
# <a name="designing-service-contracts"></a>Criando contratos de serviço
Este tópico descreve o que são contratos de serviço, como eles são definidos, quais operações estão disponíveis (e as implicações para as trocas de mensagens subjacentes), quais tipos de dados são usados e outros problemas que ajudam você a projetar operações que atendam às requisitos do seu cenário.  
  
## <a name="creating-a-service-contract"></a>Criando um contrato de serviço  
 Os serviços expõem várias operações. Em aplicativos Windows Communication Foundation (WCF), defina as operações criando um método e marcando-o com o atributo <xref:System.ServiceModel.OperationContractAttribute>. Em seguida, para criar um contrato de serviço, agrupe suas operações, seja declará-las em uma interface marcada com o atributo <xref:System.ServiceModel.ServiceContractAttribute> ou definindo-as em uma classe marcada com o mesmo atributo. (Para obter um exemplo básico, consulte [como definir um contrato de serviço](how-to-define-a-wcf-service-contract.md).)  
  
 Todos os métodos que não têm um atributo <xref:System.ServiceModel.OperationContractAttribute> não são operações de serviço e não são expostos pelos serviços WCF.  
  
 Este tópico descreve os seguintes pontos de decisão ao criar um contrato de serviço:  
  
- Se as classes ou interfaces devem ser usadas.  
  
- Como especificar os tipos de dados que você deseja trocar.  
  
- Os tipos de padrões do Exchange que você pode usar.  
  
- Se você pode fazer parte dos requisitos de segurança explícitos do contrato.  
  
- As restrições para entradas de operação e saídas.  
  
## <a name="classes-or-interfaces"></a>Classes ou interfaces  
 As classes e interfaces representam um agrupamento de funcionalidades e, portanto, ambas podem ser usadas para definir um contrato de serviço do WCF. No entanto, é recomendável que você use interfaces porque elas modelam diretamente os contratos de serviço. Sem uma implementação, as interfaces não são mais do que definir um agrupamento de métodos com determinadas assinaturas. Implemente uma interface de contrato de serviço e implemente um serviço WCF.  
  
 Todos os benefícios das interfaces gerenciadas se aplicam às interfaces de contrato de serviço:  
  
- As interfaces de contrato de serviço podem estender qualquer número de outras interfaces de contrato de serviço.  
  
- Uma única classe pode implementar qualquer número de contratos de serviço implementando essas interfaces de contrato de serviço.  
  
- Você pode modificar a implementação de um contrato de serviço alterando a implementação da interface, enquanto o contrato de serviço permanece o mesmo.  
  
- Você pode obter a versão de seu serviço implementando a interface antiga e a nova. Os clientes antigos se conectam à versão original, enquanto os clientes mais recentes podem se conectar à versão mais recente.  
  
> [!NOTE]
> Ao herdar de outras interfaces de contrato de serviço, não é possível substituir as propriedades da operação, como o nome ou o namespace. Se você tentar fazer isso, você criará uma nova operação no contrato de serviço atual.  
  
 Para obter um exemplo de como usar uma interface para criar um contrato de serviço, consulte [como: criar um serviço com uma interface de contrato](./feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 No entanto, você pode usar uma classe para definir um contrato de serviço e implementar esse contrato ao mesmo tempo. A vantagem de criar seus serviços aplicando <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> diretamente à classe e aos métodos na classe, respectivamente, é a velocidade e a simplicidade. As desvantagens são que as classes gerenciadas não dão suporte a várias heranças e, como resultado, elas só podem implementar um contrato de serviço por vez. Além disso, qualquer modificação nas assinaturas de classe ou de método modifica o contrato público para esse serviço, o que pode impedir que clientes não modificados usem seu serviço. Para obter mais informações, consulte [implementando contratos de serviço](implementing-service-contracts.md).  
  
 Para obter um exemplo que usa uma classe para criar um contrato de serviço e implementá-lo ao mesmo tempo, consulte [como: criar um serviço com uma classe de contrato](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 Neste ponto, você deve entender a diferença entre definir seu contrato de serviço usando uma interface e usando uma classe. A próxima etapa é decidir quais dados podem ser passados para frente e para trás entre um serviço e seus clientes.  
  
## <a name="parameters-and-return-values"></a>Parâmetros e valores de retorno  
 Cada operação tem um valor de retorno e um parâmetro, mesmo se eles forem `void`. No entanto, ao contrário de um método local, no qual você pode passar referências a objetos de um objeto para outro, as operações de serviço não passam referências a objetos. Em vez disso, eles passam cópias dos objetos.  
  
 Isso é significativo porque cada tipo usado em um parâmetro ou valor de retorno deve ser serializável; ou seja, deve ser possível converter um objeto desse tipo em um fluxo de bytes e de um fluxo de bytes em um objeto.  
  
 Os tipos primitivos são serializáveis por padrão, pois são muitos tipos na .NET Framework.  
  
> [!NOTE]
> O valor dos nomes de parâmetro na assinatura de operação faz parte do contrato e diferencia maiúsculas de minúsculas. Se você quiser usar o mesmo nome de parâmetro localmente, mas modificar o nome nos metadados publicados, consulte o <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Contratos de dados  
 Aplicativos orientados a serviços como os aplicativos Windows Communication Foundation (WCF) são projetados para interoperar com o número mais amplo possível de aplicativos cliente em plataformas Microsoft e não Microsoft. Para a maior interoperabilidade possível, é recomendável que você marque seus tipos com os atributos <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> para criar um contrato de dados, que é a parte do contrato de serviço que descreve os dados trocados por suas operações de serviço.  
  
 Os contratos de dados são contratos de estilo de aceitação: nenhum tipo ou membro de dados é serializado, a menos que você aplique explicitamente o atributo de contrato de dados. Os contratos de dados não estão relacionados ao escopo de acesso do código gerenciado: os membros de dados privados podem ser serializados e enviados em outro lugar para serem acessados publicamente. (Para obter um exemplo básico de um contrato de dados, consulte [como: criar um contrato de dados básico para uma classe ou estrutura](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) O WCF lida com a definição das mensagens SOAP subjacentes que habilitam a funcionalidade da operação, bem como a serialização de seus tipos de dados para dentro e fora do corpo das mensagens. Desde que os tipos de dados sejam serializáveis, você não precisa pensar na infraestrutura de troca de mensagens subjacente ao projetar suas operações.  
  
 Embora o aplicativo WCF típico use os atributos <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> para criar contratos de dados para operações, você pode usar outros mecanismos de serialização. Os mecanismos padrão <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> e <xref:System.Xml.Serialization.IXmlSerializable> funcionam para lidar com a serialização de seus tipos de dados nas mensagens SOAP subjacentes que os transportam de um aplicativo para outro. Você poderá empregar estratégias de serialização se seus tipos de dados exigirem suporte especial. Para obter mais informações sobre as opções de serialização de tipos de dados em aplicativos WCF, consulte [especificando transferência de dados em contratos de serviço](./feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapeando parâmetros e valores de retorno para trocas de mensagens  
 As operações de serviço têm suporte por uma troca subjacente de mensagens SOAP que transferem dados de aplicativos de volta e para trás, além dos dados exigidos pelo aplicativo para dar suporte a determinados recursos relacionados à segurança, à transação e à sessão padrão. Como esse é o caso, a assinatura de uma operação de serviço determina um determinado *padrão de troca de mensagens* (MEP) que pode dar suporte à transferência de dados e aos recursos que uma operação requer. Você pode especificar três padrões no modelo de programação do WCF: padrões de mensagens de solicitação/resposta, unidirecional e duplex.  
  
##### <a name="requestreply"></a>Solicitação/resposta  
 Um padrão de solicitação/resposta é aquele em que um remetente de solicitação (um aplicativo cliente) recebe uma resposta com a qual a solicitação está correlacionada. Esse é o MEP padrão porque oferece suporte a uma operação na qual um ou mais parâmetros são passados para a operação e um valor de retorno é passado de volta para o chamador. Por exemplo, o exemplo C# de código a seguir mostra uma operação básica de serviço que usa uma cadeia de caracteres e retorna uma cadeia de caracteres.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Este é o código de Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Essa assinatura de operação determina a forma de troca de mensagens subjacente. Se nenhuma correlação existir, o WCF não poderá determinar para qual operação o valor de retorno é pretendido.  
  
 Observe que, a menos que você especifique um padrão de mensagem subjacente diferente, até mesmo as operações de serviço que retornam `void` (`Nothing` em Visual Basic) são trocas de mensagens de solicitação/resposta. O resultado de sua operação é que, a menos que um cliente invoque a operação de forma assíncrona, o cliente parará de processar até que a mensagem de retorno seja recebida, mesmo que essa mensagem esteja vazia no caso normal. O exemplo C# de código a seguir mostra uma operação que não retorna até que o cliente tenha recebido uma mensagem vazia em resposta.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Este é o código de Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 O exemplo anterior pode reduzir o desempenho e a capacidade de resposta do cliente se a operação levar muito tempo para ser executada, mas houver vantagens para as operações de solicitação/resposta mesmo quando elas retornam `void`. O mais óbvio é que as falhas de SOAP podem ser retornadas na mensagem de resposta, o que indica que ocorreu alguma condição de erro relacionada ao serviço, seja em caso de comunicação ou processamento. As falhas de SOAP especificadas em um contrato de serviço são passadas para o aplicativo cliente como um objeto <xref:System.ServiceModel.FaultException%601>, em que o parâmetro de tipo é o tipo especificado no contrato de serviço. Isso torna fácil notificar os clientes sobre as condições de erro nos serviços WCF. Para obter mais informações sobre exceções, falhas de SOAP e tratamento de erros, consulte [especificando e manipulando falhas em contratos e serviços](specifying-and-handling-faults-in-contracts-and-services.md). Para ver um exemplo de um serviço de solicitação/resposta e cliente, consulte [como: criar um contrato de solicitação-resposta](./feature-details/how-to-create-a-request-reply-contract.md). Para obter mais informações sobre problemas com o padrão de solicitação-resposta, consulte [serviços de solicitação-resposta](./feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Unidirecional  
 Se o cliente de um aplicativo de serviço WCF não deve aguardar a conclusão da operação e não processar falhas de SOAP, a operação poderá especificar um padrão de mensagem unidirecional. Uma operação unidirecional é aquela na qual um cliente invoca uma operação e continua o processamento depois que o WCF grava a mensagem na rede. Normalmente, isso significa que, a menos que os dados enviados na mensagem de saída sejam extremamente grandes, o cliente continua sendo executado quase imediatamente (a menos que haja um erro ao enviar os dados). Esse tipo de padrão de troca de mensagens dá suporte ao comportamento de evento de um cliente para um aplicativo de serviço.  
  
 Uma troca de mensagens na qual uma mensagem é enviada e nenhuma é recebida não dá suporte a uma operação de serviço que especifica um valor de retorno diferente de `void`; Nesse caso, uma exceção <xref:System.InvalidOperationException> é lançada.  
  
 Nenhuma mensagem de retorno também significa que não pode haver nenhuma falha de SOAP retornada para indicar erros no processamento ou na comunicação. (Comunicar informações de erro quando as operações são operações unidirecionais requer um padrão de troca de mensagens duplex.)  
  
 Para especificar uma troca de mensagens unidirecional para uma operação que retorna `void`, defina a propriedade <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> como `true`, como no exemplo C# de código a seguir.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Este é o código de Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Esse método é idêntico ao exemplo de solicitação/resposta anterior, mas a definição da propriedade <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> como `true` significa que, embora o método seja idêntico, a operação de serviço não envia uma mensagem de retorno e os clientes retornam imediatamente após a saída a mensagem foi enviada para a camada de canal. Para obter um exemplo, consulte [como: criar um contrato unidirecional](./feature-details/how-to-create-a-one-way-contract.md). Para obter mais informações sobre o padrão unidirecional, consulte [Serviços unidirecionais](./feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Duplex  
 Um padrão duplex é caracterizado pela capacidade do serviço e do cliente de enviar mensagens entre si independentemente, seja usando mensagens unidirecionais ou de solicitação/resposta. Essa forma de comunicação bidirecional é útil para serviços que devem se comunicar diretamente com o cliente ou para fornecer uma experiência assíncrona a qualquer lado de uma troca de mensagens, incluindo comportamento semelhante a eventos.  
  
 O padrão duplex é um pouco mais complexo do que os padrões de solicitação/resposta ou unidirecional devido ao mecanismo adicional de comunicação com o cliente.  
  
 Para criar um contrato duplex, você também deve criar um contrato de retorno de chamada e atribuir o tipo desse contrato de retorno de chamada à propriedade <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> do atributo <xref:System.ServiceModel.ServiceContractAttribute> que marca seu contrato de serviço.  
  
 Para implementar um padrão duplex, você deve criar uma segunda interface que contenha as declarações de método que são chamadas no cliente.  
  
 Para obter um exemplo de como criar um serviço e um cliente que acessa esse serviço, consulte [como: criar um contrato duplex](./feature-details/how-to-create-a-duplex-contract.md) e [como acessar serviços com um contrato duplex](./feature-details/how-to-access-services-with-a-duplex-contract.md). Para obter um exemplo funcional, consulte [duplex](./samples/duplex.md). Para obter mais informações sobre problemas usando contratos duplex, consulte [Serviços duplex](./feature-details/duplex-services.md).  
  
> [!CAUTION]
> Quando um serviço recebe uma mensagem duplex, ele examina o elemento `ReplyTo` na mensagem de entrada para determinar para onde enviar a resposta. Se o canal usado para receber a mensagem não estiver protegido, um cliente não confiável poderá enviar uma mensagem mal-intencionada com o `ReplyTo` de um computador de destino, levando a uma negação de serviço (DOS) desse computador de destino.  
  
##### <a name="out-and-ref-parameters"></a>Parâmetros out e ref  
 Na maioria dos casos, você pode usar parâmetros `in` (`ByVal` em Visual Basic) e os parâmetros `out` e `ref` (`ByRef` em Visual Basic). Como os parâmetros `out` e `ref` indicam que os dados são retornados de uma operação, uma assinatura de operação como a seguinte especifica que uma operação de solicitação/resposta é necessária, mesmo que a assinatura de operação retorne `void`.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Este é o código de Visual Basic equivalente.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 As únicas exceções são os casos em que sua assinatura tem uma estrutura específica. Por exemplo, você pode usar a associação <xref:System.ServiceModel.NetMsmqBinding> para se comunicar com clientes somente se o método usado para declarar uma operação retornar `void`; Não pode haver nenhum valor de saída, seja um valor de retorno, `ref` ou parâmetro `out`.  
  
 Além disso, o uso de parâmetros `out` ou `ref` requer que a operação tenha uma mensagem de resposta subjacente para executar o objeto modificado. Se a operação for uma operação unidirecional, uma exceção <xref:System.InvalidOperationException> será lançada em tempo de execução.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Especificar o nível de proteção da mensagem no contrato  
 Ao criar seu contrato, você também deve decidir o nível de proteção de mensagem dos serviços que implementam seu contrato. Isso será necessário apenas se a segurança da mensagem for aplicada à associação no ponto de extremidade do contrato. Se a associação tiver a segurança desativada (ou seja, se a associação fornecida pelo sistema definir o <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> para o valor <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>), você não precisará decidir sobre o nível de proteção da mensagem para o contrato. Na maioria dos casos, as associações fornecidas pelo sistema com segurança em nível de mensagem aplicada fornecem um nível de proteção suficiente e você não precisa considerar o nível de proteção para cada operação ou para cada mensagem.  
  
 O nível de proteção é um valor que especifica se as mensagens (ou partes da mensagem) que dão suporte a um serviço são assinadas, assinadas e criptografadas ou enviadas sem assinaturas ou criptografia. O nível de proteção pode ser definido em vários escopos: no nível de serviço, para uma operação específica, para uma mensagem dentro dessa operação ou para uma parte de mensagem. Os valores definidos em um escopo se tornam o valor padrão para escopos menores, a menos que sejam substituídos explicitamente. Se uma configuração de associação não puder fornecer o nível mínimo de proteção necessário para o contrato, uma exceção será lançada. E quando nenhum valor de nível de proteção for explicitamente definido no contrato, a configuração de associação controlará o nível de proteção para todas as mensagens se a associação tiver segurança de mensagem. Este é o comportamento padrão.  
  
> [!IMPORTANT]
> Decidir se deve definir explicitamente vários escopos de um contrato para menos do que o nível de proteção total de <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> é geralmente uma decisão que compensa algum grau de segurança para aumentar o desempenho. Nesses casos, suas decisões devem girar em volta das operações e do valor dos dados que eles trocam. Para obter mais informações, consulte [Securing Services](securing-services.md).  
  
 Por exemplo, o exemplo de código a seguir não define a propriedade <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> ou <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> no contrato.  
  
```csharp  
[ServiceContract]  
public interface ISampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute]  
  public int GetInt();    
}  
```  
  
 Este é o código de Visual Basic equivalente.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Ao interagir com uma implementação `ISampleService` em um ponto de extremidade com um @no__t padrão-1 (o @no__t padrão-2, que é <xref:System.ServiceModel.SecurityMode.Message>), todas as mensagens são criptografadas e assinadas porque esse é o nível de proteção padrão. No entanto, quando um serviço `ISampleService` é usado com um @no__t padrão-1 (o @no__t padrão-2, que é <xref:System.ServiceModel.SecurityMode.None>), todas as mensagens são enviadas como texto porque não há segurança para essa associação e, portanto, o nível de proteção é ignorado (ou seja, as mensagens não são criptografadas nem assinado). Se o <xref:System.ServiceModel.SecurityMode> tiver sido alterado para <xref:System.ServiceModel.SecurityMode.Message>, essas mensagens seriam criptografadas e assinadas (porque isso seria o nível de proteção padrão da associação).  
  
 Se você quiser especificar ou ajustar explicitamente os requisitos de proteção para seu contrato, defina a propriedade <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> (ou qualquer uma das propriedades `ProtectionLevel` em um escopo menor) para o nível que seu contrato de serviço requer. Nesse caso, o uso de uma configuração explícita requer a associação para dar suporte a essa configuração no mínimo para o escopo usado. Por exemplo, o exemplo de código a seguir especifica um valor <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> explicitamente para a operação `GetGuid`.  
  
```csharp  
[ServiceContract]  
public interface IExplicitProtectionLevelSampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.None)]  
  public int GetInt();    
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
  public int GetGuid();    
}  
```  
  
 Este é o código de Visual Basic equivalente.  
  
```vb  
<ServiceContract()> _   
Public Interface IExplicitProtectionLevelSampleService   
    <OperationContract()> _   
    Public Function GetString() As String   
    End Function   
  
    <OperationContract(ProtectionLevel := ProtectionLevel.None)> _   
    Public Function GetInt() As Integer   
    End Function   
  
    <OperationContractAttribute(ProtectionLevel := ProtectionLevel.EncryptAndSign)> _   
    Public Function GetGuid() As Integer   
    End Function   
  
End Interface  
```  
  
 Um serviço que implementa esse contrato `IExplicitProtectionLevelSampleService` e tem um ponto de extremidade que usa o @no__t padrão-1 (o @no__t padrão-2, que é <xref:System.ServiceModel.SecurityMode.Message>) tem o seguinte comportamento:  
  
- As mensagens de operação `GetString` são criptografadas e assinadas.  
  
- As mensagens de operação `GetInt` são enviadas como texto não criptografado e não assinado (ou seja, sem formatação).  
  
- A operação `GetGuid` <xref:System.Guid?displayProperty=nameWithType> é retornada em uma mensagem criptografada e assinada.  
  
 Para obter mais informações sobre os níveis de proteção e como usá-los, consulte [noções básicas sobre o nível de proteção](understanding-protection-level.md). Para obter mais informações sobre segurança, consulte [protegendo serviços](securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Outros requisitos de assinatura de operação  
 Alguns recursos de aplicativo exigem um tipo específico de assinatura de operação. Por exemplo, a associação <xref:System.ServiceModel.NetMsmqBinding> dá suporte a serviços e clientes duráveis, nos quais um aplicativo pode ser reiniciado no meio da comunicação e retomar de onde parou sem nenhuma mensagem. (Para obter mais informações, consulte [filas no WCF](./feature-details/queues-in-wcf.md).) No entanto, as operações duráveis devem usar apenas um parâmetro `in` e não ter nenhum valor de retorno.  
  
 Outro exemplo é o uso de tipos <xref:System.IO.Stream> em operações. Como o parâmetro <xref:System.IO.Stream> inclui o corpo da mensagem inteiro, se uma entrada ou uma saída (ou seja, parâmetro `ref`, parâmetro `out` ou valor de retorno) for do tipo <xref:System.IO.Stream>, ela deverá ser a única entrada ou saída especificada em sua operação. Além disso, o parâmetro ou o tipo de retorno deve ser <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> ou <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Para obter mais informações sobre fluxos, consulte [grandes dados e streaming](./feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Nomes, namespaces e ofuscação  
 Os nomes e namespaces dos tipos .NET na definição de contratos e operações são significativos quando os contratos são convertidos em WSDL e quando as mensagens de contrato são criadas e enviadas. Portanto, é altamente recomendável que os nomes e namespaces do contrato de serviço sejam definidos explicitamente usando as propriedades `Name` e `Namespace` de todos os atributos de contrato de suporte, como os contratos <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.Runtime.Serialization.DataMemberAttribute> e outro contrato atributos.  
  
 Um resultado disso é que, se os nomes e namespaces não estiverem definidos explicitamente, o uso de ofuscação de IL no assembly altera os nomes e namespaces de tipo de contrato e resulta em trocas WSDL e de transmissão modificadas que normalmente falham. Se você não definir os nomes de contrato e os namespaces explicitamente, mas pretende usar a ofuscação, use os atributos <xref:System.Reflection.ObfuscationAttribute> e <xref:System.Reflection.ObfuscateAssemblyAttribute> para evitar a modificação dos nomes e namespaces de tipo de contrato.  
  
## <a name="see-also"></a>Consulte também

- [Como criar um contrato de solicitação-resposta](./feature-details/how-to-create-a-request-reply-contract.md)
- [Como criar um contrato unidirecional](./feature-details/how-to-create-a-one-way-contract.md)
- [Como criar um contrato duplex](./feature-details/how-to-create-a-duplex-contract.md)
- [Especificando transferência de dados em contratos de serviço](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [Especificando e lidando com falhas em contratos e serviços](specifying-and-handling-faults-in-contracts-and-services.md)
- [Usando sessões](using-sessions.md)
- [Operações síncronas e assíncronas](synchronous-and-asynchronous-operations.md)
- [Serviços confiáveis](reliable-services.md)
- [Serviços e transações](services-and-transactions.md)
