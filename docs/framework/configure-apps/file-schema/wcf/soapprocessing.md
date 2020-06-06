---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399534"
---
# \<soapProcessing>

<span data-ttu-id="2d7f7-101">Define o comportamento de ponto de extremidade de cliente usado para realizar marshaling de mensagens entre diferentes tipos de associação e versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-101">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**
  
## <a name="syntax"></a><span data-ttu-id="2d7f7-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d7f7-102">Syntax</span></span>  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d7f7-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2d7f7-103">Attributes and elements</span></span>  
  
<span data-ttu-id="2d7f7-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d7f7-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="2d7f7-105">Attributes</span></span>  
  
|                   | <span data-ttu-id="2d7f7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d7f7-106">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="2d7f7-107">Um valor booliano que especifica se as mensagens devem ser empacotadas entre as versões de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-107">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="2d7f7-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2d7f7-108">Child elements</span></span>

<span data-ttu-id="2d7f7-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2d7f7-109">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d7f7-110">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2d7f7-110">Parent elements</span></span>

|     | <span data-ttu-id="2d7f7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d7f7-111">Description</span></span> |
| --- | ----------- |
| [**\<behavior>**](behavior-of-endpointbehaviors.md) | <span data-ttu-id="2d7f7-112">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-112">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2d7f7-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d7f7-113">Remarks</span></span>

<span data-ttu-id="2d7f7-114">O processamento de SOAP é o processo em que as mensagens são convertidas entre as versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-114">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="2d7f7-115">O serviço de roteamento do Windows Communication Foundation (WCF) pode converter mensagens de um protocolo para outro.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-115">The Windows Communication Foundation (WCF) Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="2d7f7-116">Se as versões de mensagens de entrada e saída forem diferentes, uma nova mensagem da versão correta será criada.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-116">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="2d7f7-117">O processamento de mensagens de um <xref:System.ServiceModel.Channels.MessageVersion> para outro é realizado pela construção de uma nova mensagem do WCF que contém a parte do corpo e os cabeçalhos relevantes da mensagem de entrada do WCF.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-117">Processing messages from one <xref:System.ServiceModel.Channels.MessageVersion> to another is accomplished by constructing a new WCF message that contains the body part and relevant headers from the incoming WCF message.</span></span> <span data-ttu-id="2d7f7-118">Os cabeçalhos que são específicos para endereçamento, ou que são compreendidos no nível do roteador, não são usados durante a construção da nova mensagem do WCF, pois esses cabeçalhos são de uma versão diferente (no caso de cabeçalhos de endereçamento) ou foram processados como parte da comunicação entre o cliente e o roteador.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-118">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="2d7f7-119">Se um cabeçalho é colocado na mensagem de saída é determinado por se ele foi marcado como compreendido ou não como sendo passado pela camada de canal de entrada.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-119">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="2d7f7-120">Os cabeçalhos que não são compreendidos (como cabeçalhos personalizados) não são removidos e, portanto, passam pelo serviço de roteamento ao serem copiados para a mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-120">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="2d7f7-121">O corpo da mensagem é copiado para a mensagem de saída.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-121">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="2d7f7-122">Em seguida, a mensagem envia o canal de saída, ponto em que todos os cabeçalhos e outros dados de envelope específicos ao protocolo de comunicação/transporte serão criados e adicionados.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-122">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="2d7f7-123">Essas etapas de processamento ocorrem quando o comportamento de processamento de SOAP é especificado.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-123">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="2d7f7-124">Esse [\<soapProcessingExtension>](soapprocessing.md) comportamento é um comportamento de ponto de extremidade que é aplicado a todos os pontos de extremidades de cliente (enviados) quando o serviço de roteamento é iniciado.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-124">This [\<soapProcessingExtension>](soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="2d7f7-125">padrão, o [\<routing>](routing-of-servicebehavior.md) comportamento cria e anexa um novo [\<soapProcessingExtension>](soapprocessing.md) comportamento com `processMessages` definido como `true` para cada ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-125">default, the [\<routing>](routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="2d7f7-126">Se você tiver um protocolo que o serviço de roteamento não entende ou deseja substituir o comportamento de processamento padrão, você poderá desabilitar o processamento SOAP para o serviço de roteamento inteiro ou apenas para pontos de extremidade específicos.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-126">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="2d7f7-127">Para desabilitar o processamento de SOAP para todo o serviço de roteamento em todos os pontos de extremidade, defina o `soapProcessing` atributo do [\<routing>](routing-of-servicebehavior.md) comportamento como `false` .</span><span class="sxs-lookup"><span data-stu-id="2d7f7-127">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="2d7f7-128">Para desativar o processamento de SOAP para um ponto de extremidade específico, use esse comportamento e defina seu `processMessages` atributo como `false` , em seguida, anexe esse comportamento ao ponto de extremidade no qual você não deseja que o código de processamento padrão seja executado.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-128">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="2d7f7-129">Quando o [\<routing>](routing-of-servicebehavior.md) comportamento configura o serviço de roteamento, ele ignorará a reaplicação do comportamento do ponto de extremidade desde que já exista um.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-129">When the [\<routing>](routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
