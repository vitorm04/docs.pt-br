---
title: Utilizando contratos de mensagem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 4c5f1ab0b6fa56e4836a950ca3f2bbad19cfbff2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932789"
---
# <a name="using-message-contracts"></a>Utilizando contratos de mensagem
Normalmente, ao criar aplicativos do Windows Communication Foundation (WCF), os desenvolvedores preste muita atenção para as estruturas de dados e os problemas de serialização e não preciso me preocupar com a estrutura das mensagens na qual os dados são executados. Para esses aplicativos, criação de contratos de dados para os parâmetros ou valores de retorno é simples. (Para obter mais informações, consulte [especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 No entanto, às vezes, total controle sobre a estrutura de uma mensagem SOAP é tão importante quanto controle sobre seu conteúdo. Isso é especialmente verdadeiro quando a interoperabilidade é importante ou problemas de controle especificamente a segurança no nível da mensagem ou parte da mensagem. Nesses casos, você pode criar uma *contrato de mensagem* que permite que você especificar a estrutura da mensagem SOAP precisa necessárias.  
  
 Este tópico discute como usar os vários atributos de contrato de mensagem para criar um contrato de mensagem específica para sua operação.  
  
## <a name="using-message-contracts-in-operations"></a>Usando contratos de mensagem em operações  
 WCF dá suporte a operações modeladas em qualquer um de *estilo do procedimento remoto (RPC) chamada* ou o *estilo de mensagens*. Em uma operação de estilo RPC, você pode usar qualquer tipo serializável, e você tem acesso aos recursos que estão disponíveis para chamadas locais, como vários parâmetros e `ref` e `out` parâmetros. Neste estilo, a estrutura dos dados em que as mensagens subjacentes controla a forma de serialização escolhida e o tempo de execução do WCF cria as mensagens para o suporte para a operação. Isso permite que os desenvolvedores que não estão familiarizados com SOAP e as mensagens de SOAP rapidamente e facilmente criar e usam aplicativos de serviço.  
  
 O exemplo de código a seguir mostra uma operação de serviço modelada no estilo RPC.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Normalmente, um contrato de dados é suficiente para definir o esquema para as mensagens. Por exemplo, no exemplo anterior, é suficiente para a maioria dos aplicativos se `BankingTransaction` e `BankingTransactionResponse` têm contratos de dados para definir o conteúdo das mensagens SOAP subjacentes. Para obter mais informações sobre contratos de dados, consulte [contratos de dados usando](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 No entanto, ocasionalmente, é necessário controlar com precisão como a estrutura da mensagem SOAP transmitidos eletronicamente. O cenário mais comum para isso é inserindo cabeçalhos SOAP personalizados. Outro cenário comum é para definir propriedades de segurança para os cabeçalhos da mensagem e o corpo, ou seja, para decidir se esses elementos são digitalmente assinados e criptografados. Por fim, algumas pilhas SOAP de terceiros exigem que as mensagens em um formato específico. Operações de estilo de mensagens fornecem esse controle.  
  
 Uma operação de estilo de mensagens tem no máximo um parâmetro e um valor de retorno em que ambos os tipos são tipos de mensagem; ou seja, que são serializados diretamente em uma estrutura de mensagem SOAP especificada. Isso pode ser qualquer tipo marcado com o <xref:System.ServiceModel.MessageContractAttribute> ou o <xref:System.ServiceModel.Channels.Message> tipo. O exemplo de código a seguir mostra uma operação similar ao estilo de RCP anterior, mas que usa o estilo de mensagens.  
  
 Por exemplo, se `BankingTransaction` e `BankingTransactionResponse` são ambos os tipos de contratos de mensagem, em seguida, o código em que as operações a seguir é válido.  
  
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
  
 Uma exceção é gerada para qualquer operação que envolve um tipo de contrato de mensagem e que não segue um dos padrões válidos. É claro que, operações que não envolvem tipos de contrato de mensagem não estão sujeitos a essas restrições.  
  
 Se um tipo tem um contrato de mensagem e um contrato de dados, somente seu contrato de mensagem é considerado quando o tipo é usado em uma operação.  
  
## <a name="defining-message-contracts"></a>Definindo contratos de mensagem  
 Para definir um contrato de mensagem para um tipo (ou seja, para definir o mapeamento entre o tipo e um envelope SOAP), aplique o <xref:System.ServiceModel.MessageContractAttribute> para o tipo. Em seguida, aplicar a <xref:System.ServiceModel.MessageHeaderAttribute> aos membros do tipo que você deseja transformar em cabeçalhos SOAP e aplicar o <xref:System.ServiceModel.MessageBodyMemberAttribute> aos membros você deseja transformar em partes do corpo da mensagem SOAP.  
  
 O código a seguir fornece um exemplo de como usar um contrato de mensagem.  
  
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
  
 Você pode aplicar a <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> para todos os campos, propriedades e eventos, independentemente de estarem público, privado, protegido ou interno.  
  
 O <xref:System.ServiceModel.MessageContractAttribute> permite que você especifique os atributos WrapperName e WrapperNamespace que controlam o nome do elemento wrapper no corpo da mensagem SOAP. Por padrão o nome do contrato de mensagem de tipo é usado para o wrapper e o namespace no qual o contrato de mensagem é definido `http://tempuri.org/` é usado como o namespace padrão.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.KnownTypeAttribute> atributos são ignorados em contratos de mensagem. Se um <xref:System.Runtime.Serialization.KnownTypeAttribute> é necessário, coloque-o sobre a operação que está usando o contrato de mensagem em questão.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Controle de cabeçalho e nomes de partes de corpo e Namespaces  
 Na representação de SOAP de um contrato de mensagem, cada parte de cabeçalho e corpo é mapeado para um elemento XML que tem um nome e um namespace.  
  
 Por padrão, o namespace é o mesmo que o namespace do contrato de serviço que está participando da mensagem e o nome é determinado pelo nome de membro ao qual o <xref:System.ServiceModel.MessageHeaderAttribute> ou o <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos são aplicados.  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>Controlar se as partes de corpo SOAP são encapsuladas  
 Por padrão, as partes de corpo SOAP são serializadas dentro de um elemento encapsulado. Por exemplo, o código a seguir mostra a `HelloGreetingMessage` elemento wrapper gerado do nome da <xref:System.ServiceModel.MessageContractAttribute> tipo no contrato de mensagem para o `HelloGreetingMessage` mensagem.  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Para suprimir o elemento wrapper, defina as <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> propriedade para `false`. Para controlar o nome e o namespace do elemento wrapper, use o <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> e <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> propriedades.  
  
> [!NOTE]
>  Ter mais de uma parte de corpo de mensagem em mensagens que não são encapsuladas não está em conformidade com WS-I Basic 1.1 de perfil e não é recomendado ao projetar novos contratos de mensagem. No entanto, é necessário ter mais de uma parte de corpo de mensagem sem quebra de texto em determinados cenários específicos de interoperabilidade. Se você pretende transmitir mais de uma parte dos dados no corpo da mensagem, é recomendável usar o modo padrão (encapsulado). Ter mais de um cabeçalho de mensagem nas mensagens sem quebra de texto é totalmente aceitável.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Usando tipos personalizados dentro de contratos de mensagem  
 Cada cabeçalho de mensagem individual e a parte do corpo da mensagem é serializado (transformadas em XML) usando o mecanismo de serialização escolhido para o contrato de serviço em que a mensagem é usada. O mecanismo de serialização padrão, o `XmlFormatter`, pode lidar com qualquer tipo que tem um contrato de dados, ou explicitamente (fazendo com que o <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) ou implicitamente (por ser um tipo primitivo, tendo o <xref:System.SerializableAttribute?displayProperty=nameWithType>e assim por diante). Para obter mais informações, consulte [contratos de dados usando](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 No exemplo anterior, o `Operation` e `BankingTransactionData` tipos devem ter um contrato de dados, e `transactionDate` pode ser serializado porque <xref:System.DateTime> é um primitivo (e, portanto, tem um contrato de dados implícita).  
  
 No entanto, é possível alternar para um mecanismo de serialização diferentes, o `XmlSerializer`. Se você fizer existe essa chave, você deve garantir que todos os tipos usados para partes de corpo e cabeçalhos de mensagem são serializados usando a `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>Usando matrizes de contratos de mensagem  
 Você pode usar matrizes de elementos em contratos de mensagem de duas maneiras de repetição.  
  
 A primeira é usar um <xref:System.ServiceModel.MessageHeaderAttribute> ou um <xref:System.ServiceModel.MessageBodyMemberAttribute> diretamente na matriz. Nesse caso, toda a matriz é serializada como um elemento (ou seja, um cabeçalho ou uma parte de corpo) com vários elementos filhos. Considere a classe no exemplo a seguir.  
  
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
  
 Uma alternativa para isso é usar o <xref:System.ServiceModel.MessageHeaderArrayAttribute>. Nesse caso, cada elemento da matriz é serializado de forma independente e para que cada elemento da matriz tem um cabeçalho, semelhante ao seguinte.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 O nome padrão para as entradas de matriz é o nome do membro ao qual o <xref:System.ServiceModel.MessageHeaderArrayAttribute> atributos é aplicado.  
  
 O <xref:System.ServiceModel.MessageHeaderArrayAttribute> atributo herda o <xref:System.ServiceModel.MessageHeaderAttribute>. Ele tem o mesmo conjunto de recursos, como os atributos de não matriz, por exemplo, é possível definir a ordem, o nome e o namespace para uma matriz de cabeçalhos da mesma forma que você pode defini-lo para um único cabeçalho. Quando você usa o `Order` propriedade em uma matriz, ele se aplica a toda a matriz.  
  
 Você pode aplicar o <xref:System.ServiceModel.MessageHeaderArrayAttribute> somente a matrizes, coleções não.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Usando matrizes de bytes em contratos de mensagem  
 Matrizes de bytes, quando usado com os atributos não sejam de matriz (<xref:System.ServiceModel.MessageBodyMemberAttribute> e <xref:System.ServiceModel.MessageHeaderAttribute>), não são tratados como matrizes, mas como um tipo especial de primitivo representados como dados codificados na Base64 no XML resultante.  
  
 Quando você usa matrizes de bytes com o atributo de matriz <xref:System.ServiceModel.MessageHeaderArrayAttribute>, os resultados dependem do serializador em uso. Com o serializador padrão, a matriz é representada como uma entrada individual para cada byte. No entanto, quando o `XmlSerializer` estiver selecionada, (usando o <xref:System.ServiceModel.XmlSerializerFormatAttribute> no contrato de serviço), matrizes de bytes são tratados como dados de Base64, independentemente de se os atributos de matriz ou não sejam de matriz são usados.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Assinar e criptografar as partes da mensagem  
 Um contrato de mensagem pode indicar se os cabeçalhos de e/ou o corpo da mensagem deve ser digitalmente assinado e criptografado.  
  
 Isso é feito definindo a <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> propriedade sobre a <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos. A propriedade é uma enumeração do <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> de tipo e pode ser definido como <xref:System.Net.Security.ProtectionLevel.None> (sem criptografia ou assinatura), <xref:System.Net.Security.ProtectionLevel.Sign> (somente assinatura digital), ou <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (criptografia e uma assinatura digital). O padrão é <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Para esses recursos de segurança trabalhar, você deve configurar corretamente a associação e comportamentos. Se você usar esses recursos de segurança sem a configuração adequada (por exemplo, a tentativa de assinar uma mensagem sem fornecer suas credenciais), uma exceção é gerada em tempo de validação.  
  
 Para cabeçalhos de mensagem, o nível de proteção é determinado individualmente para cada cabeçalho.  
  
 Para partes de corpo de mensagem, o nível de proteção pode ser pensado como "nível mínimo de proteção". O corpo tem nível de proteção de apenas um, independentemente do número de partes do corpo. O nível de proteção do corpo é determinado pelo mais alto <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> configuração da propriedade de todas as partes de corpo. No entanto, você deve definir o nível de proteção de cada parte do corpo para a proteção mínimo real nível necessária.  
  
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
  
 Neste exemplo, o `recordID` cabeçalho não estiver protegido, `patientName` é `signed`, e `SSN` é criptografado e assinado. Parte de corpo pelo menos um `medicalHistory`, tem <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> aplicado, e, portanto, o corpo da mensagem inteira é criptografado e assinado, mesmo que os comentários e as partes do corpo do diagnóstico especificam níveis inferiores de proteção.  
  
## <a name="soap-action"></a>Ação SOAP  
 SOAP e padrões de serviços da Web relacionados a definir uma propriedade chamada `Action` que podem estar presentes para cada mensagem SOAP enviada. A operação <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> propriedades controlam o valor dessa propriedade.  
  
## <a name="soap-header-attributes"></a>Atributos de cabeçalho SOAP  
 O padrão SOAP define os seguintes atributos que podem existir em um cabeçalho:  
  
- `Actor/Role` (`Actor` em SOAP 1.1, `Role` em SOAP 1.2)  
  
- `MustUnderstand`  
  
- `Relay`  
  
 O `Actor` ou `Role` atributo especifica o URI Uniform Resource Identifier () do nó para o qual um determinado cabeçalho é pretendido. O `MustUnderstand` atributo especifica se o nó de processar o cabeçalho deve compreender. O `Relay` atributo especifica se o cabeçalho deve ser retransmitido para nós de downstream. WCF não executa qualquer processamento desses atributos nas mensagens de entrada, exceto para o `MustUnderstand` atributo, conforme especificado na seção "Controle de versão de contrato de mensagem", mais adiante neste tópico. No entanto, ele permite que você ler e gravar esses atributos conforme necessário, como a descrição a seguir.  
  
 Ao enviar uma mensagem, esses atributos não são emitidos por padrão. Você pode alterar isso de duas maneiras. Primeiro, você pode estaticamente define os atributos para todos os valores desejados, alterando a <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, e <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> propriedades, conforme mostrado no exemplo de código a seguir. (Observe que não há nenhum `Role` propriedade; configuração o <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> propriedade emite o `Role` atributo se você estiver usando o SOAP 1.2).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 A segunda maneira de controlar esses atributos dinamicamente, é por meio de código. Você pode obter isso encapsulando o tipo desejado de cabeçalho na <xref:System.ServiceModel.MessageHeader%601> tipo (certifique-se para não confundir esse tipo com a versão não genérica) e usando o tipo junto com o <xref:System.ServiceModel.MessageHeaderAttribute>. Em seguida, você pode usar propriedades sobre o <xref:System.ServiceModel.MessageHeader%601> para definir os atributos SOAP, conforme mostrado no exemplo de código a seguir.  
  
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
  
 Se você usar dinâmica e os mecanismos de controle estático, as configurações estáticas são usadas como padrão, mas podem ser substituídas mais tarde usando o mecanismo dinâmico, conforme mostrado no código a seguir.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Criando cabeçalhos repetidos com controle de atributo dinâmico é permitida, conforme mostrado no código a seguir.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 No lado do recebimento, ler esses atributos SOAP só pode ser feito se o <xref:System.ServiceModel.MessageHeader%601> classe é usada para o cabeçalho no tipo. Examine os `Actor`, `Relay`, ou `MustUnderstand` propriedades de um cabeçalho do <xref:System.ServiceModel.MessageHeader%601> tipo para descobrir as configurações de atributo na mensagem recebida.  
  
 Quando uma mensagem é recebida e, em seguida, enviada de volta, as configurações de atributo SOAP chegar apenas ida e volta para os cabeçalhos do <xref:System.ServiceModel.MessageHeader%601> tipo.  
  
## <a name="order-of-soap-body-parts"></a>Ordem das partes de corpo SOAP  
 Em algumas circunstâncias, talvez você precise controlar a ordem das partes do corpo. A ordem dos elementos do corpo é em ordem alfabética por padrão, mas pode ser controlada pela <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> propriedade. Essa propriedade tem a mesma semântica que o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> propriedade, exceto para o comportamento em cenários de herança (em contratos de mensagem, corpo do tipo base de membros não são classificados antes dos membros do corpo de tipo derivado). Para obter mais informações, consulte [ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 No exemplo a seguir, `amount` normalmente viriam primeiro porque ele é o primeiro em ordem alfabética. No entanto, o <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> propriedade coloca na terceira posição.  
  
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
 Ocasionalmente, talvez você precise alterar contratos de mensagem. Por exemplo, uma nova versão do seu aplicativo pode adicionar um cabeçalho extra a uma mensagem. Em seguida, durante o envio da nova versão e o antigo, o sistema deve lidar com um cabeçalho extra, bem como um cabeçalho ausente ao ir na outra direção.  
  
 As seguintes regras se aplicam a cabeçalhos de controle de versão:  
  
- WCF não objeto aos cabeçalhos ausentes — os membros correspondentes são deixados em seus valores padrão.  
  
- O WCF também ignora cabeçalhos adicionais inesperados. A única exceção a essa regra é se o cabeçalho extra tem um `MustUnderstand` atributo definido como `true` na mensagem SOAP de entrada — nesse caso, uma exceção é lançada como um cabeçalho que deve ser compreendido não pode ser processado.  
  
 Corpos de tem regras semelhantes de controle de versão de mensagem — partes do corpo de mensagem ausente e adicionais são ignorados.  
  
## <a name="inheritance-considerations"></a>Considerações de herança  
 Um tipo de contrato de mensagem pode herdar de outro tipo, desde que o tipo base também tem um contrato de mensagem.  
  
 Ao criar ou acessar uma mensagem usando um tipo de contrato de mensagem que herda de outros tipos de contrato de mensagem, as seguintes regras se aplicam:  
  
- Todos os cabeçalhos de mensagens na hierarquia de herança são coletados juntos para formar o conjunto completo de cabeçalhos da mensagem.  
  
- Todas as partes de corpo de mensagem na hierarquia de herança são coletadas juntos para formar o corpo da mensagem completa. As partes de corpo são ordenadas de acordo com as regras de ordenação comuns (por <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> propriedade e, em seguida, em ordem alfabética), com nenhuma relevância para o seu lugar na hierarquia de herança. Usando a herança de contrato de mensagem em que as partes de corpo da mensagem ocorrerem em vários níveis de árvore de herança é altamente desaconselhável. Se uma classe base e uma classe derivada definem um cabeçalho ou uma parte do corpo com o mesmo nome, o membro da classe base mais é usado para armazenar o valor dessa parte do cabeçalho ou no corpo.  
  
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
  
 O `PatientRecord` classe descreve uma mensagem com um cabeçalho chamado `ID`. O cabeçalho corresponde do `personID` e não o `patientID` membro, porque o membro de mais de base é escolhido. Portanto, o `patientID` campo nesse caso é inútil. O corpo da mensagem contém o `diagnosis` elemento seguido o `patientName` elemento, pois é a ordem alfabética. Observe que o exemplo mostra um padrão que é altamente desaconselhável: a base e os contratos de mensagem derivada tem partes de corpo da mensagem.  
  
## <a name="wsdl-considerations"></a>Considerações de WSDL  
 Ao gerar um contrato de descrição linguagem WSDL (Web Services) de um serviço que usa os contratos de mensagem, é importante lembrar que nem todos os recursos de contrato de mensagem são refletidos no WSDL resultante. Considere os seguintes pontos:  
  
- WSDL não pode expressar o conceito de uma matriz de cabeçalhos. Durante a criação de mensagens com uma matriz de cabeçalhos usando o <xref:System.ServiceModel.MessageHeaderArrayAttribute>, o WSDL resultante reflete apenas um cabeçalho, em vez da matriz.  
  
- O documento WSDL resultante pode não refletir algumas informações de nível de proteção.  
  
- O tipo de mensagem gerado no WSDL tem o mesmo nome que o nome da classe do tipo de contrato de mensagem.  
  
- Ao usar a mesma mensagem de contrato em várias operações, vários tipos de mensagem são gerados no documento WSDL. Os nomes são feitos exclusivos, adicionando os números "2", "3" e assim por diante, para usos subsequentes. Ao importar novamente o WSDL, vários tipos de contrato de mensagem são criados e são idênticos, exceto por seus nomes.  
  
## <a name="soap-encoding-considerations"></a>Considerações de codificação de SOAP  
 O WCF permite que você use o estilo de XML, de codificação de SOAP herdado no entanto, seu uso não é recomendado. Ao usar esse estilo (definindo o `Use` propriedade para `Encoded` no <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> aplicados ao contrato de serviço), as seguintes considerações adicionais se aplicam:  
  
- Não há suporte para os cabeçalhos da mensagem; Isso significa que o atributo <xref:System.ServiceModel.MessageHeaderAttribute> e o atributo de matriz <xref:System.ServiceModel.MessageHeaderArrayAttribute> são incompatíveis com codificação SOAP.  
  
- Se o contrato de mensagem não é empacotado, ou seja, se a propriedade <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> é definido como `false`, o contrato de mensagem pode ter parte do corpo de apenas um.  
  
- O nome do elemento wrapper para o contrato de mensagem de solicitação deve corresponder ao nome da operação. Use o `WrapperName` propriedade do contrato de mensagem para isso.  
  
- O nome do elemento wrapper para o contrato de mensagem de resposta deve ser igual ao nome da operação, tendo como sufixado 'Response'. Use o <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> propriedade do contrato de mensagem para isso.  
  
- Codificação de SOAP preserva as referências de objeto. Por exemplo, considere o código a seguir.  
  
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
 Cada cabeçalho de mensagem e a parte do corpo da mensagem é serializado independentemente dos outros. Portanto, os mesmos namespaces pode ser declarados novamente para cada cabeçalho e a parte do corpo. Para melhorar o desempenho, especialmente em termos de tamanho da mensagem durante a transmissão, Consolide vários cabeçalhos e partes do corpo em uma única parte de cabeçalho ou no corpo. Por exemplo, em vez de código a seguir:  
  
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

- [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Serviços de design e implantação](../../../../docs/framework/wcf/designing-and-implementing-services.md)
