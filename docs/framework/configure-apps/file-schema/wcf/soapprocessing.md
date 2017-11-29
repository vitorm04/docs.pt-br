---
title: '&lt;soapProcessing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e53225399e3acba275d2d95533c4baad20386a4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsoapprocessinggt"></a><span data-ttu-id="47d76-102">&lt;soapProcessing&gt;</span><span class="sxs-lookup"><span data-stu-id="47d76-102">&lt;soapProcessing&gt;</span></span>

<span data-ttu-id="47d76-103">Define o comportamento de ponto de extremidade de cliente usado para realizar marshaling de mensagens entre tipos de associação diferentes e versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="47d76-103">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

<span data-ttu-id="47d76-104">**\<sistema. ServiceModel >** </span><span class="sxs-lookup"><span data-stu-id="47d76-104">**\<system.ServiceModel>** </span></span>  
<span data-ttu-id="47d76-105">&nbsp;&nbsp;**\<comportamentos >** </span><span class="sxs-lookup"><span data-stu-id="47d76-105">&nbsp;&nbsp;**\<behaviors>** </span></span>  
<span data-ttu-id="47d76-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >** </span><span class="sxs-lookup"><span data-stu-id="47d76-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors>** </span></span>  
<span data-ttu-id="47d76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comportamento >** </span><span class="sxs-lookup"><span data-stu-id="47d76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>** </span></span>  
<span data-ttu-id="47d76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**</span><span class="sxs-lookup"><span data-stu-id="47d76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="47d76-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47d76-109">Syntax</span></span>

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47d76-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="47d76-110">Attributes and elements</span></span>

<span data-ttu-id="47d76-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="47d76-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="47d76-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="47d76-112">Attributes</span></span>

|                   | <span data-ttu-id="47d76-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="47d76-113">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="47d76-114">Um valor booleano que especifica se as mensagens devem ser empacotadas entre versões de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="47d76-114">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="47d76-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="47d76-115">Child elements</span></span>

<span data-ttu-id="47d76-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="47d76-116">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="47d76-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="47d76-117">Parent elements</span></span>

|     | <span data-ttu-id="47d76-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="47d76-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="47d76-119">**\<comportamento >**</span><span class="sxs-lookup"><span data-stu-id="47d76-119">**\<behavior>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | <span data-ttu-id="47d76-120">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="47d76-120">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="47d76-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="47d76-121">Remarks</span></span>

<span data-ttu-id="47d76-122">Processamento de SOAP é o processo em que as mensagens são convertidas entre as versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="47d76-122">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="47d76-123">O [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviço de roteamento pode converter mensagens de um protocolo para outro.</span><span class="sxs-lookup"><span data-stu-id="47d76-123">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="47d76-124">Se as versões de mensagem de entrada e saída são diferentes, é criada uma nova mensagem da versão correta.</span><span class="sxs-lookup"><span data-stu-id="47d76-124">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="47d76-125">Processamento de mensagens de um <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion` para outro é feito criando um novo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] mensagem que contém a parte do corpo e os cabeçalhos relevantes de entrada [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] mensagem.</span><span class="sxs-lookup"><span data-stu-id="47d76-125">Processing messages from one <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion`  to another is accomplished by constructing a new [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message that contains the body part and relevant headers from the incoming [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message.</span></span> <span data-ttu-id="47d76-126">Cabeçalhos específicos de endereçamento, ou que são entendidas no nível do roteador, não são usados durante a construção da nova mensagem WCF porque esses cabeçalhos são de uma versão diferente (no caso de cabeçalhos de endereçamento) ou tem sido processados como parte da comunicação entre o cliente e o roteador.</span><span class="sxs-lookup"><span data-stu-id="47d76-126">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="47d76-127">Se um cabeçalho é colocado na mensagem de saída é determinado pelo ou não foi marcado como compreender quando transmitidas por meio da camada de canal de entrada.</span><span class="sxs-lookup"><span data-stu-id="47d76-127">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="47d76-128">Cabeçalhos que não são compreendidos (como cabeçalhos personalizados) não são removidos e passam para o serviço de roteamento por que está sendo copiado para a mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="47d76-128">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="47d76-129">O corpo da mensagem é copiado para a mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="47d76-129">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="47d76-130">A mensagem é enviada, em seguida, o canal de saída, no momento em que todos os cabeçalhos e outros dados de envelope específicos para essa comunicação/transporte de protocolo será criado e adicionado.</span><span class="sxs-lookup"><span data-stu-id="47d76-130">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="47d76-131">Essas etapas de processamento ocorrem quando o comportamento de processamento de SOAP é especificado.</span><span class="sxs-lookup"><span data-stu-id="47d76-131">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="47d76-132">Isso [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) comportamento é um comportamento de ponto de extremidade que é aplicado a todos os pontos de extremidade do cliente (saída) quando o serviço de roteamento é iniciado.</span><span class="sxs-lookup"><span data-stu-id="47d76-132">This [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="47d76-133">padrão, o [ \<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportamento cria e anexa um novo [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) comportamento com `processMessages` definida como `true` para cada ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="47d76-133">default, the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="47d76-134">Se você tiver um protocolo que o serviço de roteamento não entender ou deseja substituir o comportamento padrão de processamento, você pode desativar o processamento para todo o serviço de roteamento ou apenas para pontos de extremidade específicos de SOAP.</span><span class="sxs-lookup"><span data-stu-id="47d76-134">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="47d76-135">Para desativar o processamento para todo o serviço de roteamento em todos os pontos de extremidade SOAP, defina o `soapProcessing` atributo do [ \<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportamento `false`.</span><span class="sxs-lookup"><span data-stu-id="47d76-135">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="47d76-136">Para desativar o processamento de um determinado ponto de extremidade SOAP, use esse comportamento e defina seu `processMessages` atributo `false`, em seguida, anexar esse comportamento para o ponto de extremidade que você não quiser que o padrão de processamento de código para ser executado em.</span><span class="sxs-lookup"><span data-stu-id="47d76-136">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="47d76-137">Quando o [ \<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportamento configura o serviço de roteamento, ele ignorará reaplicar o comportamento de ponto de extremidade, pois já existe um.</span><span class="sxs-lookup"><span data-stu-id="47d76-137">When the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
