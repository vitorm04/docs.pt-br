---
title: Como definir a propriedade ProtectionLevel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 4ff835f767852da586a3a35b7f4ce2edf99db283
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320907"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="a351f-102">Como definir a propriedade ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="a351f-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="a351f-103">Você pode definir o nível de proteção aplicando um atributo apropriado e configurando a propriedade.</span><span class="sxs-lookup"><span data-stu-id="a351f-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="a351f-104">Você pode definir a proteção no nível de serviço para afetar todas as partes de cada mensagem ou pode definir a proteção em níveis cada vez mais granulares, de métodos a partes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="a351f-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="a351f-105">Para obter mais informações sobre a propriedade `ProtectionLevel`, consulte [noções básicas sobre nível de proteção](understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="a351f-105">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](understanding-protection-level.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a351f-106">Você pode definir níveis de proteção somente no código, não na configuração.</span><span class="sxs-lookup"><span data-stu-id="a351f-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="a351f-107">Para assinar todas as mensagens de um serviço</span><span class="sxs-lookup"><span data-stu-id="a351f-107">To sign all messages for a service</span></span>  
  
1. <span data-ttu-id="a351f-108">Crie uma interface para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a351f-108">Create an interface for the service.</span></span>  
  
2. <span data-ttu-id="a351f-109">Aplique o atributo <xref:System.ServiceModel.ServiceContractAttribute> ao serviço e defina a propriedade <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> como <xref:System.Net.Security.ProtectionLevel.Sign>, conforme mostrado no código a seguir (o nível padrão é <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="a351f-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="a351f-110">Para assinar todas as partes da mensagem para uma operação</span><span class="sxs-lookup"><span data-stu-id="a351f-110">To sign all message parts for an operation</span></span>  
  
1. <span data-ttu-id="a351f-111">Crie uma interface para o serviço e aplique o atributo <xref:System.ServiceModel.ServiceContractAttribute> à interface.</span><span class="sxs-lookup"><span data-stu-id="a351f-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2. <span data-ttu-id="a351f-112">Adicione uma declaração de método à interface.</span><span class="sxs-lookup"><span data-stu-id="a351f-112">Add a method declaration to the interface.</span></span>  
  
3. <span data-ttu-id="a351f-113">Aplique o atributo <xref:System.ServiceModel.OperationContractAttribute> ao método e defina a propriedade <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> como <xref:System.Net.Security.ProtectionLevel.Sign>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a351f-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="a351f-114">Protegendo mensagens de falha</span><span class="sxs-lookup"><span data-stu-id="a351f-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="a351f-115">As exceções que são geradas em um serviço podem ser enviadas a um cliente como falhas de SOAP.</span><span class="sxs-lookup"><span data-stu-id="a351f-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="a351f-116">Para obter mais informações sobre como criar falhas com rigidez de tipos, consulte [especificando e tratando falhas em contratos e serviços](specifying-and-handling-faults-in-contracts-and-services.md) e [como declarar falhas em contratos de serviço](how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a351f-116">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="a351f-117">Para proteger uma mensagem de falha</span><span class="sxs-lookup"><span data-stu-id="a351f-117">To protect a fault message</span></span>  
  
1. <span data-ttu-id="a351f-118">Crie um tipo que representa a mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="a351f-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="a351f-119">O exemplo a seguir cria uma classe chamada `MathFault` com dois campos.</span><span class="sxs-lookup"><span data-stu-id="a351f-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2. <span data-ttu-id="a351f-120">Aplique o atributo <xref:System.Runtime.Serialization.DataContractAttribute> ao tipo e um atributo <xref:System.Runtime.Serialization.DataMemberAttribute> a cada campo que deve ser serializado, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a351f-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. <span data-ttu-id="a351f-121">Na interface que retornará a falha, aplique o atributo <xref:System.ServiceModel.FaultContractAttribute> ao método que retornará a falha e defina o parâmetro `detailType` como o tipo da classe de falha.</span><span class="sxs-lookup"><span data-stu-id="a351f-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4. <span data-ttu-id="a351f-122">Também no construtor, defina a propriedade <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a351f-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="a351f-123">Protegendo partes da mensagem</span><span class="sxs-lookup"><span data-stu-id="a351f-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="a351f-124">Use um contrato de mensagem para proteger partes de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="a351f-124">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="a351f-125">Para obter mais informações sobre os contratos de mensagem, consulte [usando contratos de mensagem](./feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a351f-125">For more information about message contracts, see [Using Message Contracts](./feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="a351f-126">Para proteger um corpo de mensagem</span><span class="sxs-lookup"><span data-stu-id="a351f-126">To protect a message body</span></span>  
  
1. <span data-ttu-id="a351f-127">Crie um tipo que representa a mensagem.</span><span class="sxs-lookup"><span data-stu-id="a351f-127">Create a type that represents the message.</span></span> <span data-ttu-id="a351f-128">O exemplo a seguir cria uma classe `Company` com dois campos, `CompanyName` e `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="a351f-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2. <span data-ttu-id="a351f-129">Aplique o atributo <xref:System.ServiceModel.MessageContractAttribute> à classe e defina a propriedade <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="a351f-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3. <span data-ttu-id="a351f-130">Aplique o atributo <xref:System.ServiceModel.MessageHeaderAttribute> a um campo que será expresso como um cabeçalho de mensagem e defina a propriedade `ProtectionLevel` como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="a351f-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4. <span data-ttu-id="a351f-131">Aplique o <xref:System.ServiceModel.MessageBodyMemberAttribute> a qualquer campo que será expresso como parte do corpo da mensagem e defina a propriedade `ProtectionLevel` como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a351f-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="a351f-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a351f-132">Example</span></span>  
 <span data-ttu-id="a351f-133">O exemplo a seguir define a propriedade `ProtectionLevel` de várias classes de atributo em vários locais em um serviço.</span><span class="sxs-lookup"><span data-stu-id="a351f-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a351f-134">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a351f-134">Compiling the Code</span></span>  
 <span data-ttu-id="a351f-135">O código a seguir mostra os namespaces necessários para compilar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="a351f-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="a351f-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a351f-136">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="a351f-137">Noções básicas de nível de proteção</span><span class="sxs-lookup"><span data-stu-id="a351f-137">Understanding Protection Level</span></span>](understanding-protection-level.md)
