---
title: Utilizando contratos de mensagem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
caps.latest.revision: "46"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 521393aabb9d5674b00194926cb67071cc4566bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-message-contracts"></a>Utilizando contratos de mensagem
Normalmente ao criar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativos, os desenvolvedores preste muita atenção para as estruturas de dados e os problemas de serialização e não precisa se preocupar com a estrutura de mensagens no qual os dados são executados. Para esses aplicativos, a criação de contratos de dados para os parâmetros ou valores de retorno é simples. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 No entanto, às vezes, total controle sobre a estrutura de uma mensagem SOAP é tão importante quanto o controle sobre seu conteúdo. Isso é especialmente verdadeiro quando a interoperabilidade é importante ou problemas de controle especificamente a segurança no nível da mensagem ou parte da mensagem. Nesses casos, você pode criar um *contrato de mensagem* que permite que você especifique a estrutura da mensagem SOAP exata necessário.  
  
 Este tópico discute como usar os vários atributos de contrato de mensagem para criar um contrato de mensagem específica para a operação.  
  
## <a name="using-message-contracts-in-operations"></a>Usando contratos de mensagem em operações  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dá suporte a operações modeladas no *estilo do procedimento remoto (RPC) chamada* ou *mensagens estilo*. Em uma operação de estilo RPC, você pode usar qualquer tipo serializável, e você tem acesso aos recursos que estão disponíveis para chamadas locais, como vários parâmetros e `ref` e `out` parâmetros. Neste estilo, o formato de serialização escolhida controla a estrutura dos dados nas mensagens subjacentes e o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução cria as mensagens para dar suporte à operação. Isso permite que os desenvolvedores que não estão familiarizados com SOAP e as mensagens de SOAP rapidamente e facilmente criar e usam aplicativos de serviço.  
  
 O exemplo de código a seguir mostra uma operação de serviço estabelecida no estilo RPC.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Normalmente, um contrato de dados é suficiente para definir o esquema para as mensagens. Por exemplo, no exemplo anterior, é suficiente para a maioria dos aplicativos se `BankingTransaction` e `BankingTransactionResponse` ter contratos de dados para definir o conteúdo das mensagens de SOAP subjacentes. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]contratos de dados, consulte [usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 No entanto, ocasionalmente, é necessário controlar exatamente como a estrutura da mensagem SOAP transmitidos eletronicamente. O cenário mais comum para isso é inserir cabeçalhos SOAP personalizados. Outro cenário comum é para definir propriedades de segurança para os cabeçalhos da mensagem e o corpo, ou seja, para decidir se esses elementos são assinados digitalmente e criptografados. Finalmente, algumas pilhas SOAP de terceiros exigem que as mensagens em um formato específico. As operações de mensagens de estilo fornecem esse controle.  
  
 Uma operação de estilo de mensagens tem no máximo um parâmetro e um valor de retorno em que ambos os tipos são tipos de mensagem. ou seja, que são serializados diretamente em uma estrutura de mensagens SOAP especificada. Isso pode ser qualquer tipo marcado com o <xref:System.ServiceModel.MessageContractAttribute> ou <xref:System.ServiceModel.Channels.Message> tipo. O exemplo de código a seguir mostra uma operação semelhante para o estilo de RCP anterior, mas que usa o estilo de mensagens.  
  
 Por exemplo, se `BankingTransaction` e `BankingTransactionResponse` são os dois tipos de contratos de mensagem, em seguida, o código em que as operações a seguir é válido.  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 No entanto, o código a seguir é inválido.  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 Uma exceção é gerada para qualquer operação que envolve um tipo de contrato de mensagem e que não siga um dos padrões de válido. Obviamente, as operações que envolvem tipos de contrato de mensagem não estão sujeitos essas restrições.  
  
 Se um tipo tem um contrato de mensagem e um contrato de dados, somente seu contrato de mensagem é considerado quando o tipo é usado em uma operação.  
  
## <a name="defining-message-contracts"></a>Definindo contratos de mensagem  
 Para definir um contrato de mensagem para um tipo (ou seja, para definir o mapeamento entre o tipo e um envelope SOAP), aplique o <xref:System.ServiceModel.MessageContractAttribute> para o tipo. Em seguida, aplique a <xref:System.ServiceModel.MessageHeaderAttribute> aos membros do tipo que você deseja transformar em cabeçalhos SOAP e aplicar o <xref:System.ServiceModel.MessageBodyMemberAttribute> aos membros você deseja transformar em partes do corpo da mensagem SOAP.  
  
 O código a seguir fornece um exemplo do uso de um contrato de mensagem.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 Ao usar esse tipo como um parâmetro de operação, é gerado o envelope SOAP a seguir:  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 Observe que `operation` e `transactionDate` aparecem como cabeçalhos SOAP e o corpo SOAP consiste em um elemento wrapper `BankingTransaction` contendo `sourceAccount`,`targetAccount`, e `amount`.  
  
 Você pode aplicar o <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> para todos os campos, propriedades e eventos, independentemente de estarem público, privado, protegido ou interno.  
  
 O <xref:System.ServiceModel.MessageContractAttribute> permite que você especifique os atributos WrapperName e WrapperNamespace que controlam o nome do elemento wrapper no corpo da mensagem SOAP. Por padrão o nome do contrato de mensagem de tipo é usado para o wrapper e o namespace no qual o contrato de mensagem é definido `HYPERLINK "http://tempuri.org/" http://tempuri.org/` é usado como o namespace padrão.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.KnownTypeAttribute>atributos são ignorados em contratos de mensagem. Se um <xref:System.Runtime.Serialization.KnownTypeAttribute> é necessário, coloque-o sobre a operação que está usando o contrato de mensagem em questão.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Controle de cabeçalho e nomes de partes de corpo e Namespaces  
 Na representação de um contrato de mensagem SOAP, cada parte de cabeçalho e corpo mapeia para um elemento XML que tem um nome e um namespace.  
  
 Por padrão, o namespace é o mesmo que o namespace do contrato de serviço que está participando de mensagem e o nome é determinado pelo nome de membro para o qual o <xref:System.ServiceModel.MessageHeaderAttribute> ou <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos são aplicados.  
  
 Você pode alterar esses padrões manipulando o <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (na classe pai do <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos).  
  
 Considere a classe no exemplo de código a seguir.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 Neste exemplo, o `IsAudited` cabeçalho está no namespace especificado no código e a parte do corpo que representa o `theData` membro é representado por um elemento XML com o nome `transactionData`. O exemplo a seguir mostra o XML gerado para este contrato de mensagem.  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>Controlar se as partes de corpo SOAP são quebradas  
 Por padrão, as partes de corpo SOAP são serializadas dentro de um elemento encapsulado. Por exemplo, o código a seguir mostra o `HelloGreetingMessage` elemento wrapper gerado do nome do <xref:System.ServiceModel.MessageContractAttribute> tipo no contrato de mensagem para o `HelloGreetingMessage` mensagem.  
  
 [!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
 [!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Para suprimir o elemento wrapper, defina o <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> propriedade `false`. Para controlar o nome e o namespace do elemento wrapper, use o <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> e <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> propriedades.  
  
> [!NOTE]
>  Ter mais de uma parte de corpo de mensagem em mensagens que não são encapsuladas não é compatível com o WS-I Basic perfil 1.1 e não é recomendado durante a criação de novos contratos de mensagem. No entanto, é necessário ter mais de uma parte do corpo da mensagem não encapsulada em determinados cenários específicos de interoperabilidade. Se você pretende transmitir mais de uma parte dos dados no corpo da mensagem, é recomendável usar o modo padrão (quebrada). Ter mais de um cabeçalho de mensagem em mensagens sem é totalmente aceitável.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Usando tipos personalizados em contratos de mensagem  
 Cada cabeçalho de mensagem individual e parte do corpo da mensagem é serializado (transformado em XML) usando o mecanismo de serialização escolhidas para o contrato de serviço em que a mensagem é usada. O mecanismo de serialização padrão, o `XmlFormatter`, pode lidar com qualquer tipo que tem um contrato de dados, ou explicitamente (fazendo com que o <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) ou implicitamente (por ser um tipo primitivo, tendo o <xref:System.SerializableAttribute?displayProperty=nameWithType>, e assim por diante). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 No exemplo anterior, o `Operation` e `BankingTransactionData` tipos devem ter um contrato de dados, e `transactionDate` pode ser serializado porque <xref:System.DateTime> é um primitivo (e portanto, tem um contrato de dados implícitos).  
  
 No entanto, é possível alternar para um mecanismo de serialização diferentes, o `XmlSerializer`. Se você fizer existe essa chave, você deve garantir que todos os tipos usados para cabeçalhos de mensagem e partes de corpo são serializável usando o `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>Usando matrizes dentro de contratos de mensagem  
 Você pode usar matrizes de elementos em contratos de mensagem de duas maneiras de repetição.  
  
 A primeira é usar um <xref:System.ServiceModel.MessageHeaderAttribute> ou um <xref:System.ServiceModel.MessageBodyMemberAttribute> diretamente na matriz. Nesse caso, a matriz inteira é serializada como um elemento (ou seja, um cabeçalho ou uma parte de corpo) com vários elementos filho. Considere a classe no exemplo a seguir.  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 Isso resulta em cabeçalhos SOAP é semelhante ao seguinte.  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 Uma alternativa para isso é usar o <xref:System.ServiceModel.MessageHeaderArrayAttribute>. Nesse caso, cada elemento da matriz é serializado de forma independente e para cada elemento de matriz tem um cabeçalho, semelhante ao seguinte.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 O nome padrão para as entradas da matriz é o nome do membro para o qual o <xref:System.ServiceModel.MessageHeaderArrayAttribute> atributos é aplicada.  
  
 O <xref:System.ServiceModel.MessageHeaderArrayAttribute> atributo herda o <xref:System.ServiceModel.MessageHeaderAttribute>. Ele tem o mesmo conjunto de recursos, como os atributos de não-matriz, por exemplo, é possível definir a ordem, o nome e o namespace para uma matriz de cabeçalhos da mesma forma, que você pode configurá-lo para um único cabeçalho. Quando você usa o `Order` propriedade em uma matriz, ela se aplica a toda a matriz.  
  
 Você pode aplicar o <xref:System.ServiceModel.MessageHeaderArrayAttribute> somente a matrizes, coleções não.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Usando matrizes de bytes em contratos de mensagem  
 Matrizes de bytes, quando usado com os atributos de matriz não (<xref:System.ServiceModel.MessageBodyMemberAttribute> e <xref:System.ServiceModel.MessageHeaderAttribute>), não são tratadas como matrizes, mas como um tipo primitivo especial representados como dados codificados na Base64 no XML resultante.  
  
 Quando você usa matrizes de bytes com o atributo de matriz <xref:System.ServiceModel.MessageHeaderArrayAttribute>, os resultados dependem do serializador em uso. Com o serializador padrão, a matriz é representada como uma entrada individual para cada byte. No entanto, quando o `XmlSerializer` for selecionada, (usando o <xref:System.ServiceModel.XmlSerializerFormatAttribute> no contrato de serviço), matrizes de bytes são tratadas como dados de Base64 independentemente se os atributos de matriz ou matriz não são usados.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Assinar e criptografar as partes da mensagem  
 Um contrato de mensagem pode indicar se os cabeçalhos de e/ou o corpo da mensagem deve ser assinado digitalmente e criptografado.  
  
 Isso é feito definindo o <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> propriedade o <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos. A propriedade é uma enumeração do <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> de tipo e pode ser definido como <xref:System.Net.Security.ProtectionLevel.None> (sem criptografia ou assinatura), <xref:System.Net.Security.ProtectionLevel.Sign> (somente assinatura digital), ou <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (criptografia e uma assinatura digital). O padrão é <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Esses recursos de segurança trabalhar, você deve configurar adequadamente a associação e os comportamentos. Se você usar esses recursos de segurança sem a configuração apropriada (por exemplo, a tentativa de assinar uma mensagem sem fornecer suas credenciais), uma exceção é lançada em tempo de validação.  
  
 Para cabeçalhos de mensagem, o nível de proteção é determinado individualmente para cada cabeçalho.  
  
 Para partes de corpo de mensagem, o nível de proteção pode ser pensado como "nível mínimo de proteção". O corpo tem o nível de proteção apenas um, independentemente do número de partes de corpo. O nível de proteção do corpo é determinado pelo maior <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> configuração de propriedade de todas as partes de corpo. No entanto, você deve definir o nível de proteção de cada parte do corpo para a proteção mínimo real nível necessária.  
  
 Considere a classe no exemplo de código a seguir.  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 Neste exemplo, o `recordID` cabeçalho não estiver protegido, `patientName` é `signed`, e `SSN` é criptografado e assinado. Parte do corpo de pelo menos um, `medicalHistory`, tem <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> aplicado, e, portanto, o corpo da mensagem inteira é criptografado e assinado, embora os comentários e partes de corpo de diagnóstico especificam níveis inferiores de proteção.  
  
## <a name="soap-action"></a>Ação SOAP  
 SOAP e padrões relacionados de serviços Web definem uma propriedade chamada `Action` que podem estar presentes para cada mensagem SOAP enviada. A operação <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> propriedades controlam o valor dessa propriedade.  
  
## <a name="soap-header-attributes"></a>Atributos de cabeçalho SOAP  
 O padrão SOAP define os seguintes atributos que podem existir em um cabeçalho de:  
  
-   `Actor/Role`(`Actor` em SOAP 1.1, `Role` em SOAP 1.2)  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 O `Actor` ou `Role` atributo especifica o identificador de URI (Uniform Resource) do nó para o qual um determinado cabeçalho é pretendido. O `MustUnderstand` atributo especifica se o nó de processar o cabeçalho deve entender. O `Relay` atributo especifica se o cabeçalho deve ser retransmitidas para nós de downstream. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]não executa qualquer processamento desses atributos em mensagens de entrada, exceto para o `MustUnderstand` atributo, conforme especificado na seção "Controle de versão de contrato de mensagem", mais adiante neste tópico. No entanto, ele permite que você ler e gravar esses atributos conforme necessário, como a descrição a seguir.  
  
 Ao enviar uma mensagem, esses atributos não são emitidos por padrão. Você pode alterar isso de duas maneiras. Primeiro, você pode estaticamente definir os atributos para qualquer valor desejado, alterando o <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, e <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> propriedades, conforme mostrado no exemplo de código a seguir. (Observe que não há nenhum `Role` propriedade; a configuração a <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> propriedade emite o `Role` atributo se você estiver usando SOAP 1.2).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 A segunda maneira de controlar esses atributos dinamicamente, é por meio de código. Você pode obter isso ao encapsular o tipo desejado de cabeçalho no <xref:System.ServiceModel.MessageHeader%601> tipo (cuidado para não confunda esse tipo com a versão não genérica) e usando o tipo junto com o <xref:System.ServiceModel.MessageHeaderAttribute>. Em seguida, você pode usar propriedades no <xref:System.ServiceModel.MessageHeader%601> para definir os atributos SOAP, conforme mostrado no exemplo de código a seguir.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 Se você usar dinâmico e os mecanismos de controle estático, as configurações estáticas são usadas como padrão, mas podem ser substituídas posteriormente usando o mecanismo dinâmico, conforme mostrado no código a seguir.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Criando cabeçalhos repetidos com controle de atributo dinâmico é permitido, conforme mostrado no código a seguir.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 No lado de recepção, ler esses atributos SOAP só pode ser feito se o <xref:System.ServiceModel.MessageHeader%601> classe é usada para o cabeçalho no tipo. Examine o `Actor`, `Relay`, ou `MustUnderstand` propriedades de um cabeçalho do <xref:System.ServiceModel.MessageHeader%601> tipo para descobrir as configurações de atributo na mensagem recebida.  
  
 Quando uma mensagem é recebida e, em seguida, enviada de volta, as configurações de atributo SOAP apenas ir ida e volta para cabeçalhos do <xref:System.ServiceModel.MessageHeader%601> tipo.  
  
## <a name="order-of-soap-body-parts"></a>Ordem das partes de corpo SOAP  
 Em algumas circunstâncias, talvez seja necessário controlar a ordem das partes de corpo. A ordem dos elementos do corpo é alfabética por padrão, mas pode ser controlada pelo <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> propriedade. Essa propriedade tem a mesma semântica de <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> propriedade, exceto o comportamento em cenários de herança (em contratos de mensagem, membros não são classificados antes dos membros de corpo de tipo derivado de corpo de tipo base). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 No exemplo a seguir, `amount` normalmente seriam primeiro porque ele é o primeiro em ordem alfabética. No entanto, o <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> propriedade coloca na terceira posição.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a>Controle de versão de contrato de mensagem  
 Ocasionalmente, talvez seja necessário alterar contratos de mensagem. Por exemplo, uma nova versão do seu aplicativo pode adicionar um cabeçalho extra a uma mensagem. Em seguida, ao enviar da nova versão para o antigo, o sistema deve lidar com um cabeçalho extra, bem como um cabeçalho ausente ao ir na outra direção.  
  
 As seguintes regras se aplicam a cabeçalhos de controle de versão:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]objeto não aos cabeçalhos ausentes — os membros correspondentes são deixados em seus valores padrão.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]também ignora inesperados cabeçalhos adicionais. A única exceção a essa regra é se o cabeçalho extra tem um `MustUnderstand` atributo definido como `true` na mensagem SOAP de entrada — nesse caso, uma exceção será lançada como um cabeçalho que deve ser compreendido não pode ser processado.  
  
 Corpos de tem regras semelhantes de controle de versão de mensagem — partes de corpo de mensagem ausente e adicionais são ignorados.  
  
## <a name="inheritance-considerations"></a>Considerações de herança  
 Um tipo de contrato de mensagem pode herdar de outro tipo, como o tipo base também tem um contrato de mensagem.  
  
 Ao criar ou acessar uma mensagem usando um tipo de contrato de mensagem que herda de outros tipos de contrato de mensagem, as seguintes regras se aplicam:  
  
-   Todos os cabeçalhos de mensagem na hierarquia de herança são coletados juntos para formar o conjunto completo de cabeçalhos da mensagem.  
  
-   Todas as partes de corpo de mensagem na hierarquia de herança são coletadas juntos para formar o corpo da mensagem completa. As partes de corpo são ordenadas de acordo com as regras de ordenação comuns (por <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> propriedade e, em seguida, em ordem alfabética), nenhuma relevância para seu local na hierarquia de herança. Usando a herança de contrato de mensagem em que as partes de corpo de mensagem ocorrerem em vários níveis de árvore de herança é altamente desaconselhável. Se uma classe base e uma classe derivada definem um cabeçalho ou uma parte de corpo com o mesmo nome, o membro da classe base mais é usado para armazenar o valor da parte cabeçalho ou no corpo.  
  
 Considere as classes no exemplo de código a seguir.  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 O `PatientRecord` classe descreve uma mensagem com um cabeçalho chamado `ID`. O cabeçalho corresponde do `personID` e não o `patientID` membro, porque o membro de mais de base é escolhido. Portanto, o `patientID` campo nesse caso é inútil. O corpo da mensagem contém o `diagnosis` elemento seguido de `patientName` elemento, porque é a ordem alfabética. Observe que o exemplo mostra um padrão que é altamente desaconselhável: a base e os contratos de mensagem derivados tem partes de corpo de mensagem.  
  
## <a name="wsdl-considerations"></a>Considerações de WSDL  
 Quando um serviço que usa os contratos de mensagem para gerar um contrato de WSDL Web Services Description Language (), é importante lembrar que nem todos os recursos de contrato de mensagem são refletidos no WSDL resultante. Considere os seguintes pontos:  
  
-   WSDL não pode expressar o conceito de uma matriz de cabeçalhos. Ao criar as mensagens com uma matriz de cabeçalhos usando o <xref:System.ServiceModel.MessageHeaderArrayAttribute>, o WSDL resultante reflete apenas um cabeçalho, em vez de matriz.  
  
-   O documento WSDL resultante talvez não reflita algumas informações de nível de proteção.  
  
-   O tipo de mensagem gerado no WSDL tem o mesmo nome que o nome da classe do tipo de contrato de mensagem.  
  
-   Quando usar a mesma mensagem de contrato em várias operações, vários tipos de mensagem são gerados no documento WSDL. Os nomes são feitos exclusivos, adicionando os números "2", "3" e assim por diante, para usos subsequentes. Ao importar novamente o WSDL, vários tipos de contrato de mensagem são criados e são idênticos, exceto seus nomes.  
  
## <a name="soap-encoding-considerations"></a>Considerações de codificação de SOAP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]permite que você use o SOAP herdado codificação de estilo de XML, no entanto, seu uso não é recomendável. Ao usar esse estilo (definindo o `Use` propriedade `Encoded` no <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> aplicados ao contrato de serviço), as seguintes considerações adicionais se aplicam:  
  
-   Não há suporte para os cabeçalhos de mensagem; Isso significa que o atributo <xref:System.ServiceModel.MessageHeaderAttribute> e o atributo de matriz <xref:System.ServiceModel.MessageHeaderArrayAttribute> são incompatíveis com codificação SOAP.  
  
-   Se o contrato de mensagem não está quebrado, ou seja, se a propriedade <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> é definido como `false`, o contrato de mensagem pode ter parte de apenas um corpo.  
  
-   O nome do elemento wrapper para o contrato de mensagem de solicitação deve corresponder ao nome de operação. Use o `WrapperName` o contrato de mensagem para essa propriedade.  
  
-   O nome do elemento wrapper para o contrato de mensagem de resposta deve ser igual ao nome da operação de sufixo 'Resposta'. Use o <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> o contrato de mensagem para essa propriedade.  
  
-   Codificação SOAP preserva as referências de objeto. Por exemplo, considere o código a seguir.  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 Depois de serializar a mensagem usando a codificação de SOAP, `changedFrom` e `changedTo` não contêm suas próprias cópias de `p`, mas em vez disso, aponte para a cópia dentro a `changedBy` elemento.  
  
## <a name="performance-considerations"></a>Considerações sobre desempenho  
 Cada cabeçalho de mensagem e a parte do corpo da mensagem é serializado independentemente de outras pessoas. Portanto, os mesmos namespaces pode ser declarados novamente para cada cabeçalho e a parte do corpo. Para melhorar o desempenho, especialmente em termos de tamanho da mensagem na conexão, Consolide vários cabeçalhos e partes de corpo em uma única parte de cabeçalho ou no corpo. Por exemplo, em vez do código a seguir:  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 Use este código.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Baseado em evento assíncrono e contratos de mensagem  
 As diretrizes de design do modelo assíncrono baseado em eventos declaram que, se mais de um valor for retornado, um valor será retornado como a propriedade `Result` e os outros serão retornados como propriedades no objeto <xref:System.EventArgs>. Um resultado é que, se um cliente importar metadados usando as opções de comando assíncrono com base em eventos, e a operação retornar mais de um valor, o objeto padrão <xref:System.EventArgs> retornará um valor como a propriedade `Result` e os restantes serão propriedades do objeto <xref:System.EventArgs>.  
  
 Se você desejar receber o objeto de mensagem como a propriedade `Result` e ter valores retornados como propriedades nesse objeto, use a opção de comando `/messageContract`. Isso gera uma assinatura que retorna a mensagem de resposta como a propriedade `Result` no objeto <xref:System.EventArgs>. Todos os valores de retorno internos são propriedades do objeto da mensagem de resposta.  
  
## <a name="see-also"></a>Consulte também  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md) (Serviços de design e implantação)
