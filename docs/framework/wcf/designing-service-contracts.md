---
title: Criando contratos de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 6d1e9ba7f5546923b222f2d495aacdb2c1caaf96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="designing-service-contracts"></a>Criando contratos de serviço
Este tópico descreve qual serviço os contratos são, como elas são definidas, as operações que estão disponíveis (e as implicações para as trocas de mensagens subjacente), quais tipos de dados são usados e outros problemas que ajudarão a criar operações que atendem a requisitos do seu cenário.  
  
## <a name="creating-a-service-contract"></a>Criar um contrato de serviço  
 Serviços de expõem um número de operações. Em aplicativos do Windows Communication Foundation (WCF), define as operações de criação de um método e marcá-lo com o <xref:System.ServiceModel.OperationContractAttribute> atributo. Em seguida, para criar um contrato de serviço, agrupar suas operações, por declará-los dentro de uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> de atributo ou pelo definindo-os em uma classe marcada com o mesmo atributo. (Para obter um exemplo básico, consulte [como: definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).)  
  
 Todos os métodos que não têm um <xref:System.ServiceModel.OperationContractAttribute> atributo não são operações de serviço e não são expostos por [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços.  
  
 Este tópico descreve os seguintes pontos de decisão ao projetar um contrato de serviço:  
  
-   Se deseja usar interfaces ou classes.  
  
-   Como especificar os tipos de dados que você deseja que o exchange.  
  
-   Os tipos de padrões de troca, que você pode usar.  
  
-   Se você pode fazer parte de requisitos de segurança explícita do contrato.  
  
-   As restrições para operação entradas e saídas.  
  
## <a name="classes-or-interfaces"></a>Interfaces ou classes  
 Classes e interfaces representam um agrupamento de funcionalidade e, portanto, ambos podem ser usados para definir um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] contrato de serviço. No entanto, é recomendável que você use interfaces porque eles diretamente modelo contratos de serviço. Sem uma implementação interfaces não mais do que definem um agrupamento de métodos com determinadas assinaturas. Implementar uma interface de contrato de serviço e você tiver implementado um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço.  
  
 Todos os benefícios de interfaces gerenciadas se aplicam a interfaces de contrato de serviço:  
  
-   Interfaces de contrato de serviço podem estender qualquer número de outras interfaces de contrato de serviço.  
  
-   Uma única classe pode implementar qualquer número de contratos de serviço com a implementação dessas interfaces de contrato de serviço.  
  
-   Você pode modificar a implementação de um contrato de serviço, alterando a implementação da interface, enquanto o contrato de serviço permanece o mesmo.  
  
-   Você pode versão seu serviço implementando a interface antiga e nova. Clientes antigos se conectar à versão original, enquanto os clientes mais recentes podem conectar-se para a versão mais recente.  
  
> [!NOTE]
>  Ao herdar de outras interfaces de contrato de serviço, você não pode substituir as propriedades de operação, como o nome ou namespace. Se você tentar fazer isso, você cria uma nova operação no contrato de serviço atual.  
  
 Para obter um exemplo do uso de uma interface para criar um contrato de serviço, consulte [como: criar um serviço com uma Interface de contrato](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 No entanto, você pode usar uma classe para definir um contrato de serviço e implementar o contrato ao mesmo tempo. A vantagem de criar seus serviços aplicando <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> diretamente para a classe e os métodos na classe, respectivamente, é velocidade e simplicidade. As desvantagens são que classes gerenciadas não oferecem suporte a várias heranças, e assim eles somente podem implementar um contrato de serviço por vez. Além disso, qualquer modificação para as assinaturas de método ou classe modifica o contrato público para esse serviço, o que pode impedir que clientes sem modificações usando seu serviço. Para obter mais informações, consulte [implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Para obter um exemplo que usa uma classe para criar um contrato de serviço e implementa ao mesmo tempo, consulte [como: criar um serviço com uma classe de contrato](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 Neste ponto, você deve compreender a diferença entre a definição de seu contrato de serviço usando uma interface e usando uma classe. A próxima etapa é decidir quais dados podem ser passados bidirecionalmente entre um serviço e seus clientes.  
  
## <a name="parameters-and-return-values"></a>Parâmetros e valores de retorno  
 Cada operação tem um valor de retorno e um parâmetro, mesmo se eles forem `void`. No entanto, ao contrário de um método de local, no qual você pode passar as referências a objetos de um objeto para outro, operações de serviço não passa as referências a objetos. Em vez disso, eles passam cópias dos objetos.  
  
 Isso é significativo porque cada tipo usado em um parâmetro ou retornar o valor deve ser serializável; ou seja, deve ser possível converter um objeto do tipo em um fluxo de bytes em um fluxo de bytes em um objeto.  
  
 Tipos primitivos são serializáveis por padrão, assim como muitos tipos do .NET Framework.  
  
> [!NOTE]
>  O valor dos nomes de parâmetro na assinatura de operação são parte do contrato e diferenciam maiusculas de minúsculas. Se você quiser usar o mesmo nome de parâmetro localmente mas modificar o nome nos metadados publicados, consulte o <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Contratos de dados  
 Aplicativos orientados a serviços, como aplicativos do Windows Communication Foundation (WCF) são projetados para interagir com o maior número possível de aplicativos de cliente no Microsoft e plataformas da Microsoft não. Para a mais ampla interoperabilidade possível, é recomendável que você marca seus tipos com o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para criar um contrato de dados, que é a parte do contrato de serviço que descreve os dados que suas operações de serviço Exchange.  
  
 Contratos de dados são contratos de estilo de aceitar: nenhum tipo ou membro de dados é serializado, a menos que você explicitamente aplique o atributo de contrato de dados. Contratos de dados não estão relacionados ao escopo de acesso do código gerenciado: membros de dados particular podem ser serializados e enviados em qualquer lugar para ser acessados publicamente. (Para obter um exemplo básico de um contrato de dados, consulte [como: criar um contrato de dados básico para uma classe ou estrutura](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] lida com a definição das mensagens SOAP subjacentes que habilitar a funcionalidade da operação, bem como a serialização dos seus tipos de dados dentro e fora do corpo das mensagens. Como seus tipos de dados são serializáveis, você não precisa pensar sobre a infraestrutura de troca de mensagem subjacente ao projetar suas operações.  
  
 Embora o típico [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo usa o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para criar contratos de dados para operações, você pode usar outros mecanismos de serialização. O padrão <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> e <xref:System.Xml.Serialization.IXmlSerializable> todos os mecanismos de trabalham para lidar com a serialização dos seus tipos de dados para as mensagens SOAP subjacentes que executá-las a partir de um aplicativo para outro. Se os tipos de dados requerem suporte especial, você pode usar mais estratégias de serialização. Para obter mais informações sobre as opções para a serialização de tipos de dados em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos, consulte [especificando a transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapeando parâmetros e valores de retorno para as trocas de mensagens  
 Operações de serviço são suportadas por uma troca de base de mensagens SOAP que transferem dados de aplicativo e para trás, além dos dados requeridos pelo aplicativo para oferecer suporte a determinados segurança padrão, transações e recursos relacionados à sessão. Como esse é o caso, a assinatura de uma operação de serviço determina um determinado subjacente *padrão de troca de mensagem* (MEPS) que pode dar suporte a transferência de dados e os recursos que requer uma operação. Você pode especificar três padrões no [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de programação: solicitação/resposta, unidirecional e padrões de mensagens duplex.  
  
##### <a name="requestreply"></a>Solicitação/resposta  
 Um padrão de solicitação/resposta é um no qual um remetente da solicitação (um aplicativo cliente) recebe uma resposta correlacionada com a qual a solicitação. Esse é o padrão MEPS porque ele oferece suporte a uma operação em que um ou mais parâmetros são passados para a operação e um valor de retorno é passado de volta para o chamador. Por exemplo, o seguinte exemplo de código em c# mostra uma operação de serviço básico que utiliza uma cadeia de caracteres e retorna uma cadeia de caracteres.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Este é o código do Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Essa assinatura de operação determina a forma de troca de mensagens subjacente. Se nenhuma correlação existia, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] não é possível determinar qual operação destina-se o valor de retorno.  
  
 Observe que, a menos que você especificar um padrão de mensagem subjacente diferente, até mesmo as operações de serviço que retornam `void` (`Nothing` no Visual Basic) são trocas de mensagens de solicitação/resposta. O resultado para a operação é que, a menos que um cliente invoca a operação de forma assíncrona, o cliente para o processamento até que a mensagem de retorno é recebida, mesmo que essa mensagem está vazia no caso normal. O seguinte exemplo de código em c# mostra uma operação que não retorna até que o cliente recebeu uma mensagem vazia em resposta.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Este é o código do Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 O exemplo anterior pode diminuir o desempenho de cliente e a capacidade de resposta se a operação leva muito tempo para executar, mas há vantagens em operações de solicitação/resposta mesmo quando eles retornarem `void`. O mais óbvio é que as falhas de SOAP podem ser retornadas na mensagem de resposta, que indica que alguma condição de erro relacionados ao serviço ocorreu na comunicação ou processamento. Falhas de SOAP que são especificadas em um contrato de serviço são passadas para o aplicativo cliente como um <xref:System.ServiceModel.FaultException%601> objeto, onde o parâmetro de tipo é o tipo especificado no contrato de serviço. Isso faz com que os clientes de notificação sobre condições de erro no [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fácil de serviços. Para obter mais informações sobre exceções, falhas de SOAP e tratamento de erros, consulte [especificando e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Para ver um exemplo de um serviço de solicitação/resposta e um cliente, consulte [como: criar um contrato de solicitação-resposta](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Para obter mais informações sobre problemas com o padrão de solicitação-resposta, consulte [serviços de solicitação-resposta](../../../docs/framework/wcf/feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Unidirecional  
 Se o cliente de um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo de serviço não deve aguardar a conclusão da operação e não processa falhas de SOAP, a operação pode especificar um padrão de mensagem unidirecional. Uma operação unidirecional é um no qual um cliente invoca uma operação e continua o processamento após [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] grava a mensagem para a rede. Normalmente, isso significa que, a menos que os dados que está sendo enviados na mensagem de saída são muito grandes o cliente continua executando quase imediatamente (a menos que haja um erro ao enviar os dados). Esse tipo de padrão de troca de mensagens dá suporte ao comportamento do tipo de evento de um cliente para um aplicativo de serviço.  
  
 Uma troca de mensagens no qual uma mensagem é enviada e nenhum são recebidas não oferece suporte a uma operação de serviço que especifica um valor de retorno diferente de `void`; nesse caso um <xref:System.InvalidOperationException> exceção será lançada.  
  
 Nenhuma mensagem de retorno também significa que não pode haver nenhuma falha SOAP retornada para indicar erros em processamento ou a comunicação. (Comunicação de informações de erro quando as operações estão operações unidirecionais requer um padrão de troca de mensagens duplex).  
  
 Para especificar uma troca de mensagens unidirecionais para uma operação que retorna `void`, defina o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `true`, conforme mostrado no seguinte exemplo de código c#.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Este é o código do Visual Basic equivalente.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Este método é idêntico para exemplo de solicitação/resposta anterior, mas configuração o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `true` significa que, embora o método é idêntico, a operação de serviço não envia uma mensagem de retorno e os clientes retornarão imediatamente quando o mensagem de saída foi passada para a camada do canal. Para obter um exemplo, consulte [como: criar um contrato unidirecional](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md). Para obter mais informações sobre o padrão unidirecional, consulte [unidirecional serviços](../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Duplex  
 Um padrão de duplex é caracterizada pela capacidade do serviço e o cliente para enviar mensagens ao outro independentemente se usando unidirecional ou mensagens de solicitação/resposta. Essa forma de comunicação bidirecional é útil para os serviços que devem se comunicar diretamente com o cliente ou para fornecer uma experiência assíncrona para nenhum dos lados de uma troca de mensagens, incluindo o comportamento do tipo de evento.  
  
 O padrão de duplex é um pouco mais complexo do que a solicitação/resposta ou unidirecionais padrões devido o mecanismo adicional para se comunicar com o cliente.  
  
 Para criar um contrato duplex, você também deve criar um contrato de retorno de chamada e atribuir o tipo de contrato de retorno de chamada para o <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> propriedade o <xref:System.ServiceModel.ServiceContractAttribute> atributo que marca o contrato de serviço.  
  
 Para implementar um padrão de duplex, você deve criar uma segunda interface que contém as declarações de método são chamadas no cliente.  
  
 Para obter um exemplo de criação de um serviço e um cliente que acessa o serviço, consulte [como: criar um contrato Duplex](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md) e [como: serviços do Access com um contrato Duplex](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Para obter um exemplo de funcionamento, consulte [Duplex](../../../docs/framework/wcf/samples/duplex.md). Para obter mais informações sobre como usar contratos duplex, consulte [serviços Duplex](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
> [!CAUTION]
>  Quando um serviço recebe uma mensagem duplex, ele examina o `ReplyTo` elemento nessa mensagem de entrada para determinar para onde enviar a resposta. Se o canal que é usado para receber a mensagem não for protegido, um cliente não confiável pode enviar uma mensagem mal-intencionado com um computador de destino `ReplyTo`, causando uma negação de serviço (DOS) da máquina de destino.  
  
##### <a name="out-and-ref-parameters"></a>Parâmetros de Ref e out  
 Na maioria dos casos, você pode usar `in` parâmetros (`ByVal` no Visual Basic) e `out` e `ref` parâmetros (`ByRef` no Visual Basic). Porque ambos `out` e `ref` parâmetros indicam que dados são retornados de uma operação, uma assinatura de operação, como a seguir especifica que uma operação de solicitação/resposta for necessária, embora a assinatura da operação retorna `void`.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Este é o código do Visual Basic equivalente.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 As únicas exceções são os casos em que a sua assinatura tem uma estrutura específica. Por exemplo, você pode usar o <xref:System.ServiceModel.NetMsmqBinding> de associação para se comunicar com se apenas os clientes, o método usado para declarar uma operação retorna `void`; não pode haver nenhum valor de saída, se ele é um valor de retorno, `ref`, ou `out` parâmetro.  
  
 Além disso, usando `out` ou `ref` parâmetros requer que a operação tenha uma mensagem de resposta subjacente para executar novamente o objeto modificado. Se a operação é uma operação unidirecional, um <xref:System.InvalidOperationException> exceção em tempo de execução.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Especificar o nível de proteção de mensagem do contrato  
 Ao criar o contrato, você também deve decidir o nível de proteção de mensagem de serviços que implemente o contrato. Isso é necessário apenas se a segurança de mensagem é aplicada para a associação no ponto de extremidade do contrato. Se a associação de segurança desativada (ou seja, se a associação fornecida pelo sistema define o <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> para o valor <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>), em seguida, você não precisa decidir sobre o nível de proteção de mensagem para o contrato. Na maioria dos casos, as associações fornecidas pelo sistema com segurança em nível de mensagem aplicada fornecem um nível de proteção suficiente e você não deve considerar o nível de proteção para cada operação, ou para cada mensagem.  
  
 O nível de proteção é um valor que especifica se as mensagens (ou partes da mensagem) que dão suporte a um serviço são assinados, assinado e criptografado ou enviados sem criptografia ou assinaturas. O nível de proteção pode ser definido em vários escopos: no nível de serviço, para uma operação específica, para uma mensagem em que a operação ou uma parte da mensagem. Os valores definidos em um escopo tornam-se o valor padrão para escopos menores, a menos que explicitamente substituído. Se uma configuração de associação não pode fornecer o nível de proteção mínima necessária para o contrato, uma exceção será lançada. E, quando nenhum valor de nível de proteção é definidos explicitamente o contrato, a configuração de associação controla o nível de proteção para todas as mensagens se a associação de segurança de mensagem. Este é o comportamento padrão.  
  
> [!IMPORTANT]
>  Decidir se deseja definir explicitamente vários escopos de um contrato para menor que o nível de proteção completa de <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> geralmente é uma decisão que lida com algum nível de segurança para melhorar o desempenho. Nesses casos, as decisões devem giram em torno de suas operações e o valor dos dados que eles do exchange. Para obter mais informações, consulte [protegendo serviços](../../../docs/framework/wcf/securing-services.md).  
  
 Por exemplo, o exemplo de código a seguir não definido o <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> ou <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> propriedade no contrato.  
  
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
  
 Este é o código do Visual Basic equivalente.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Ao interagir com um `ISampleService` implementação em um ponto de extremidade com um padrão <xref:System.ServiceModel.WSHttpBinding> (o padrão <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, que é <xref:System.ServiceModel.SecurityMode.Message>), todas as mensagens são criptografadas e assinadas porque este é o nível de proteção padrão. No entanto, quando um `ISampleService` serviço é usado com um padrão <xref:System.ServiceModel.BasicHttpBinding> (o padrão <xref:System.ServiceModel.SecurityMode>, que é <xref:System.ServiceModel.SecurityMode.None>), todas as mensagens são enviadas como texto porque não há nenhuma segurança para esta associação e, portanto, o nível de proteção é ignorado (ou seja, o as mensagens não são criptografadas nem assinadas). Se o <xref:System.ServiceModel.SecurityMode> foi alterado para <xref:System.ServiceModel.SecurityMode.Message>, em seguida, essas mensagens deve ser criptografadas e assinadas (porque agora que seria o nível de proteção da associação padrão).  
  
 Se você deseja especificar explicitamente ou ajustar os requisitos de proteção para o contrato, defina o <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> propriedade (ou qualquer uma da `ProtectionLevel` propriedades em um escopo menor) para o nível de seu contrato de serviço exige. Nesse caso, usar uma configuração explícita exige a associação dar suporte a essa configuração, no mínimo para o escopo usado. Por exemplo, o exemplo de código a seguir especifica um <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> valor explicitamente, para o `GetGuid` operação.  
  
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
  
 Este é o código do Visual Basic equivalente.  
  
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
  
 Um serviço que implementa `IExplicitProtectionLevelSampleService` contrato e tem um ponto de extremidade que usa o padrão <xref:System.ServiceModel.WSHttpBinding> (o padrão <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, que é <xref:System.ServiceModel.SecurityMode.Message>) tem o seguinte comportamento:  
  
-   O `GetString` mensagens de operação são criptografadas e assinadas.  
  
-   O `GetInt` assinados (ou seja, simples) e descriptografados de operação são enviadas como texto.  
  
-   O `GetGuid` operação <xref:System.Guid?displayProperty=nameWithType> é retornado em uma mensagem que é criptografada e assinada.  
  
 Para obter mais informações sobre níveis de proteção e como usá-los, consulte [Noções básicas sobre nível de proteção](../../../docs/framework/wcf/understanding-protection-level.md). Para obter mais informações sobre segurança, consulte [protegendo serviços](../../../docs/framework/wcf/securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Outros requisitos de assinatura de operação  
 Alguns recursos de aplicativo exigir um determinado tipo de assinatura da operação. Por exemplo, o <xref:System.ServiceModel.NetMsmqBinding> associação oferece suporte a clientes, em que um aplicativo pode reiniciar no meio de comunicação e continuar onde ela parou sem perder todas as mensagens e serviços duráveis. (Para obter mais informações, consulte [filas no WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).) No entanto, operações duráveis devem levar apenas um `in` parâmetro e não têm nenhum valor de retorno.  
  
 Outro exemplo é o uso de <xref:System.IO.Stream> tipos de operações. Porque o <xref:System.IO.Stream> parâmetro inclui o corpo da mensagem inteira, se uma entrada ou uma saída (ou seja, `ref` parâmetro `out` parâmetro ou valor de retorno) é do tipo <xref:System.IO.Stream>, em seguida, ele deve ser a única entrada ou saída especificada no seu operação. Além disso, o tipo de retorno ou parâmetro deve ser <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, ou <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Para obter mais informações sobre fluxos, consulte [dados grandes e Streaming](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Nomes de Namespaces e ofuscação  
 Os nomes e os namespaces, os tipos do .NET na definição de contratos e operações são significativos quando contratos são convertidos em WSDL e quando as mensagens de contrato são criadas e enviadas. Portanto, é altamente recomendável que os nomes de contrato de serviço e namespaces são definidos explicitamente usando o `Name` e `Namespace` propriedades de dar suporte a todos os atributos de contrato, como o <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>e outros atributos do contrato.  
  
 Um resultado é que, se os nomes e os namespaces não são explicitamente definidas, o uso de ofuscação de IL no assembly altera os nomes de tipo de contrato e namespaces e resultados de WSDL modificado e trocas de transmissão que normalmente não. Se você não definir os nomes de contrato e os namespaces explicitamente, mas pretende usar ofuscamento, use o <xref:System.Reflection.ObfuscationAttribute> e <xref:System.Reflection.ObfuscateAssemblyAttribute> namespaces e nomes de tipo de atributos para impedir a modificação do contrato.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar um contrato de solicitação-resposta](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)  
 [Como criar um contrato unidirecional](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)  
 [Como criar um contrato duplex](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Especificando transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 [Especificando e lidando com falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Usando sessões](../../../docs/framework/wcf/using-sessions.md)  
 [Operações síncronas e assíncronas](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)  
 [Serviços confiáveis](../../../docs/framework/wcf/reliable-services.md)  
 [Serviços e transações](../../../docs/framework/wcf/services-and-transactions.md)
