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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 14020e62e936ae6a9acad25c6c24d937feb150af
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="using-message-contracts"></a><span data-ttu-id="7201b-102">Utilizando contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="7201b-102">Using Message Contracts</span></span>
<span data-ttu-id="7201b-103">Normalmente ao criar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativos, os desenvolvedores preste muita atenção para as estruturas de dados e os problemas de serialização e não precisa se preocupar com a estrutura de mensagens no qual os dados são executados.</span><span class="sxs-lookup"><span data-stu-id="7201b-103">Typically when building [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="7201b-104">Para esses aplicativos, a criação de contratos de dados para os parâmetros ou valores de retorno é simples.</span><span class="sxs-lookup"><span data-stu-id="7201b-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="7201b-105">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span><span class="sxs-lookup"><span data-stu-id="7201b-105">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="7201b-106">No entanto, às vezes, total controle sobre a estrutura de uma mensagem SOAP é tão importante quanto o controle sobre seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="7201b-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="7201b-107">Isso é especialmente verdadeiro quando a interoperabilidade é importante ou problemas de controle especificamente a segurança no nível da mensagem ou parte da mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="7201b-108">Nesses casos, você pode criar um *contrato de mensagem* que permite que você especifique a estrutura da mensagem SOAP exata necessário.</span><span class="sxs-lookup"><span data-stu-id="7201b-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="7201b-109">Este tópico discute como usar os vários atributos de contrato de mensagem para criar um contrato de mensagem específica para a operação.</span><span class="sxs-lookup"><span data-stu-id="7201b-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="7201b-110">Usando contratos de mensagem em operações</span><span class="sxs-lookup"><span data-stu-id="7201b-110">Using Message Contracts in Operations</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7201b-111">dá suporte a operações modeladas no *estilo do procedimento remoto (RPC) chamada* ou *mensagens estilo*.</span><span class="sxs-lookup"><span data-stu-id="7201b-111"> supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="7201b-112">Em uma operação de estilo RPC, você pode usar qualquer tipo serializável, e você tem acesso aos recursos que estão disponíveis para chamadas locais, como vários parâmetros e `ref` e `out` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7201b-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="7201b-113">Neste estilo, o formato de serialização escolhida controla a estrutura dos dados nas mensagens subjacentes e o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução cria as mensagens para dar suporte à operação.</span><span class="sxs-lookup"><span data-stu-id="7201b-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime creates the messages to support the operation.</span></span> <span data-ttu-id="7201b-114">Isso permite que os desenvolvedores que não estão familiarizados com SOAP e as mensagens de SOAP rapidamente e facilmente criar e usam aplicativos de serviço.</span><span class="sxs-lookup"><span data-stu-id="7201b-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="7201b-115">O exemplo de código a seguir mostra uma operação de serviço estabelecida no estilo RPC.</span><span class="sxs-lookup"><span data-stu-id="7201b-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="7201b-116">Normalmente, um contrato de dados é suficiente para definir o esquema para as mensagens.</span><span class="sxs-lookup"><span data-stu-id="7201b-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="7201b-117">Por exemplo, no exemplo anterior, é suficiente para a maioria dos aplicativos se `BankingTransaction` e `BankingTransactionResponse` ter contratos de dados para definir o conteúdo das mensagens de SOAP subjacentes.</span><span class="sxs-lookup"><span data-stu-id="7201b-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7201b-118">contratos de dados, consulte [usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7201b-118"> data contracts, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="7201b-119">No entanto, ocasionalmente, é necessário controlar exatamente como a estrutura da mensagem SOAP transmitidos eletronicamente.</span><span class="sxs-lookup"><span data-stu-id="7201b-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="7201b-120">O cenário mais comum para isso é inserir cabeçalhos SOAP personalizados.</span><span class="sxs-lookup"><span data-stu-id="7201b-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="7201b-121">Outro cenário comum é para definir propriedades de segurança para os cabeçalhos da mensagem e o corpo, ou seja, para decidir se esses elementos são assinados digitalmente e criptografados.</span><span class="sxs-lookup"><span data-stu-id="7201b-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="7201b-122">Finalmente, algumas pilhas SOAP de terceiros exigem que as mensagens em um formato específico.</span><span class="sxs-lookup"><span data-stu-id="7201b-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="7201b-123">As operações de mensagens de estilo fornecem esse controle.</span><span class="sxs-lookup"><span data-stu-id="7201b-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="7201b-124">Uma operação de estilo de mensagens tem no máximo um parâmetro e um valor de retorno em que ambos os tipos são tipos de mensagem. ou seja, que são serializados diretamente em uma estrutura de mensagens SOAP especificada.</span><span class="sxs-lookup"><span data-stu-id="7201b-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="7201b-125">Isso pode ser qualquer tipo marcado com o <xref:System.ServiceModel.MessageContractAttribute> ou <xref:System.ServiceModel.Channels.Message> tipo.</span><span class="sxs-lookup"><span data-stu-id="7201b-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="7201b-126">O exemplo de código a seguir mostra uma operação semelhante para o estilo de RCP anterior, mas que usa o estilo de mensagens.</span><span class="sxs-lookup"><span data-stu-id="7201b-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="7201b-127">Por exemplo, se `BankingTransaction` e `BankingTransactionResponse` são os dois tipos de contratos de mensagem, em seguida, o código em que as operações a seguir é válido.</span><span class="sxs-lookup"><span data-stu-id="7201b-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="7201b-128">No entanto, o código a seguir é inválido.</span><span class="sxs-lookup"><span data-stu-id="7201b-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="7201b-129">Uma exceção é gerada para qualquer operação que envolve um tipo de contrato de mensagem e que não siga um dos padrões de válido.</span><span class="sxs-lookup"><span data-stu-id="7201b-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="7201b-130">Obviamente, as operações que envolvem tipos de contrato de mensagem não estão sujeitos essas restrições.</span><span class="sxs-lookup"><span data-stu-id="7201b-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="7201b-131">Se um tipo tem um contrato de mensagem e um contrato de dados, somente seu contrato de mensagem é considerado quando o tipo é usado em uma operação.</span><span class="sxs-lookup"><span data-stu-id="7201b-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="7201b-132">Definindo contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="7201b-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="7201b-133">Para definir um contrato de mensagem para um tipo (ou seja, para definir o mapeamento entre o tipo e um envelope SOAP), aplique o <xref:System.ServiceModel.MessageContractAttribute> para o tipo.</span><span class="sxs-lookup"><span data-stu-id="7201b-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="7201b-134">Em seguida, aplique a <xref:System.ServiceModel.MessageHeaderAttribute> aos membros do tipo que você deseja transformar em cabeçalhos SOAP e aplicar o <xref:System.ServiceModel.MessageBodyMemberAttribute> aos membros você deseja transformar em partes do corpo da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="7201b-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="7201b-135">O código a seguir fornece um exemplo do uso de um contrato de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-135">The following code provides an example of using a message contract.</span></span>  
  
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
  
 <span data-ttu-id="7201b-136">Ao usar esse tipo como um parâmetro de operação, é gerado o envelope SOAP a seguir:</span><span class="sxs-lookup"><span data-stu-id="7201b-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
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
  
 <span data-ttu-id="7201b-137">Observe que `operation` e `transactionDate` aparecem como cabeçalhos SOAP e o corpo SOAP consiste em um elemento wrapper `BankingTransaction` contendo `sourceAccount`,`targetAccount`, e `amount`.</span><span class="sxs-lookup"><span data-stu-id="7201b-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="7201b-138">Você pode aplicar o <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> para todos os campos, propriedades e eventos, independentemente de estarem público, privado, protegido ou interno.</span><span class="sxs-lookup"><span data-stu-id="7201b-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="7201b-139">O <xref:System.ServiceModel.MessageContractAttribute> permite que você especifique os atributos WrapperName e WrapperNamespace que controlam o nome do elemento wrapper no corpo da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="7201b-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="7201b-140">Por padrão o nome do contrato de mensagem de tipo é usado para o wrapper e o namespace no qual o contrato de mensagem é definido `HYPERLINK "http://tempuri.org/" http://tempuri.org/` é usado como o namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="7201b-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined  `HYPERLINK "http://tempuri.org/" http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7201b-141"><xref:System.Runtime.Serialization.KnownTypeAttribute>atributos são ignorados em contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="7201b-142">Se um <xref:System.Runtime.Serialization.KnownTypeAttribute> é necessário, coloque-o sobre a operação que está usando o contrato de mensagem em questão.</span><span class="sxs-lookup"><span data-stu-id="7201b-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="7201b-143">Controle de cabeçalho e nomes de partes de corpo e Namespaces</span><span class="sxs-lookup"><span data-stu-id="7201b-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="7201b-144">Na representação de um contrato de mensagem SOAP, cada parte de cabeçalho e corpo mapeia para um elemento XML que tem um nome e um namespace.</span><span class="sxs-lookup"><span data-stu-id="7201b-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="7201b-145">Por padrão, o namespace é o mesmo que o namespace do contrato de serviço que está participando de mensagem e o nome é determinado pelo nome de membro para o qual o <xref:System.ServiceModel.MessageHeaderAttribute> ou <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos são aplicados.</span><span class="sxs-lookup"><span data-stu-id="7201b-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="7201b-146">Você pode alterar esses padrões manipulando o <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (na classe pai do <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos).</span><span class="sxs-lookup"><span data-stu-id="7201b-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="7201b-147">Considere a classe no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="7201b-148">Neste exemplo, o `IsAudited` cabeçalho está no namespace especificado no código e a parte do corpo que representa o `theData` membro é representado por um elemento XML com o nome `transactionData`.</span><span class="sxs-lookup"><span data-stu-id="7201b-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="7201b-149">O exemplo a seguir mostra o XML gerado para este contrato de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-149">The following shows the XML generated for this message contract.</span></span>  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="7201b-150">Controlar se as partes de corpo SOAP são quebradas</span><span class="sxs-lookup"><span data-stu-id="7201b-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="7201b-151">Por padrão, as partes de corpo SOAP são serializadas dentro de um elemento encapsulado.</span><span class="sxs-lookup"><span data-stu-id="7201b-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="7201b-152">Por exemplo, o código a seguir mostra o `HelloGreetingMessage` elemento wrapper gerado do nome do <xref:System.ServiceModel.MessageContractAttribute> tipo no contrato de mensagem para o `HelloGreetingMessage` mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
 [!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
 [!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="7201b-153">Para suprimir o elemento wrapper, defina o <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="7201b-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="7201b-154">Para controlar o nome e o namespace do elemento wrapper, use o <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> e <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="7201b-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7201b-155">Ter mais de uma parte de corpo de mensagem em mensagens que não são encapsuladas não é compatível com o WS-I Basic perfil 1.1 e não é recomendado durante a criação de novos contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="7201b-156">No entanto, é necessário ter mais de uma parte do corpo da mensagem não encapsulada em determinados cenários específicos de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="7201b-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="7201b-157">Se você pretende transmitir mais de uma parte dos dados no corpo da mensagem, é recomendável usar o modo padrão (quebrada).</span><span class="sxs-lookup"><span data-stu-id="7201b-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="7201b-158">Ter mais de um cabeçalho de mensagem em mensagens sem é totalmente aceitável.</span><span class="sxs-lookup"><span data-stu-id="7201b-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="7201b-159">Usando tipos personalizados em contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="7201b-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="7201b-160">Cada cabeçalho de mensagem individual e parte do corpo da mensagem é serializado (transformado em XML) usando o mecanismo de serialização escolhidas para o contrato de serviço em que a mensagem é usada.</span><span class="sxs-lookup"><span data-stu-id="7201b-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="7201b-161">O mecanismo de serialização padrão, o `XmlFormatter`, pode lidar com qualquer tipo que tem um contrato de dados, ou explicitamente (fazendo com que o <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) ou implicitamente (por ser um tipo primitivo, tendo o <xref:System.SerializableAttribute?displayProperty=nameWithType>, e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="7201b-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7201b-162">[Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7201b-162"> [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="7201b-163">No exemplo anterior, o `Operation` e `BankingTransactionData` tipos devem ter um contrato de dados, e `transactionDate` pode ser serializado porque <xref:System.DateTime> é um primitivo (e portanto, tem um contrato de dados implícitos).</span><span class="sxs-lookup"><span data-stu-id="7201b-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="7201b-164">No entanto, é possível alternar para um mecanismo de serialização diferentes, o `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="7201b-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="7201b-165">Se você fizer existe essa chave, você deve garantir que todos os tipos usados para cabeçalhos de mensagem e partes de corpo são serializável usando o `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="7201b-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="7201b-166">Usando matrizes dentro de contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="7201b-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="7201b-167">Você pode usar matrizes de elementos em contratos de mensagem de duas maneiras de repetição.</span><span class="sxs-lookup"><span data-stu-id="7201b-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="7201b-168">A primeira é usar um <xref:System.ServiceModel.MessageHeaderAttribute> ou um <xref:System.ServiceModel.MessageBodyMemberAttribute> diretamente na matriz.</span><span class="sxs-lookup"><span data-stu-id="7201b-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="7201b-169">Nesse caso, a matriz inteira é serializada como um elemento (ou seja, um cabeçalho ou uma parte de corpo) com vários elementos filho.</span><span class="sxs-lookup"><span data-stu-id="7201b-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="7201b-170">Considere a classe no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="7201b-171">Isso resulta em cabeçalhos SOAP é semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="7201b-171">This results in SOAP headers is similar to the following.</span></span>  
  
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
  
 <span data-ttu-id="7201b-172">Uma alternativa para isso é usar o <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7201b-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="7201b-173">Nesse caso, cada elemento da matriz é serializado de forma independente e para cada elemento de matriz tem um cabeçalho, semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="7201b-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="7201b-174">O nome padrão para as entradas da matriz é o nome do membro para o qual o <xref:System.ServiceModel.MessageHeaderArrayAttribute> atributos é aplicada.</span><span class="sxs-lookup"><span data-stu-id="7201b-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="7201b-175">O <xref:System.ServiceModel.MessageHeaderArrayAttribute> atributo herda o <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7201b-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="7201b-176">Ele tem o mesmo conjunto de recursos, como os atributos de não-matriz, por exemplo, é possível definir a ordem, o nome e o namespace para uma matriz de cabeçalhos da mesma forma, que você pode configurá-lo para um único cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="7201b-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="7201b-177">Quando você usa o `Order` propriedade em uma matriz, ela se aplica a toda a matriz.</span><span class="sxs-lookup"><span data-stu-id="7201b-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="7201b-178">Você pode aplicar o <xref:System.ServiceModel.MessageHeaderArrayAttribute> somente a matrizes, coleções não.</span><span class="sxs-lookup"><span data-stu-id="7201b-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="7201b-179">Usando matrizes de bytes em contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="7201b-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="7201b-180">Matrizes de bytes, quando usado com os atributos de matriz não (<xref:System.ServiceModel.MessageBodyMemberAttribute> e <xref:System.ServiceModel.MessageHeaderAttribute>), não são tratadas como matrizes, mas como um tipo primitivo especial representados como dados codificados na Base64 no XML resultante.</span><span class="sxs-lookup"><span data-stu-id="7201b-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="7201b-181">Quando você usa matrizes de bytes com o atributo de matriz <xref:System.ServiceModel.MessageHeaderArrayAttribute>, os resultados dependem do serializador em uso.</span><span class="sxs-lookup"><span data-stu-id="7201b-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="7201b-182">Com o serializador padrão, a matriz é representada como uma entrada individual para cada byte.</span><span class="sxs-lookup"><span data-stu-id="7201b-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="7201b-183">No entanto, quando o `XmlSerializer` for selecionada, (usando o <xref:System.ServiceModel.XmlSerializerFormatAttribute> no contrato de serviço), matrizes de bytes são tratadas como dados de Base64 independentemente se os atributos de matriz ou matriz não são usados.</span><span class="sxs-lookup"><span data-stu-id="7201b-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="7201b-184">Assinar e criptografar as partes da mensagem</span><span class="sxs-lookup"><span data-stu-id="7201b-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="7201b-185">Um contrato de mensagem pode indicar se os cabeçalhos de e/ou o corpo da mensagem deve ser assinado digitalmente e criptografado.</span><span class="sxs-lookup"><span data-stu-id="7201b-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="7201b-186">Isso é feito definindo o <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> propriedade o <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute> atributos.</span><span class="sxs-lookup"><span data-stu-id="7201b-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="7201b-187">A propriedade é uma enumeração do <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> de tipo e pode ser definido como <xref:System.Net.Security.ProtectionLevel.None> (sem criptografia ou assinatura), <xref:System.Net.Security.ProtectionLevel.Sign> (somente assinatura digital), ou <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (criptografia e uma assinatura digital).</span><span class="sxs-lookup"><span data-stu-id="7201b-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="7201b-188">O padrão é <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="7201b-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="7201b-189">Esses recursos de segurança trabalhar, você deve configurar adequadamente a associação e os comportamentos.</span><span class="sxs-lookup"><span data-stu-id="7201b-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="7201b-190">Se você usar esses recursos de segurança sem a configuração apropriada (por exemplo, a tentativa de assinar uma mensagem sem fornecer suas credenciais), uma exceção é lançada em tempo de validação.</span><span class="sxs-lookup"><span data-stu-id="7201b-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="7201b-191">Para cabeçalhos de mensagem, o nível de proteção é determinado individualmente para cada cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="7201b-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="7201b-192">Para partes de corpo de mensagem, o nível de proteção pode ser pensado como "nível mínimo de proteção".</span><span class="sxs-lookup"><span data-stu-id="7201b-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="7201b-193">O corpo tem o nível de proteção apenas um, independentemente do número de partes de corpo.</span><span class="sxs-lookup"><span data-stu-id="7201b-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="7201b-194">O nível de proteção do corpo é determinado pelo maior <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> configuração de propriedade de todas as partes de corpo.</span><span class="sxs-lookup"><span data-stu-id="7201b-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="7201b-195">No entanto, você deve definir o nível de proteção de cada parte do corpo para a proteção mínimo real nível necessária.</span><span class="sxs-lookup"><span data-stu-id="7201b-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="7201b-196">Considere a classe no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-196">Consider the class in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="7201b-197">Neste exemplo, o `recordID` cabeçalho não estiver protegido, `patientName` é `signed`, e `SSN` é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="7201b-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="7201b-198">Parte do corpo de pelo menos um, `medicalHistory`, tem <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> aplicado, e, portanto, o corpo da mensagem inteira é criptografado e assinado, embora os comentários e partes de corpo de diagnóstico especificam níveis inferiores de proteção.</span><span class="sxs-lookup"><span data-stu-id="7201b-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="7201b-199">Ação SOAP</span><span class="sxs-lookup"><span data-stu-id="7201b-199">SOAP Action</span></span>  
 <span data-ttu-id="7201b-200">SOAP e padrões relacionados de serviços Web definem uma propriedade chamada `Action` que podem estar presentes para cada mensagem SOAP enviada.</span><span class="sxs-lookup"><span data-stu-id="7201b-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="7201b-201">A operação <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> propriedades controlam o valor dessa propriedade.</span><span class="sxs-lookup"><span data-stu-id="7201b-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="7201b-202">Atributos de cabeçalho SOAP</span><span class="sxs-lookup"><span data-stu-id="7201b-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="7201b-203">O padrão SOAP define os seguintes atributos que podem existir em um cabeçalho de:</span><span class="sxs-lookup"><span data-stu-id="7201b-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
-   <span data-ttu-id="7201b-204">`Actor/Role`(`Actor` em SOAP 1.1, `Role` em SOAP 1.2)</span><span class="sxs-lookup"><span data-stu-id="7201b-204">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 <span data-ttu-id="7201b-205">O `Actor` ou `Role` atributo especifica o identificador de URI (Uniform Resource) do nó para o qual um determinado cabeçalho é pretendido.</span><span class="sxs-lookup"><span data-stu-id="7201b-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="7201b-206">O `MustUnderstand` atributo especifica se o nó de processar o cabeçalho deve entender.</span><span class="sxs-lookup"><span data-stu-id="7201b-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="7201b-207">O `Relay` atributo especifica se o cabeçalho deve ser retransmitidas para nós de downstream.</span><span class="sxs-lookup"><span data-stu-id="7201b-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7201b-208">não executa qualquer processamento desses atributos em mensagens de entrada, exceto para o `MustUnderstand` atributo, conforme especificado na seção "Controle de versão de contrato de mensagem", mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="7201b-208"> does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="7201b-209">No entanto, ele permite que você ler e gravar esses atributos conforme necessário, como a descrição a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="7201b-210">Ao enviar uma mensagem, esses atributos não são emitidos por padrão.</span><span class="sxs-lookup"><span data-stu-id="7201b-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="7201b-211">Você pode alterar isso de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="7201b-211">You can change this in two ways.</span></span> <span data-ttu-id="7201b-212">Primeiro, você pode estaticamente definir os atributos para qualquer valor desejado, alterando o <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, e <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> propriedades, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="7201b-213">(Observe que não há nenhum `Role` propriedade; a configuração a <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> propriedade emite o `Role` atributo se você estiver usando SOAP 1.2).</span><span class="sxs-lookup"><span data-stu-id="7201b-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="7201b-214">A segunda maneira de controlar esses atributos dinamicamente, é por meio de código.</span><span class="sxs-lookup"><span data-stu-id="7201b-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="7201b-215">Você pode obter isso ao encapsular o tipo desejado de cabeçalho no <xref:System.ServiceModel.MessageHeader%601> tipo (cuidado para não confunda esse tipo com a versão não genérica) e usando o tipo junto com o <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7201b-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="7201b-216">Em seguida, você pode usar propriedades no <xref:System.ServiceModel.MessageHeader%601> para definir os atributos SOAP, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="7201b-217">Se você usar dinâmico e os mecanismos de controle estático, as configurações estáticas são usadas como padrão, mas podem ser substituídas posteriormente usando o mecanismo dinâmico, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="7201b-218">Criando cabeçalhos repetidos com controle de atributo dinâmico é permitido, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="7201b-219">No lado de recepção, ler esses atributos SOAP só pode ser feito se o <xref:System.ServiceModel.MessageHeader%601> classe é usada para o cabeçalho no tipo.</span><span class="sxs-lookup"><span data-stu-id="7201b-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="7201b-220">Examine o `Actor`, `Relay`, ou `MustUnderstand` propriedades de um cabeçalho do <xref:System.ServiceModel.MessageHeader%601> tipo para descobrir as configurações de atributo na mensagem recebida.</span><span class="sxs-lookup"><span data-stu-id="7201b-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="7201b-221">Quando uma mensagem é recebida e, em seguida, enviada de volta, as configurações de atributo SOAP apenas ir ida e volta para cabeçalhos do <xref:System.ServiceModel.MessageHeader%601> tipo.</span><span class="sxs-lookup"><span data-stu-id="7201b-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="7201b-222">Ordem das partes de corpo SOAP</span><span class="sxs-lookup"><span data-stu-id="7201b-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="7201b-223">Em algumas circunstâncias, talvez seja necessário controlar a ordem das partes de corpo.</span><span class="sxs-lookup"><span data-stu-id="7201b-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="7201b-224">A ordem dos elementos do corpo é alfabética por padrão, mas pode ser controlada pelo <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7201b-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7201b-225">Essa propriedade tem a mesma semântica de <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> propriedade, exceto o comportamento em cenários de herança (em contratos de mensagem, membros não são classificados antes dos membros de corpo de tipo derivado de corpo de tipo base).</span><span class="sxs-lookup"><span data-stu-id="7201b-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7201b-226">[Ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="7201b-226"> [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="7201b-227">No exemplo a seguir, `amount` normalmente seriam primeiro porque ele é o primeiro em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="7201b-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="7201b-228">No entanto, o <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> propriedade coloca na terceira posição.</span><span class="sxs-lookup"><span data-stu-id="7201b-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
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
  
## <a name="message-contract-versioning"></a><span data-ttu-id="7201b-229">Controle de versão de contrato de mensagem</span><span class="sxs-lookup"><span data-stu-id="7201b-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="7201b-230">Ocasionalmente, talvez seja necessário alterar contratos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="7201b-231">Por exemplo, uma nova versão do seu aplicativo pode adicionar um cabeçalho extra a uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="7201b-232">Em seguida, ao enviar da nova versão para o antigo, o sistema deve lidar com um cabeçalho extra, bem como um cabeçalho ausente ao ir na outra direção.</span><span class="sxs-lookup"><span data-stu-id="7201b-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="7201b-233">As seguintes regras se aplicam a cabeçalhos de controle de versão:</span><span class="sxs-lookup"><span data-stu-id="7201b-233">The following rules apply for versioning headers:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7201b-234">objeto não aos cabeçalhos ausentes — os membros correspondentes são deixados em seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="7201b-234"> does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7201b-235">também ignora inesperados cabeçalhos adicionais.</span><span class="sxs-lookup"><span data-stu-id="7201b-235"> also ignores unexpected extra headers.</span></span> <span data-ttu-id="7201b-236">A única exceção a essa regra é se o cabeçalho extra tem um `MustUnderstand` atributo definido como `true` na mensagem SOAP de entrada — nesse caso, uma exceção será lançada como um cabeçalho que deve ser compreendido não pode ser processado.</span><span class="sxs-lookup"><span data-stu-id="7201b-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="7201b-237">Corpos de tem regras semelhantes de controle de versão de mensagem — partes de corpo de mensagem ausente e adicionais são ignorados.</span><span class="sxs-lookup"><span data-stu-id="7201b-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="7201b-238">Considerações de herança</span><span class="sxs-lookup"><span data-stu-id="7201b-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="7201b-239">Um tipo de contrato de mensagem pode herdar de outro tipo, como o tipo base também tem um contrato de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="7201b-240">Ao criar ou acessar uma mensagem usando um tipo de contrato de mensagem que herda de outros tipos de contrato de mensagem, as seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="7201b-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
-   <span data-ttu-id="7201b-241">Todos os cabeçalhos de mensagem na hierarquia de herança são coletados juntos para formar o conjunto completo de cabeçalhos da mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
-   <span data-ttu-id="7201b-242">Todas as partes de corpo de mensagem na hierarquia de herança são coletadas juntos para formar o corpo da mensagem completa.</span><span class="sxs-lookup"><span data-stu-id="7201b-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="7201b-243">As partes de corpo são ordenadas de acordo com as regras de ordenação comuns (por <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> propriedade e, em seguida, em ordem alfabética), nenhuma relevância para seu local na hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="7201b-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="7201b-244">Usando a herança de contrato de mensagem em que as partes de corpo de mensagem ocorrerem em vários níveis de árvore de herança é altamente desaconselhável.</span><span class="sxs-lookup"><span data-stu-id="7201b-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="7201b-245">Se uma classe base e uma classe derivada definem um cabeçalho ou uma parte de corpo com o mesmo nome, o membro da classe base mais é usado para armazenar o valor da parte cabeçalho ou no corpo.</span><span class="sxs-lookup"><span data-stu-id="7201b-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="7201b-246">Considere as classes no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-246">Consider the classes in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="7201b-247">O `PatientRecord` classe descreve uma mensagem com um cabeçalho chamado `ID`.</span><span class="sxs-lookup"><span data-stu-id="7201b-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="7201b-248">O cabeçalho corresponde do `personID` e não o `patientID` membro, porque o membro de mais de base é escolhido.</span><span class="sxs-lookup"><span data-stu-id="7201b-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="7201b-249">Portanto, o `patientID` campo nesse caso é inútil.</span><span class="sxs-lookup"><span data-stu-id="7201b-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="7201b-250">O corpo da mensagem contém o `diagnosis` elemento seguido de `patientName` elemento, porque é a ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="7201b-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="7201b-251">Observe que o exemplo mostra um padrão que é altamente desaconselhável: a base e os contratos de mensagem derivados tem partes de corpo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="7201b-252">Considerações de WSDL</span><span class="sxs-lookup"><span data-stu-id="7201b-252">WSDL Considerations</span></span>  
 <span data-ttu-id="7201b-253">Quando um serviço que usa os contratos de mensagem para gerar um contrato de WSDL Web Services Description Language (), é importante lembrar que nem todos os recursos de contrato de mensagem são refletidos no WSDL resultante.</span><span class="sxs-lookup"><span data-stu-id="7201b-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="7201b-254">Considere os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="7201b-254">Consider the following points:</span></span>  
  
-   <span data-ttu-id="7201b-255">WSDL não pode expressar o conceito de uma matriz de cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="7201b-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="7201b-256">Ao criar as mensagens com uma matriz de cabeçalhos usando o <xref:System.ServiceModel.MessageHeaderArrayAttribute>, o WSDL resultante reflete apenas um cabeçalho, em vez de matriz.</span><span class="sxs-lookup"><span data-stu-id="7201b-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
-   <span data-ttu-id="7201b-257">O documento WSDL resultante talvez não reflita algumas informações de nível de proteção.</span><span class="sxs-lookup"><span data-stu-id="7201b-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
-   <span data-ttu-id="7201b-258">O tipo de mensagem gerado no WSDL tem o mesmo nome que o nome da classe do tipo de contrato de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7201b-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
-   <span data-ttu-id="7201b-259">Quando usar a mesma mensagem de contrato em várias operações, vários tipos de mensagem são gerados no documento WSDL.</span><span class="sxs-lookup"><span data-stu-id="7201b-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="7201b-260">Os nomes são feitos exclusivos, adicionando os números "2", "3" e assim por diante, para usos subsequentes.</span><span class="sxs-lookup"><span data-stu-id="7201b-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="7201b-261">Ao importar novamente o WSDL, vários tipos de contrato de mensagem são criados e são idênticos, exceto seus nomes.</span><span class="sxs-lookup"><span data-stu-id="7201b-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="7201b-262">Considerações de codificação de SOAP</span><span class="sxs-lookup"><span data-stu-id="7201b-262">SOAP Encoding Considerations</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7201b-263">permite que você use o SOAP herdado codificação de estilo de XML, no entanto, seu uso não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="7201b-263"> allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="7201b-264">Ao usar esse estilo (definindo o `Use` propriedade `Encoded` no <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> aplicados ao contrato de serviço), as seguintes considerações adicionais se aplicam:</span><span class="sxs-lookup"><span data-stu-id="7201b-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
-   <span data-ttu-id="7201b-265">Não há suporte para os cabeçalhos de mensagem; Isso significa que o atributo <xref:System.ServiceModel.MessageHeaderAttribute> e o atributo de matriz <xref:System.ServiceModel.MessageHeaderArrayAttribute> são incompatíveis com codificação SOAP.</span><span class="sxs-lookup"><span data-stu-id="7201b-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
-   <span data-ttu-id="7201b-266">Se o contrato de mensagem não está quebrado, ou seja, se a propriedade <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> é definido como `false`, o contrato de mensagem pode ter parte de apenas um corpo.</span><span class="sxs-lookup"><span data-stu-id="7201b-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
-   <span data-ttu-id="7201b-267">O nome do elemento wrapper para o contrato de mensagem de solicitação deve corresponder ao nome de operação.</span><span class="sxs-lookup"><span data-stu-id="7201b-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="7201b-268">Use o `WrapperName` o contrato de mensagem para essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="7201b-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="7201b-269">O nome do elemento wrapper para o contrato de mensagem de resposta deve ser igual ao nome da operação de sufixo 'Resposta'.</span><span class="sxs-lookup"><span data-stu-id="7201b-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="7201b-270">Use o <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> o contrato de mensagem para essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="7201b-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="7201b-271">Codificação SOAP preserva as referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="7201b-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="7201b-272">Por exemplo, considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7201b-272">For example, consider the following code.</span></span>  
  
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
  
 <span data-ttu-id="7201b-273">Depois de serializar a mensagem usando a codificação de SOAP, `changedFrom` e `changedTo` não contêm suas próprias cópias de `p`, mas em vez disso, aponte para a cópia dentro a `changedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="7201b-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="7201b-274">Considerações sobre desempenho</span><span class="sxs-lookup"><span data-stu-id="7201b-274">Performance Considerations</span></span>  
 <span data-ttu-id="7201b-275">Cada cabeçalho de mensagem e a parte do corpo da mensagem é serializado independentemente de outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="7201b-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="7201b-276">Portanto, os mesmos namespaces pode ser declarados novamente para cada cabeçalho e a parte do corpo.</span><span class="sxs-lookup"><span data-stu-id="7201b-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="7201b-277">Para melhorar o desempenho, especialmente em termos de tamanho da mensagem na conexão, Consolide vários cabeçalhos e partes de corpo em uma única parte de cabeçalho ou no corpo.</span><span class="sxs-lookup"><span data-stu-id="7201b-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="7201b-278">Por exemplo, em vez do código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7201b-278">For example, instead of the following code:</span></span>  
  
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
  
 <span data-ttu-id="7201b-279">Use este código.</span><span class="sxs-lookup"><span data-stu-id="7201b-279">Use this code.</span></span>  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="7201b-280">Baseado em evento assíncrono e contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="7201b-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="7201b-281">As diretrizes de design do modelo assíncrono baseado em eventos declaram que, se mais de um valor for retornado, um valor será retornado como a propriedade `Result` e os outros serão retornados como propriedades no objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="7201b-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="7201b-282">Um resultado é que, se um cliente importar metadados usando as opções de comando assíncrono com base em eventos, e a operação retornar mais de um valor, o objeto padrão <xref:System.EventArgs> retornará um valor como a propriedade `Result` e os restantes serão propriedades do objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="7201b-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="7201b-283">Se você desejar receber o objeto de mensagem como a propriedade `Result` e ter valores retornados como propriedades nesse objeto, use a opção de comando `/messageContract`.</span><span class="sxs-lookup"><span data-stu-id="7201b-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="7201b-284">Isso gera uma assinatura que retorna a mensagem de resposta como a propriedade `Result` no objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="7201b-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="7201b-285">Todos os valores de retorno internos são propriedades do objeto da mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="7201b-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7201b-286">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7201b-286">See Also</span></span>  
 [<span data-ttu-id="7201b-287">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="7201b-287">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="7201b-288">[Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md) (Serviços de design e implantação)</span><span class="sxs-lookup"><span data-stu-id="7201b-288">[Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md)</span></span>
