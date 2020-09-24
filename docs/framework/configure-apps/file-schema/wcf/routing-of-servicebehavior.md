---
title: <routing> de <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: cd53b720bad5752189f1c30d9e4acd3a66830396
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150876"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="f048f-102">\<routing> de \<serviceBehavior></span><span class="sxs-lookup"><span data-stu-id="f048f-102">\<routing> of \<serviceBehavior></span></span>

<span data-ttu-id="f048f-103">Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="f048f-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a><span data-ttu-id="f048f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f048f-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f048f-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f048f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f048f-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f048f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f048f-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f048f-107">Attributes</span></span>  
  
|<span data-ttu-id="f048f-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="f048f-108">Attribute</span></span>|<span data-ttu-id="f048f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f048f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f048f-110">filterTable</span><span class="sxs-lookup"><span data-stu-id="f048f-110">filterTable</span></span>|<span data-ttu-id="f048f-111">Uma cadeia de caracteres que especifica o nome da tabela de roteamento que contém filtros a serem avaliados pelo serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="f048f-111">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="f048f-112">Esse valor deve corresponder ao `name` atributo de um [\<filterTable>](filtertable.md) elemento na [\<filterTables>](filtertables.md) seção.</span><span class="sxs-lookup"><span data-stu-id="f048f-112">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="f048f-113">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="f048f-113">routeOnHeaderOnly</span></span>|<span data-ttu-id="f048f-114">Um valor booliano que especifica se o filtro examinará o corpo da mensagem e o cabeçalho, ou apenas o cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="f048f-114">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="f048f-115">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="f048f-115">The default is `true`.</span></span>|  
|<span data-ttu-id="f048f-116">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="f048f-116">soapProcessingEnabled</span></span>|<span data-ttu-id="f048f-117">Um valor booliano que especifica se o processamento SOAP deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="f048f-117">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f048f-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f048f-118">Child Elements</span></span>  

 <span data-ttu-id="f048f-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f048f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f048f-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f048f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f048f-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f048f-121">Element</span></span>|<span data-ttu-id="f048f-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f048f-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f048f-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="f048f-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f048f-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f048f-124">Remarks</span></span>  

 <span data-ttu-id="f048f-125">Quando adicionado à configuração de comportamento do serviço, esse elemento de configuração habilita o roteamento para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f048f-125">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="f048f-126">Você pode especificar a tabela de roteamento real a ser usada pelo serviço neste elemento.</span><span class="sxs-lookup"><span data-stu-id="f048f-126">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="f048f-127">Usando esta seção de configuração, você pode alterar suas configurações de roteamento imediatamente quando o padrão de implantação for alterado.</span><span class="sxs-lookup"><span data-stu-id="f048f-127">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="f048f-128">Em tempo de execução, você pode registrar sua própria extensão de roteamento com novas configurações de roteamento e o serviço de roteamento começará a usar as informações de configuração atualizadas para novas mensagens e sessões, deixando, ao mesmo tempo, mensagens/sessões em andamento usando as regras que estavam em vigor quando elas foram iniciadas.</span><span class="sxs-lookup"><span data-stu-id="f048f-128">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="f048f-129">Isso lhe dá a capacidade de fazer a reconfiguração com segurança de sessão e sem reciclagem do serviço de roteamento durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f048f-129">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
