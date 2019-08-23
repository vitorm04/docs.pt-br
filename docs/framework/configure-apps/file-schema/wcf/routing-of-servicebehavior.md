---
title: <routing> de <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 73a610056f94efe144705968eaf97c8314c1ae0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934194"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="bfb38-102">\<> de roteamento \<de > de serviço</span><span class="sxs-lookup"><span data-stu-id="bfb38-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="bfb38-103">Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="bfb38-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="bfb38-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bfb38-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bfb38-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="bfb38-105">\<behaviors></span></span>  
<span data-ttu-id="bfb38-106">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="bfb38-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bfb38-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="bfb38-107">\<behavior></span></span>  
<span data-ttu-id="bfb38-108">\<> de roteamento</span><span class="sxs-lookup"><span data-stu-id="bfb38-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb38-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfb38-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfb38-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bfb38-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bfb38-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bfb38-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfb38-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="bfb38-112">Attributes</span></span>  
  
|<span data-ttu-id="bfb38-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="bfb38-113">Attribute</span></span>|<span data-ttu-id="bfb38-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfb38-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bfb38-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="bfb38-115">filterTable</span></span>|<span data-ttu-id="bfb38-116">Uma cadeia de caracteres que especifica o nome da tabela de roteamento que contém filtros a serem avaliados pelo serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="bfb38-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="bfb38-117">Esse valor deve corresponder ao `name` atributo de um [ \<](filtertable.md) elemento de > de FilterTable na seção de [ \<> filterTables](filtertables.md) .</span><span class="sxs-lookup"><span data-stu-id="bfb38-117">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="bfb38-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="bfb38-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="bfb38-119">Um valor booliano que especifica se o filtro examinará o corpo da mensagem e o cabeçalho, ou apenas o cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="bfb38-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="bfb38-120">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="bfb38-120">The default is `true`.</span></span>|  
|<span data-ttu-id="bfb38-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="bfb38-121">soapProcessingEnabled</span></span>|<span data-ttu-id="bfb38-122">Um valor booliano que especifica se o processamento SOAP deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="bfb38-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfb38-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bfb38-123">Child Elements</span></span>  
 <span data-ttu-id="bfb38-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bfb38-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfb38-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bfb38-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bfb38-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="bfb38-126">Element</span></span>|<span data-ttu-id="bfb38-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfb38-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfb38-128">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="bfb38-128">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bfb38-129">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="bfb38-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfb38-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfb38-130">Remarks</span></span>  
 <span data-ttu-id="bfb38-131">Quando adicionado à configuração de comportamento do serviço, esse elemento de configuração habilita o roteamento para o serviço.</span><span class="sxs-lookup"><span data-stu-id="bfb38-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="bfb38-132">Você pode especificar a tabela de roteamento real a ser usada pelo serviço neste elemento.</span><span class="sxs-lookup"><span data-stu-id="bfb38-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="bfb38-133">Usando esta seção de configuração, você pode alterar suas configurações de roteamento imediatamente quando o padrão de implantação for alterado.</span><span class="sxs-lookup"><span data-stu-id="bfb38-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="bfb38-134">Em tempo de execução, você pode registrar sua própria extensão de roteamento com novas configurações de roteamento e o serviço de roteamento começará a usar as informações de configuração atualizadas para novas mensagens e sessões, deixando de manter mensagens/sessões em andamento usando quaisquer regras que estavam em local quando eles começaram.</span><span class="sxs-lookup"><span data-stu-id="bfb38-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="bfb38-135">Isso lhe dá a capacidade de fazer a reconfiguração com segurança de sessão e sem reciclagem do serviço de roteamento durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bfb38-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
