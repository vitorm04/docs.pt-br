---
title: <routing> de <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397726"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="0cb36-102">\<> de roteamento \<de > de serviço</span><span class="sxs-lookup"><span data-stu-id="0cb36-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="0cb36-103">Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="0cb36-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
<span data-ttu-id="0cb36-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0cb36-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0cb36-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0cb36-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0cb36-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0cb36-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="0cb36-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0cb36-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="0cb36-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0cb36-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="0cb36-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de roteamento**</span><span class="sxs-lookup"><span data-stu-id="0cb36-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb36-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cb36-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cb36-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0cb36-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0cb36-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0cb36-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cb36-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="0cb36-113">Attributes</span></span>  
  
|<span data-ttu-id="0cb36-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="0cb36-114">Attribute</span></span>|<span data-ttu-id="0cb36-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cb36-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0cb36-116">filterTable</span><span class="sxs-lookup"><span data-stu-id="0cb36-116">filterTable</span></span>|<span data-ttu-id="0cb36-117">Uma cadeia de caracteres que especifica o nome da tabela de roteamento que contém filtros a serem avaliados pelo serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="0cb36-117">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="0cb36-118">Esse valor deve corresponder ao `name` atributo de um [ \<elemento de > de FilterTable](filtertable.md) na seção de [ \<> filterTables](filtertables.md) .</span><span class="sxs-lookup"><span data-stu-id="0cb36-118">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="0cb36-119">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="0cb36-119">routeOnHeaderOnly</span></span>|<span data-ttu-id="0cb36-120">Um valor booliano que especifica se o filtro examinará o corpo da mensagem e o cabeçalho, ou apenas o cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="0cb36-120">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="0cb36-121">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="0cb36-121">The default is `true`.</span></span>|  
|<span data-ttu-id="0cb36-122">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="0cb36-122">soapProcessingEnabled</span></span>|<span data-ttu-id="0cb36-123">Um valor booliano que especifica se o processamento SOAP deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="0cb36-123">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0cb36-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0cb36-124">Child Elements</span></span>  
 <span data-ttu-id="0cb36-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0cb36-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0cb36-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0cb36-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0cb36-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="0cb36-127">Element</span></span>|<span data-ttu-id="0cb36-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cb36-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cb36-129">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="0cb36-129">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0cb36-130">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="0cb36-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cb36-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="0cb36-131">Remarks</span></span>  
 <span data-ttu-id="0cb36-132">Quando adicionado à configuração de comportamento do serviço, esse elemento de configuração habilita o roteamento para o serviço.</span><span class="sxs-lookup"><span data-stu-id="0cb36-132">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="0cb36-133">Você pode especificar a tabela de roteamento real a ser usada pelo serviço neste elemento.</span><span class="sxs-lookup"><span data-stu-id="0cb36-133">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="0cb36-134">Usando esta seção de configuração, você pode alterar suas configurações de roteamento imediatamente quando o padrão de implantação for alterado.</span><span class="sxs-lookup"><span data-stu-id="0cb36-134">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="0cb36-135">Em tempo de execução, você pode registrar sua própria extensão de roteamento com novas configurações de roteamento e o serviço de roteamento começará a usar as informações de configuração atualizadas para novas mensagens e sessões, deixando de manter mensagens/sessões em andamento usando quaisquer regras que estavam em local quando eles começaram.</span><span class="sxs-lookup"><span data-stu-id="0cb36-135">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="0cb36-136">Isso lhe dá a capacidade de fazer a reconfiguração com segurança de sessão e sem reciclagem do serviço de roteamento durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0cb36-136">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
