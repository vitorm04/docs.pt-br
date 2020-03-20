---
title: Criando contratos de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 37723011d69e8ea2ead3f7a30a30898dede054cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176676"
---
# <a name="designing-service-contracts"></a>Criando contratos de serviço
Este tópico descreve o que são contratos de serviço, como eles são definidos, quais operações estão disponíveis (e as implicações para as trocas de mensagens subjacentes), quais tipos de dados são usados e outras questões que ajudam você a projetar operações que satisfaçam o requisitos de seu cenário.  
  
## <a name="creating-a-service-contract"></a>Criando um contrato de serviço  
 Os serviços expõem uma série de operações. Nos aplicativos da Windows Communication Foundation (WCF), defina as operações criando um método e marcando-o com o atributo. <xref:System.ServiceModel.OperationContractAttribute> Em seguida, para criar um contrato de serviço, agrupe suas <xref:System.ServiceModel.ServiceContractAttribute> operações, seja declarando-as dentro de uma interface marcada com o atributo, ou definindo-as em uma classe marcada com o mesmo atributo. (Para um exemplo básico, [consulte Como definir um contrato de serviço](how-to-define-a-wcf-service-contract.md).)  
  
 Todos os métodos que <xref:System.ServiceModel.OperationContractAttribute> não possuem um atributo não são operações de serviço e não são expostos por serviços WCF.  
  
 Este tópico descreve os seguintes pontos de decisão ao projetar um contrato de serviço:  
  
- Seja para usar classes ou interfaces.  
  
- Como especificar os tipos de dados que deseja trocar.  
  
- Os tipos de padrões de troca que você pode usar.  
  
- Se você pode fazer requisitos de segurança explícitos parte do contrato.  
  
- As restrições para entradas e saídas de operação.  
  
## <a name="classes-or-interfaces"></a>Classes ou Interfaces  
 Ambas as classes e interfaces representam um agrupamento de funcionalidades e, portanto, ambas podem ser usadas para definir um contrato de serviço WCF. No entanto, recomenda-se que você use interfaces porque eles modelam diretamente contratos de serviço. Sem uma implementação, as interfaces não fazem mais do que definir um agrupamento de métodos com certas assinaturas. Implemente uma interface de contrato de serviço e você implementou um serviço WCF.  
  
 Todos os benefícios das interfaces gerenciadas se aplicam às interfaces de contrato de serviço:  
  
- Interfaces de contrato de serviço podem estender qualquer número de outras interfaces de contrato de serviço.  
  
- Uma única classe pode implementar qualquer número de contratos de serviço implementando essas interfaces de contrato de serviço.  
  
- Você pode modificar a implementação de um contrato de serviço alterando a implementação da interface, enquanto o contrato de serviço permanece o mesmo.  
  
- Você pode versácia seu serviço implementando a interface antiga e a nova. Clientes antigos se conectam à versão original, enquanto clientes mais novos podem se conectar à versão mais recente.  
  
> [!NOTE]
> Ao herdar de outras interfaces de contrato de serviço, você não pode substituir propriedades de operação, como o nome ou namespace. Se você tentar fazê-lo, você cria uma nova operação no contrato de serviço atual.  
  
 Para um exemplo de usar uma interface para criar um contrato de serviço, consulte [Como: Criar um serviço com uma interface de contrato](./feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Você pode, no entanto, usar uma classe para definir um contrato de serviço e implementar esse contrato ao mesmo tempo. A vantagem de criar seus <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> serviços aplicando e diretamente à classe e aos métodos da classe, respectivamente, é a rapidez e a simplicidade. As desvantagens são que as classes gerenciadas não suportam herança múltipla e, como resultado, só podem implementar um contrato de serviço por vez. Além disso, qualquer modificação nas assinaturas de classe ou método modifica o contrato público para esse serviço, o que pode impedir que clientes não modificados usem seu serviço. Para obter mais informações, consulte [Implementando Contratos de Serviços](implementing-service-contracts.md).  
  
 Para um exemplo que usa uma classe para criar um contrato de serviço e implementá-lo ao mesmo tempo, consulte [Como: Criar um serviço com uma classe de contrato](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 Neste ponto, você deve entender a diferença entre definir seu contrato de serviço usando uma interface e usando uma classe. O próximo passo é decidir quais dados podem ser passados para frente e para trás entre um serviço e seus clientes.  
  
## <a name="parameters-and-return-values"></a>Parâmetros e Valores de Retorno  
 Cada operação tem um valor de retorno e `void`um parâmetro, mesmo que estes sejam . No entanto, ao contrário de um método local, no qual você pode passar referências a objetos de um objeto para outro, as operações de serviço não passam referências a objetos. Em vez disso, eles passam cópias dos objetos.  
  
 Isso é significativo porque cada tipo usado em um parâmetro ou valor de retorno deve ser serializável; ou seja, deve ser possível converter um objeto desse tipo em um fluxo de bytes e de um fluxo de bytes em um objeto.  
  
 Os tipos primitivos são serializáveis por padrão, assim como muitos tipos no Quadro .NET.  
  
> [!NOTE]
> O valor dos nomes dos parâmetros na assinatura da operação faz parte do contrato e são sensíveis a maiúsculas e minúsculas. Se você quiser usar o mesmo nome de parâmetro localmente, mas <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>modificar o nome nos metadados publicados, consulte o .  
  
#### <a name="data-contracts"></a>Contratos de dados  
 Aplicativos orientados a serviços, como os aplicativos do Windows Communication Foundation (WCF), são projetados para interagir com o maior número possível de aplicativos clientes em plataformas Microsoft e não-Microsoft. Para a maior interoperabilidade possível, recomenda-se que você <xref:System.Runtime.Serialization.DataContractAttribute> marque seus tipos com os atributos para <xref:System.Runtime.Serialization.DataMemberAttribute> criar um contrato de dados, que é a parte do contrato de serviço que descreve os dados que suas operações de serviço trocam.  
  
 Os contratos de dados são contratos de estilo opt-in: Nenhum tipo ou membro de dados é serializado, a menos que você aplique explicitamente o atributo do contrato de dados. Os contratos de dados não estão relacionados com o escopo de acesso do código gerenciado: os membros de dados privados podem ser serializados e enviados para outros lugares para serem acessados publicamente. (Para um exemplo básico de um contrato de dados, consulte [Como: Criar um contrato básico de dados para uma classe ou estrutura](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) O WCF lida com a definição das mensagens SOAP subjacentes que permitem a funcionalidade da operação, bem como a serialização de seus tipos de dados dentro e fora do corpo das mensagens. Enquanto seus tipos de dados forem serializáveis, você não precisa pensar na infra-estrutura de troca de mensagens subjacente ao projetar suas operações.  
  
 Embora o aplicativo WCF <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> típico use os atributos e atributos para criar contratos de dados para operações, você pode usar outros mecanismos de serialização. O <xref:System.Runtime.Serialization.ISerializable>padrão <xref:System.SerializableAttribute> <xref:System.Xml.Serialization.IXmlSerializable> e os mecanismos funcionam para lidar com a serialização de seus tipos de dados nas mensagens SOAP subjacentes que as transportam de um aplicativo para outro. Você pode empregar mais estratégias de serialização se seus tipos de dados precisarem de suporte especial. Para obter mais informações sobre as opções de serialização de tipos de dados em aplicativos WCF, consulte [Especificando transferência de dados em contratos de serviço](./feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapeamento de parâmetros e valores de retorno para trocas de mensagens  
 As operações de serviço são suportadas por uma troca subjacente de mensagens SOAP que transferem dados do aplicativo para frente e para trás, além dos dados necessários pelo aplicativo para suportar certos recursos padrão de segurança, transação e sessão. Por se trata, a assinatura de uma operação de serviço dita um certo padrão de *troca de mensagens* (MEP) subjacente que pode suportar a transferência de dados e os recursos que uma operação requer. Você pode especificar três padrões no modelo de programação WCF: solicitação/resposta, padrão de mensagens unidirecionais e duplex.  
  
##### <a name="requestreply"></a>Solicitação/Resposta  
 Um padrão de solicitação/resposta é aquele em que um remetente de solicitação (um aplicativo cliente) recebe uma resposta com a qual a solicitação está correlacionada. Este é o MEP padrão porque suporta uma operação na qual um ou mais parâmetros são passados para a operação e um valor de retorno é repassado ao chamador. Por exemplo, o exemplo de código C# a seguir mostra uma operação de serviço básico que pega uma seqüência e retorna uma seqüência.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 A seguir está o código Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Esta assinatura de operação dita a forma de troca de mensagens subjacente. Se não houver correlação, o WCF não pode determinar para qual operação o valor de retorno é destinado.  
  
 Observe que, a menos que você especifique `void` `Nothing` um padrão de mensagem subjacente diferente, até mesmo as operações de serviço que retornam (no Visual Basic) são trocas de mensagens de solicitação/resposta. O resultado para sua operação é que, a menos que um cliente invoque a operação de forma assíncrona, o cliente pára de processar até que a mensagem de retorno seja recebida, mesmo que essa mensagem esteja vazia no caso normal. O exemplo de código C# a seguir mostra uma operação que não retorna até que o cliente tenha recebido uma mensagem vazia em resposta.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 A seguir está o código Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 O exemplo anterior pode retardar o desempenho e a capacidade de resposta do cliente se a operação `void`demorar muito tempo para ser realizada, mas há vantagens para solicitar/responder operações mesmo quando eles retornam . O mais óbvio é que as falhas soap podem ser devolvidas na mensagem de resposta, o que indica que alguma condição de erro relacionada ao serviço ocorreu, seja na comunicação ou no processamento. As falhas de SABÃO especificadas em um contrato de <xref:System.ServiceModel.FaultException%601> serviço são passadas ao aplicativo do cliente como objeto, onde o parâmetro de tipo é o tipo especificado no contrato de serviço. Isso facilita a notificação dos clientes sobre as condições de erro nos serviços wcf. Para obter mais informações sobre exceções, falhas de SABÃO e manipulação de erros, consulte [Especificar e lidar com falhas em Contratos e Serviços](specifying-and-handling-faults-in-contracts-and-services.md). Para ver um exemplo de um serviço de solicitação/resposta e cliente, consulte [Como: Criar um Contrato de Solicitação e Resposta](./feature-details/how-to-create-a-request-reply-contract.md). Para obter mais informações sobre problemas com o padrão solicitação-resposta, consulte [Request-Reply Services](./feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Unidirecional  
 Se o cliente de um aplicativo de serviço WCF não deve esperar que a operação seja concluída e não processar falhas soap, a operação pode especificar um padrão de mensagem unidirecional. Uma operação unidirecional é aquela em que um cliente invoca uma operação e continua processando após o WCF escrever a mensagem para a rede. Normalmente, isso significa que, a menos que os dados enviados na mensagem de saída sejam extremamente grandes, o cliente continua sendo executado quase imediatamente (a menos que haja um erro no envio dos dados). Esse tipo de padrão de troca de mensagens suporta o comportamento semelhante a um evento de um cliente para um aplicativo de serviço.  
  
 Uma troca de mensagens na qual uma mensagem é enviada e nenhuma `void`é recebida não pode suportar uma operação de serviço que especifique um valor de retorno diferente de ; neste caso, <xref:System.InvalidOperationException> uma exceção é lançada.  
  
 Nenhuma mensagem de retorno também significa que não pode haver nenhuma falha SOAP retornada para indicar quaisquer erros no processamento ou comunicação. (Comunicar informações de erro quando as operações são operações unidirecionais requer um padrão de troca de mensagens duplex.)  
  
 Para especificar uma troca de mensagens `void`unidirecionais para uma operação que retorna, defina a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade para `true`, como no exemplo de código C# a seguir.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 A seguir está o código Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Este método é idêntico ao exemplo anterior de <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> solicitação/resposta, mas definir a propriedade significa `true` que, embora o método seja idêntico, a operação de serviço não envia uma mensagem de retorno e os clientes retornam imediatamente uma vez que a mensagem de saída tenha sido entregue à camada do canal. Por exemplo, [veja Como: Criar um contrato unidirecional](./feature-details/how-to-create-a-one-way-contract.md). Para obter mais informações sobre o padrão unidirecional, consulte [Serviços unidirecionais](./feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Duplex  
 Um padrão duplex é caracterizado pela capacidade do serviço e do cliente de enviar mensagens entre si de forma independente, seja usando mensagens unidirecionais ou de solicitação/resposta. Esta forma de comunicação bidirecional é útil para serviços que devem se comunicar diretamente com o cliente ou para fornecer uma experiência assíncrona para ambos os lados de uma troca de mensagens, incluindo comportamento semelhante a um evento.  
  
 O padrão duplex é um pouco mais complexo do que os padrões de solicitação/resposta ou unidirecional devido ao mecanismo adicional de comunicação com o cliente.  
  
 Para projetar um contrato duplex, você também deve projetar um contrato de retorno <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> de <xref:System.ServiceModel.ServiceContractAttribute> chamada e atribuir o tipo desse contrato de retorno à propriedade do atributo que marca o seu contrato de serviço.  
  
 Para implementar um padrão duplex, você deve criar uma segunda interface que contenha as declarações de método que são chamadas ao cliente.  
  
 Para um exemplo de criação de um serviço, e um cliente que acessa esse serviço, consulte [Como: Criar um Contrato Duplex](./feature-details/how-to-create-a-duplex-contract.md) e [Como: Acessar Serviços com um Contrato Duplex](./feature-details/how-to-access-services-with-a-duplex-contract.md). Para obter uma amostra de trabalho, consulte [Duplex](./samples/duplex.md). Para obter mais informações sobre problemas usando contratos duplex, consulte [Serviços Duplex](./feature-details/duplex-services.md).  
  
> [!CAUTION]
> Quando um serviço recebe uma mensagem `ReplyTo` duplex, ele olha para o elemento nessa mensagem recebida para determinar para onde enviar a resposta. Se o canal usado para receber a mensagem não for protegido, um cliente não `ReplyTo`confiável poderá enviar uma mensagem maliciosa com uma máquina de destino, levando a uma negação de serviço (DOS) dessa máquina de destino.  
  
##### <a name="out-and-ref-parameters"></a>Parâmetros de saída e ref  
 Na maioria dos casos, você pode usar `in` parâmetros (no`ByVal` Visual Basic) e `out` `ref` parâmetros (no`ByRef` Visual Basic). Como `out` ambos `ref` e parâmetros indicam que os dados são retornados de uma operação, uma assinatura de operação `void`como a seguinte especifica que uma operação de solicitação/resposta é necessária mesmo que a assinatura da operação retorne .  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 A seguir está o código Visual Basic equivalente.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 As únicas exceções são os casos em que sua assinatura tem uma estrutura particular. Por exemplo, você <xref:System.ServiceModel.NetMsmqBinding> pode usar a vinculação para se comunicar `void`com os clientes somente se o método usado para declarar uma operação retornar ; não pode haver valor de saída, se `ref`é `out` um valor de retorno, ou parâmetro.  
  
 Além disso, `out` `ref` o uso ou parâmetros requer que a operação tenha uma mensagem de resposta subjacente para transportar de volta o objeto modificado. Se a sua operação for unidirecional, uma exceção <xref:System.InvalidOperationException> é lançada em tempo de execução.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Especificar o nível de proteção de mensagens no contrato  
 Ao projetar seu contrato, você também deve decidir o nível de proteção de mensagens dos serviços que implementam seu contrato. Isso só é necessário se a segurança da mensagem for aplicada à vinculação no ponto final do contrato. Se a vinculação tiver a segurança desligada (isto <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> é, <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>se a vinculação fornecida pelo sistema definir o valor ) então você não terá que decidir sobre o nível de proteção de mensagens para o contrato. Na maioria dos casos, as vinculações fornecidas pelo sistema com segurança em nível de mensagem aplicada fornecem um nível de proteção suficiente e você não precisa considerar o nível de proteção para cada operação ou para cada mensagem.  
  
 O nível de proteção é um valor que especifica se as mensagens (ou partes de mensagem) que suportam um serviço são assinadas, assinadas e criptografadas ou enviadas sem assinaturas ou criptografia. O nível de proteção pode ser definido em vários escopos: no nível de serviço, para uma operação específica, para uma mensagem dentro dessa operação ou uma parte de mensagem. Os valores definidos em um escopo tornam-se o valor padrão para escopos menores, a menos que explicitamente substituídos. Se uma configuração vinculante não puder fornecer o nível mínimo de proteção necessário para o contrato, uma exceção será lançada. E quando nenhum valor de nível de proteção é explicitamente definido no contrato, a configuração vinculante controla o nível de proteção de todas as mensagens se a vinculação tiver segurança de mensagem. Esse é o comportamento padrão.  
  
> [!IMPORTANT]
> Decidir se definir explicitamente vários escopos de um contrato para <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> menos do que o nível de proteção total é geralmente uma decisão que negocia algum grau de segurança para um maior desempenho. Nesses casos, suas decisões devem girar em torno de suas operações e do valor dos dados que eles trocam. Para obter mais informações, consulte [Protegendo serviços](securing-services.md).  
  
 Por exemplo, o exemplo de código <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> a <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> seguir não define nem a propriedade no contrato.  
  
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
  
 A seguir está o código Visual Basic equivalente.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Ao interagir com `ISampleService` uma implementação em <xref:System.ServiceModel.WSHttpBinding> um ponto <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>final <xref:System.ServiceModel.SecurityMode.Message>com um padrão (o padrão , ou seja), todas as mensagens são criptografadas e assinadas porque este é o nível de proteção padrão. No entanto, `ISampleService` quando um <xref:System.ServiceModel.BasicHttpBinding> serviço é <xref:System.ServiceModel.SecurityMode>usado com um padrão (o padrão , ou seja), <xref:System.ServiceModel.SecurityMode.None>todas as mensagens são enviadas como texto porque não há segurança para essa vinculação e assim o nível de proteção é ignorado (ou seja, as mensagens não são criptografadas nem assinadas). Se <xref:System.ServiceModel.SecurityMode> a mudança <xref:System.ServiceModel.SecurityMode.Message>para , então essas mensagens seriam criptografadas e assinadas (porque esse seria agora o nível de proteção padrão da vinculação).  
  
 Se você quiser especificar ou ajustar explicitamente os requisitos de proteção para o seu contrato, defina a <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> propriedade (ou qualquer uma das `ProtectionLevel` propriedades em um escopo menor) para o nível que seu contrato de serviço exige. Neste caso, o uso de uma configuração explícita requer a vinculação para suportar essa configuração no mínimo para o escopo utilizado. Por exemplo, o exemplo de <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> código a seguir `GetGuid` especifica um valor explicitamente para a operação.  
  
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
  
 A seguir está o código Visual Basic equivalente.  
  
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
  
 Um serviço que `IExplicitProtectionLevelSampleService` implementa este contrato e tem <xref:System.ServiceModel.WSHttpBinding> um <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>ponto final <xref:System.ServiceModel.SecurityMode.Message>que usa o padrão (o padrão , que é ) tem o seguinte comportamento:  
  
- As `GetString` mensagens de operação são criptografadas e assinadas.  
  
- As `GetInt` mensagens de operação são enviadas como texto não criptografado e não assinado (ou seja, simples).  
  
- A `GetGuid` <xref:System.Guid?displayProperty=nameWithType> operação é devolvida em uma mensagem que é criptografada e assinada.  
  
 Para obter mais informações sobre os níveis de proteção e como usá-los, consulte [Understanding Protection Level](understanding-protection-level.md). Para obter mais informações sobre segurança, consulte [Protegendo serviços](securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Outros requisitos de assinatura de operação  
 Alguns recursos de aplicação requerem um tipo específico de assinatura de operação. Por exemplo, <xref:System.ServiceModel.NetMsmqBinding> a vinculação suporta serviços duráveis e clientes, nos quais um aplicativo pode reiniciar no meio da comunicação e continuar de onde parou sem perder nenhuma mensagem. (Para obter mais informações, consulte [Filas no WCF](./feature-details/queues-in-wcf.md).) No entanto, as `in` operações duráveis devem ter apenas um parâmetro e não ter valor de retorno.  
  
 Outro exemplo é <xref:System.IO.Stream> o uso de tipos em operações. Como <xref:System.IO.Stream> o parâmetro inclui todo o corpo da mensagem, se `ref` uma `out` entrada ou uma saída (ou <xref:System.IO.Stream>seja, parâmetro, parâmetro ou valor de retorno) for do tipo, então ele deve ser a única entrada ou saída especificada em sua operação. Além disso, o parâmetro ou o <xref:System.IO.Stream> <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>tipo <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>de retorno devem ser, ou , ou . Para obter mais informações sobre fluxos, consulte [Big Data e Streaming](./feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Nomes, Namespaces e Ofuscação  
 Os nomes e namespaces dos tipos .NET na definição de contratos e operações são significativos quando os contratos são convertidos em WSDL e quando as mensagens de contrato são criadas e enviadas. Portanto, é fortemente recomendável que nomes de contratos de serviço `Name` `Namespace` e namespaces sejam explicitamente definidos <xref:System.Runtime.Serialization.DataContractAttribute>usando <xref:System.Runtime.Serialization.DataMemberAttribute>as propriedades de todos os atributos do contrato de suporte, como os atributos, <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute>e outros atributos contratuais.  
  
 Um resultado disso é que, se os nomes e namespaces não forem explicitamente definidos, o uso da ofuscação de IL no conjunto altera os nomes do tipo de contrato e os namespaces e resulta em trocas modificadas de WSDL e fio que normalmente falham. Se você não definir os nomes e namespaces do contrato explicitamente, mas <xref:System.Reflection.ObfuscationAttribute> <xref:System.Reflection.ObfuscateAssemblyAttribute> pretende usar ofuscação, use os atributos e atributos para evitar a modificação dos nomes do tipo de contrato e dos namespaces.  
  
## <a name="see-also"></a>Confira também

- [Como criar um contrato de solicitação-resposta](./feature-details/how-to-create-a-request-reply-contract.md)
- [Como criar um contrato unidirecional](./feature-details/how-to-create-a-one-way-contract.md)
- [Como criar um contrato duplex](./feature-details/how-to-create-a-duplex-contract.md)
- [Especificando transferência de dados em contratos de serviço](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [Especificando e lidando com falhas em contratos e serviços](specifying-and-handling-faults-in-contracts-and-services.md)
- [Usando sessões](using-sessions.md)
- [Operações síncronas e assíncronas](synchronous-and-asynchronous-operations.md)
- [Reliable Services](reliable-services.md)
- [Serviços e transações](services-and-transactions.md)
