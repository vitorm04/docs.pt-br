---
title: "Serialização e transferência de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8daadec1eef20e62747cdbfcafd1fd13cfc16093
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="d7dac-102">Serialização e transferência de dados</span><span class="sxs-lookup"><span data-stu-id="d7dac-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="d7dac-103">Em um sistema conectado, o clientes e serviços dependem da troca de dados para realizar qualquer tarefa.</span><span class="sxs-lookup"><span data-stu-id="d7dac-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="d7dac-104">Como desenvolvedor de um serviço ou cliente, você também deve entender como [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] lida com dados e serialização de dados para criar aplicativos que são eficiente e fácil de manter.</span><span class="sxs-lookup"><span data-stu-id="d7dac-104">As a developer of a service or client, you must also understand how [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7dac-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d7dac-105">In This Section</span></span>  
 [<span data-ttu-id="d7dac-106">Especificando transferência de dados em contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="d7dac-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="d7dac-107">Descreve os conceitos básicos de transferência de dados nos serviços.</span><span class="sxs-lookup"><span data-stu-id="d7dac-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="d7dac-108">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="d7dac-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="d7dac-109">Descreve contratos de dados que são e como criar e usá-los.</span><span class="sxs-lookup"><span data-stu-id="d7dac-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="d7dac-110">Serializador de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="d7dac-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="d7dac-111">Descreve como realizar a serialização de dados com o <xref:System.Runtime.Serialization.DataContractSerializer> classe ou qualquer extensão do <xref:System.Runtime.Serialization.XmlObjectSerializer> classe.</span><span class="sxs-lookup"><span data-stu-id="d7dac-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="d7dac-112">Usando a classe XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="d7dac-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="d7dac-113">Descreve como e por que usar o <xref:System.Xml.Serialization.XmlSerializer> classe, uma alternativa para o <xref:System.Runtime.Serialization.DataContractSerializer> classe.</span><span class="sxs-lookup"><span data-stu-id="d7dac-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="d7dac-114">Usando contratos de mensagem</span><span class="sxs-lookup"><span data-stu-id="d7dac-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="d7dac-115">Descreve como contratos de mensagem permitem controle refinado sobre mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7dac-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="d7dac-116">Usando a classe de mensagens</span><span class="sxs-lookup"><span data-stu-id="d7dac-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="d7dac-117">Descreve como usar recursos de classe de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d7dac-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="d7dac-118">Filtragem</span><span class="sxs-lookup"><span data-stu-id="d7dac-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="d7dac-119">Descreve a filtragem, que permite que o pré-processamento de uma mensagem com base em vários critérios.</span><span class="sxs-lookup"><span data-stu-id="d7dac-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="d7dac-120">Dados grandes e streaming</span><span class="sxs-lookup"><span data-stu-id="d7dac-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="d7dac-121">Descreve como enviar um grande bloco de dados, como um arquivo binário.</span><span class="sxs-lookup"><span data-stu-id="d7dac-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="d7dac-122">Considerações sobre segurança para dados</span><span class="sxs-lookup"><span data-stu-id="d7dac-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="d7dac-123">Descreve itens deve estar atento ao programar a serialização e transferência de dados.</span><span class="sxs-lookup"><span data-stu-id="d7dac-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="d7dac-124">Visão geral da arquitetura de transferência de dados</span><span class="sxs-lookup"><span data-stu-id="d7dac-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="d7dac-125">Descreve uma exibição do design geral de transferência de dados em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7dac-125">Describes a view of the overall design of data transfer in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d7dac-126">Referência</span><span class="sxs-lookup"><span data-stu-id="d7dac-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="d7dac-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d7dac-127">Related Sections</span></span>  
 [<span data-ttu-id="d7dac-128">Estendendo codificadores e serializadores</span><span class="sxs-lookup"><span data-stu-id="d7dac-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="d7dac-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7dac-129">See Also</span></span>  
 [<span data-ttu-id="d7dac-130">Práticas recomendadas: controle de versão de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="d7dac-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [<span data-ttu-id="d7dac-131">Controle de versão de serviço</span><span class="sxs-lookup"><span data-stu-id="d7dac-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
