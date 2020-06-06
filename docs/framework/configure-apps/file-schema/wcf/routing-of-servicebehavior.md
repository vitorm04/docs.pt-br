---
title: <routing> de <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397726"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="01d73-102">\<routing> de \<serviceBehavior></span><span class="sxs-lookup"><span data-stu-id="01d73-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="01d73-103">Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="01d73-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a><span data-ttu-id="01d73-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01d73-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01d73-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="01d73-105">Attributes and Elements</span></span>  
 <span data-ttu-id="01d73-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="01d73-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01d73-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="01d73-107">Attributes</span></span>  
  
|<span data-ttu-id="01d73-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="01d73-108">Attribute</span></span>|<span data-ttu-id="01d73-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="01d73-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01d73-110">filterTable</span><span class="sxs-lookup"><span data-stu-id="01d73-110">filterTable</span></span>|<span data-ttu-id="01d73-111">Uma cadeia de caracteres que especifica o nome da tabela de roteamento que contém filtros a serem avaliados pelo serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="01d73-111">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="01d73-112">Esse valor deve corresponder ao `name` atributo de um [\<filterTable>](filtertable.md) elemento na [\<filterTables>](filtertables.md) seção.</span><span class="sxs-lookup"><span data-stu-id="01d73-112">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="01d73-113">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="01d73-113">routeOnHeaderOnly</span></span>|<span data-ttu-id="01d73-114">Um valor booliano que especifica se o filtro examinará o corpo da mensagem e o cabeçalho, ou apenas o cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="01d73-114">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="01d73-115">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="01d73-115">The default is `true`.</span></span>|  
|<span data-ttu-id="01d73-116">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="01d73-116">soapProcessingEnabled</span></span>|<span data-ttu-id="01d73-117">Um valor booliano que especifica se o processamento SOAP deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="01d73-117">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01d73-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="01d73-118">Child Elements</span></span>  
 <span data-ttu-id="01d73-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="01d73-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01d73-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="01d73-120">Parent Elements</span></span>  
  
|<span data-ttu-id="01d73-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="01d73-121">Element</span></span>|<span data-ttu-id="01d73-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="01d73-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="01d73-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="01d73-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01d73-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="01d73-124">Remarks</span></span>  
 <span data-ttu-id="01d73-125">Quando adicionado à configuração de comportamento do serviço, esse elemento de configuração habilita o roteamento para o serviço.</span><span class="sxs-lookup"><span data-stu-id="01d73-125">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="01d73-126">Você pode especificar a tabela de roteamento real a ser usada pelo serviço neste elemento.</span><span class="sxs-lookup"><span data-stu-id="01d73-126">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="01d73-127">Usando esta seção de configuração, você pode alterar suas configurações de roteamento imediatamente quando o padrão de implantação for alterado.</span><span class="sxs-lookup"><span data-stu-id="01d73-127">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="01d73-128">Em tempo de execução, você pode registrar sua própria extensão de roteamento com novas configurações de roteamento e o serviço de roteamento começará a usar as informações de configuração atualizadas para novas mensagens e sessões, deixando, ao mesmo tempo, mensagens/sessões em andamento usando as regras que estavam em vigor quando elas foram iniciadas.</span><span class="sxs-lookup"><span data-stu-id="01d73-128">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="01d73-129">Isso lhe dá a capacidade de fazer a reconfiguração com segurança de sessão e sem reciclagem do serviço de roteamento durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="01d73-129">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
