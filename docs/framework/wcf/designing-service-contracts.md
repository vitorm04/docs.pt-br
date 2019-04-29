---
title: Criando contratos de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 68ea866b736350b8a393d1f4788e4b08754e5ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785028"
---
# <a name="designing-service-contracts"></a>Criando contratos de serviço
Este tópico descreve o que serviço contratos estão, como elas são definidas, as operações que estão disponíveis (e as implicações para as trocas de mensagens subjacente), quais tipos de dados são usados e outros problemas que ajudam você a criar operações que satisfazem a requisitos do seu cenário.  
  
## <a name="creating-a-service-contract"></a>Criar um contrato de serviço  
 Os serviços expõem um número de operações. Aplicativos do Windows Communication Foundation (WCF), define as operações Criando um método e marcá-lo com o <xref:System.ServiceModel.OperationContractAttribute> atributo. Em seguida, para criar um contrato de serviço, agrupar suas operações, pelo declará-los dentro de uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> de atributo ou por defini-los em uma classe marcada com o mesmo atributo. (Para obter um exemplo básico, consulte [como: Definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).)  
  
 Todos os métodos que não têm um <xref:System.ServiceModel.OperationContractAttribute> atributo não são operações de serviço e não são expostos por serviços do WCF.  
  
 Este tópico descreve os seguintes pontos de decisão ao projetar um contrato de serviço:  
  
- Se usar interfaces ou classes.  
  
- Como especificar os tipos de dados para o exchange.  
  
- Os tipos de padrões de troca, que você pode usar.  
  
- Se você pode fazer parte de requisitos de segurança explícita do contrato.  
  
- As restrições para operação entradas e saídas.  
  
## <a name="classes-or-interfaces"></a>Classes ou Interfaces  
 Classes e interfaces representam um agrupamento de funcionalidade e, portanto, ambos podem ser usados para definir um contrato de serviço do WCF. No entanto, é recomendável que você use interfaces porque elas diretamente modelam contratos de serviço. Sem uma implementação, as interfaces não mais do que definir um agrupamento de métodos com determinadas assinaturas. Implementar uma interface de contrato de serviço e você tiver implementado um serviço WCF.  
  
 Todos os benefícios de interfaces gerenciadas se aplicam a interfaces de contrato de serviço:  
  
- Interfaces de contrato de serviço podem estender qualquer número de outras interfaces de contrato de serviço.  
  
- Uma única classe pode implementar qualquer número de contratos de serviço com a implementação dessas interfaces de contrato de serviço.  
  
- Você pode modificar a implementação de um contrato de serviço, alterando a implementação da interface, enquanto o contrato de serviço permanece o mesmo.  
  
- Você pode versão seu serviço, Implementando a interface antiga e nova. Clientes antigos conecte-se à versão original, enquanto os clientes mais recentes podem conectar-se para a versão mais recente.  
  
> [!NOTE]
>  Ao herdar de outras interfaces de contrato de serviço, você não pode substituir as propriedades da operação, como o nome ou namespace. Se você tentar fazer isso, você cria uma nova operação no contrato de serviço atual.  
  
 Para obter um exemplo de como usar uma interface para criar um contrato de serviço, consulte [como: Criar um serviço com uma Interface de contrato](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Você pode, no entanto, usar uma classe para definir um contrato de serviço e implementar esse contrato ao mesmo tempo. A vantagem de criar seus serviços por meio da aplicação <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> diretamente à classe e os métodos na classe, respectivamente, é velocidade e a simplicidade. As desvantagens são que classes gerenciadas não dão suporte a várias heranças e, assim eles podem implementar apenas um contrato de serviço por vez. Além disso, qualquer modificação para as assinaturas de classe ou método modifica o contrato público para o serviço, que pode impedir que clientes sem modificações usando seu serviço. Para obter mais informações, consulte [implementar contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Para obter um exemplo que usa uma classe para criar um contrato de serviço e implementa-lo ao mesmo tempo, consulte [como: Criar um serviço com uma classe de contrato](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 Neste ponto, você deve compreender a diferença entre a definição de seu contrato de serviço usando uma interface e por meio de uma classe. A próxima etapa é decidir quais dados podem ser passados bidirecionalmente entre um serviço e seus clientes.  
  
## <a name="parameters-and-return-values"></a>Parâmetros e valores de retorno  
 Cada operação tem um valor de retorno e um parâmetro, mesmo se eles forem `void`. No entanto, ao contrário de um método de local, no qual você pode passar referências a objetos de um objeto para outro, as operações de serviço não passam as referências a objetos. Em vez disso, eles passam cópias dos objetos.  
  
 Isso é significativo porque cada tipo usado em um parâmetro ou retornar o valor deve ser serializável; ou seja, deve ser possível converter um objeto desse tipo em um fluxo de bytes e a partir de um fluxo de bytes em um objeto.  
  
 Tipos primitivos são serializáveis por padrão, assim como muitos tipos no .NET Framework.  
  
> [!NOTE]
>  O valor de nomes de parâmetro na assinatura da operação são parte do contrato e diferenciam maiusculas de minúsculas. Se você quiser usar o mesmo nome de parâmetro localmente, mas modificar o nome nos metadados publicados, consulte o <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Contratos de dados  
 Aplicativos orientada a serviços como o Windows Communication Foundation (WCF) são projetados para interoperar com o maior número possível dos aplicativos de cliente na Microsoft e plataformas não-Microsoft. Para a mais ampla interoperabilidade possível, é recomendável que você marca seus tipos com o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para criar um contrato de dados, que é a parte do contrato de serviço que descreve os dados que suas operações de serviço Exchange.  
  
 Contratos de dados são contratos de aceitação do estilo: Nenhum tipo ou membro de dados é serializado, a menos que você aplique explicitamente o atributo de contrato de dados. Contratos de dados não estão relacionados ao escopo de acesso do código gerenciado: Membros de dados particulares podem ser serializados e enviados em qualquer lugar para ser acessados publicamente. (Para obter um exemplo básico de um contrato de dados, consulte [como: Criar um contrato de dados básicos para uma classe ou estrutura](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) O WCF trata a definição das mensagens SOAP subjacentes que habilitam a funcionalidade da operação, bem como a serialização dos seus tipos de dados dentro e fora do corpo das mensagens. Desde que seus tipos de dados são serializáveis, você não precisa pensar sobre a infraestrutura subjacente de troca de mensagem durante a criação de suas operações.  
  
 Embora o aplicativo WCF típico usa a <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para criar contratos de dados para operações, você pode usar outros mecanismos de serialização. O padrão <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> e <xref:System.Xml.Serialization.IXmlSerializable> mecanismos todos funcionam para lidar com a serialização dos seus tipos de dados em mensagens SOAP subjacentes que executá-las a partir de um aplicativo para outro. Você pode empregar estratégias de serialização mais se seus tipos de dados requerem suporte especial. Para obter mais informações sobre as opções para a serialização de tipos de dados em aplicativos do WCF, consulte [especificando a transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapeando parâmetros e valores de retorno para trocas de mensagens  
 Operações de serviço são compatíveis com uma troca de base das mensagens SOAP que transferir dados de aplicativo e para trás, além dos dados exigidos pelo aplicativo para dar suporte a determinados segurança padrão, transações e recursos relacionados à sessão. Como esse é o caso, a assinatura de uma operação de serviço impõe um determinado subjacente *padrão de troca de mensagem* (MEP) que pode dar suporte a transferência de dados e os recursos de uma operação exige. Você pode especificar três padrões no modelo de programação WCF: solicitação/resposta, unidirecional e padrões de mensagens duplex.  
  
##### <a name="requestreply"></a>Solicitação/resposta  
 Um padrão de solicitação/resposta é um em que um remetente da solicitação (um aplicativo cliente) recebe uma resposta correlacionada com a qual a solicitação. Esse é o padrão MEP porque ele dá suporte a uma operação em que um ou mais parâmetros são passados para a operação e um valor de retorno é passado para o chamador. Por exemplo, a seguinte C# exemplo de código mostra uma operação de serviço básico que usa uma cadeia de caracteres e retorna uma cadeia de caracteres.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 A seguir está o código do Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Essa assinatura de operação determina a forma de troca de mensagens subjacente. Se nenhuma correlação existia, o WCF não pode determinar para qual operação destina-se o valor de retorno.  
  
 Observe que, a menos que você especificar um padrão de mensagem subjacente diferente, até mesmo operações de serviço que retornam `void` (`Nothing` no Visual Basic) são as trocas de mensagens de solicitação/resposta. O resultado para a sua operação é que, a menos que um cliente chama a operação de forma assíncrona, o cliente interrompe o processamento até que a mensagem de retorno é recebida, mesmo que essa mensagem está vazia no caso normal. O seguinte C# exemplo de código mostra uma operação que não retorna até que o cliente recebeu uma mensagem vazia na resposta.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 A seguir está o código do Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 O exemplo anterior pode diminuir o desempenho de cliente e a capacidade de resposta se a operação leva muito tempo para executar, mas há vantagens em operações de solicitação/resposta, mesmo quando eles retornarem `void`. O mais óbvio é que as falhas de SOAP podem ser retornadas na mensagem de resposta, que indica que tenha ocorrido alguma condição de erro relacionadas ao serviço, em processamento ou de comunicação. Falhas de SOAP que são especificadas em um contrato de serviço são passadas para o aplicativo cliente como um <xref:System.ServiceModel.FaultException%601> objeto, em que o parâmetro de tipo é o tipo especificado no contrato de serviço. Isso facilita realiza clientes sobre as condições de erro nos serviços do WCF. Para obter mais informações sobre exceções, falhas de SOAP e tratamento de erros, consulte [especificação e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Para ver um exemplo de um cliente e serviço de solicitação/resposta, consulte [como: Criar um contrato de solicitação-resposta](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Para obter mais informações sobre problemas com o padrão de solicitação-resposta, consulte [serviços de solicitação-resposta](../../../docs/framework/wcf/feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Unidirecional  
 Se o cliente de um aplicativo de serviço do WCF não deve aguardar a conclusão da operação e não processa falhas de SOAP, a operação pode especificar um padrão de mensagem unidirecional. Uma operação unidirecional é aquela na qual um cliente invoca uma operação e continua o processamento depois que o WCF grava a mensagem para a rede. Normalmente, isso significa que, a menos que os dados que está sendo enviados na mensagem de saída são muito grandes o cliente continua executando quase que imediatamente (a menos que haja um erro ao enviar os dados). Esse tipo de padrão de troca de mensagens dá suporte ao comportamento do tipo de evento de um cliente para um aplicativo de serviço.  
  
 Uma troca de mensagens em que uma mensagem é enviada e o none são recebidas não oferece suporte a uma operação de serviço que especifica um valor de retorno diferente de `void`; nesse caso, um <xref:System.InvalidOperationException> exceção é lançada.  
  
 Nenhuma mensagem de retorno também significa que não pode haver nenhuma falha SOAP retornada para indicar os erros em processamento ou de comunicação. (Comunicação de informações de erro quando as operações são operações unidirecionais requer um padrão de troca de mensagens duplex).  
  
 Para especificar uma troca de mensagens unidirecional de uma operação que retorna `void`, defina a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `true`, conforme mostrado no seguinte C# exemplo de código.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 A seguir está o código do Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Esse método é idêntico ao exemplo de solicitação/resposta anterior, mas configuração o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade para `true` significa que, embora o método é idêntico, a operação de serviço não envia uma mensagem de retorno e os clientes retornarão imediatamente quando o mensagem de saída foi passada para a camada de canais. Para obter um exemplo, consulte [ Criar um contrato unidirecional](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md). Para obter mais informações sobre o padrão unidirecional, consulte [unidirecional serviços](../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Duplex  
 Um padrão de duplex é caracterizada pela capacidade do serviço e o cliente para enviar mensagens entre si independentemente se usando unidirecional ou solicitação/resposta de mensagens. Essa forma de comunicação bidirecional é útil para os serviços que devem se comunicar diretamente com o cliente ou para fornecer uma experiência assíncrona para ambos os lados de uma troca de mensagens, incluindo o comportamento do tipo de evento.  
  
 O padrão de duplex é um pouco mais complexo do que os padrões unidirecionais ou solicitação/resposta por causa do mecanismo adicional para se comunicar com o cliente.  
  
 Para criar um contrato duplex, você também deve criar um contrato de retorno de chamada e atribuir o tipo do contrato de retorno de chamada para o <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> propriedade do <xref:System.ServiceModel.ServiceContractAttribute> atributo que marca o contrato de serviço.  
  
 Para implementar um padrão de duplex, você deve criar uma segunda interface que contém as declarações de método que são chamadas no cliente.  
  
 Para obter um exemplo de criação de um serviço e um cliente que acessa o serviço, consulte [como: Criar um contrato Duplex](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md) e [como: Acessar os serviços com um contrato Duplex](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Para obter um exemplo funcional, consulte [Duplex](../../../docs/framework/wcf/samples/duplex.md). Para obter mais informações sobre como usar contratos duplex, consulte [serviços Duplex](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
> [!CAUTION]
>  Quando um serviço recebe uma mensagem duplex, ele examina o `ReplyTo` elemento na mensagem de entrada para determinar para onde enviar a resposta. Se o canal que é usado para receber a mensagem não é seguro e, em seguida, um cliente não confiável pode enviar uma mensagem mal-intencionada com um computador de destino `ReplyTo`, gerando uma negação de serviço (DOS) dessa máquina de destino.  
  
##### <a name="out-and-ref-parameters"></a>Parâmetros de Ref e out  
 Na maioria dos casos, você pode usar `in` parâmetros (`ByVal` no Visual Basic) e `out` e `ref` parâmetros (`ByRef` no Visual Basic). Porque ambos `out` e `ref` parâmetros indicam que dados são retornados de uma operação, uma assinatura da operação, como a seguir especifica que uma operação de solicitação/resposta é necessária mesmo que a assinatura da operação retorna `void`.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 A seguir está o código do Visual Basic equivalente.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 As únicas exceções são os casos em que a sua assinatura tem uma estrutura específica. Por exemplo, você pode usar o <xref:System.ServiceModel.NetMsmqBinding> para se comunicar com somente se de clientes, o método usado para declarar uma operação de associação retorna `void`; não pode haver nenhum valor de saída, se ele é um valor de retorno `ref`, ou `out` parâmetro.  
  
 Além disso, usando `out` ou `ref` parâmetros exige que a operação tem uma mensagem de resposta subjacente para executar novamente o objeto modificado. Se a operação é uma operação unidirecional, um <xref:System.InvalidOperationException> exceção é gerada em tempo de execução.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Especificar o nível de proteção de mensagem no contrato  
 Ao projetar seu contrato, você também deve decidir o nível de proteção de serviços que implementam o contrato de mensagem. Isso é necessário apenas se a segurança de mensagem é aplicada à associação no ponto de extremidade do contrato. Se a associação possui segurança desativada (ou seja, se a associação fornecida pelo sistema define o <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> ao valor <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>) e em seguida, você precisa decidir sobre o nível de proteção de mensagem para o contrato. Na maioria dos casos, as associações fornecidas pelo sistema com segurança em nível de mensagem aplicada fornecem um nível de proteção suficiente e não é necessário considerar o nível de proteção para cada operação ou para cada mensagem.  
  
 O nível de proteção é um valor que especifica se as mensagens (ou partes da mensagem) que dão suporte a um serviço estiver conectado, assinado e criptografado ou enviados sem criptografia ou assinaturas. O nível de proteção pode ser definido em vários escopos: No nível de serviço, para uma operação específica, para uma mensagem em que a operação ou uma parte da mensagem. Um escopo de conjunto de valores se tornam o valor padrão para escopos menores, a menos que explicitamente substituídos. Se uma configuração de associação não pode fornecer o nível de proteção mínimo necessário para o contrato, uma exceção é lançada. E quando não há valores de nível de proteção são definidos explicitamente no contrato, a configuração de ligação controla o nível de proteção para todas as mensagens se a associação tem segurança de mensagem. Este é o comportamento padrão.  
  
> [!IMPORTANT]
>  Decidir se deseja definir explicitamente vários escopos de um contrato como menor que o nível de proteção completa de <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> geralmente é uma decisão que negocia um certo grau de segurança para melhorar o desempenho. Nesses casos, suas decisões devem giram em torno de suas operações e o valor dos dados que eles do exchange. Para obter mais informações, consulte [protegendo serviços](../../../docs/framework/wcf/securing-services.md).  
  
 Por exemplo, o exemplo de código a seguir não definido o <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> ou o <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> propriedade no contrato.  
  
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
  
 A seguir está o código do Visual Basic equivalente.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Ao interagir com um `ISampleService` implementação em um ponto de extremidade com um padrão <xref:System.ServiceModel.WSHttpBinding> (o padrão <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, que é <xref:System.ServiceModel.SecurityMode.Message>), todas as mensagens são criptografadas e assinadas porque este é o nível de proteção padrão. No entanto, quando um `ISampleService` serviço é usado com um padrão <xref:System.ServiceModel.BasicHttpBinding> (o padrão <xref:System.ServiceModel.SecurityMode>, que é <xref:System.ServiceModel.SecurityMode.None>), todas as mensagens são enviadas como texto porque não há nenhuma segurança para essa associação e, portanto, o nível de proteção é ignorado (ou seja, o as mensagens não são criptografadas nem assinadas). Se o <xref:System.ServiceModel.SecurityMode> foi alterado para <xref:System.ServiceModel.SecurityMode.Message>, em seguida, essas mensagens devem ser criptografadas e assinadas (porque agora que seria o nível de proteção padrão da associação).  
  
 Se você quiser especificar explicitamente ou ajustar os requisitos de proteção para seu contrato, defina as <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> propriedade (ou qualquer um do `ProtectionLevel` propriedades em um escopo menor) para o nível de seu contrato de serviço exige. Nesse caso, usar uma configuração explícita exige a associação dar suporte a essa configuração, no mínimo para o escopo usado. Por exemplo, o exemplo de código a seguir especifica um <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> valor explicitamente, para o `GetGuid` operação.  
  
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
  
 A seguir está o código do Visual Basic equivalente.  
  
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
  
 Um serviço que implementa essa `IExplicitProtectionLevelSampleService` de contrato e tem um ponto de extremidade que usa o padrão <xref:System.ServiceModel.WSHttpBinding> (o padrão <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, que é <xref:System.ServiceModel.SecurityMode.Message>) tem o seguinte comportamento:  
  
- O `GetString` mensagens da operação são criptografadas e assinadas.  
  
- O `GetInt` assinados (ou seja, simples) e não criptografado de operação de mensagens são enviadas como texto.  
  
- O `GetGuid` operação <xref:System.Guid?displayProperty=nameWithType> é retornado em uma mensagem que é criptografada e assinada.  
  
 Para obter mais informações sobre os níveis de proteção e como usá-los, consulte [Noções básicas sobre nível de proteção](../../../docs/framework/wcf/understanding-protection-level.md). Para obter mais informações sobre a segurança, consulte [protegendo serviços](../../../docs/framework/wcf/securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Outros requisitos de assinatura de operação  
 Alguns recursos do aplicativo exigir um determinado tipo de assinatura da operação. Por exemplo, o <xref:System.ServiceModel.NetMsmqBinding> associação dá suporte a serviços duráveis e clientes, em que um aplicativo pode reiniciar no meio da comunicação e escolher onde ela parou sem perder todas as mensagens. (Para obter mais informações, consulte [filas no WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).) No entanto, as operações duráveis devem levar apenas um `in` parâmetro e não têm nenhum valor de retorno.  
  
 Outro exemplo é o uso de <xref:System.IO.Stream> tipos de operações. Porque o <xref:System.IO.Stream> parâmetro inclui o corpo da mensagem inteira, se uma entrada ou uma saída (ou seja, `ref` parâmetro, `out` parâmetro ou valor de retorno) é do tipo <xref:System.IO.Stream>, em seguida, ele deve ser a única entrada ou saída especificada no seu operação. Além disso, o tipo de retorno ou parâmetro deve ser <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, ou <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Para obter mais informações sobre fluxos, consulte [dados grandes e Streaming](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Nomes, Namespaces e ofuscação  
 Os nomes e namespaces, os tipos do .NET na definição de contratos e operações são significativas quando contratos são convertidos em WSDL e quando criadas e enviadas mensagens de contrato. Portanto, é altamente recomendável que os nomes de contrato de serviço e os namespaces são definidos explicitamente usando o `Name` e `Namespace` propriedades de dar suporte a todos os atributos de contrato, como o <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>e outros atributos de contrato.  
  
 Um resultado disso é que, se os nomes e namespaces não forem definidos explicitamente, o uso de ofuscação de IL em assembly altera os nomes de tipo de contrato e namespaces e resulta em WSDL modificado e trocas de transmissão que normalmente falham. Se você não definir os nomes de contrato e os namespaces explicitamente, mas pretende usar ofuscação, use o <xref:System.Reflection.ObfuscationAttribute> e <xref:System.Reflection.ObfuscateAssemblyAttribute> nomes e namespaces de tipo de atributos para impedir a modificação do contrato.  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar um contrato de solicitação-resposta](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)
- [Como: Criar um contrato unidirecional](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)
- [Como: Criar um contrato Duplex](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Especificando transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Especificando e lidando com falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Usando sessões](../../../docs/framework/wcf/using-sessions.md)
- [Operações síncronas e assíncronas](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
- [Serviços confiáveis](../../../docs/framework/wcf/reliable-services.md)
- [Serviços e transações](../../../docs/framework/wcf/services-and-transactions.md)
