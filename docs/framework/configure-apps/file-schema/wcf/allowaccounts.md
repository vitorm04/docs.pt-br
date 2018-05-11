---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: bbfe0d5d531cf61c01f95d0e82ce0f894031d6f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="c5ff7-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="c5ff7-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="c5ff7-103">Contém uma coleção de elementos de configuração que especificam contas para os processos que hospedam serviços Windows Communication Foundation (WCF) de usuário e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="c5ff7-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="c5ff7-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="c5ff7-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ff7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5ff7-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5ff7-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c5ff7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c5ff7-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c5ff7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5ff7-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c5ff7-108">Attributes</span></span>  
 <span data-ttu-id="c5ff7-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c5ff7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c5ff7-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c5ff7-110">Child Elements</span></span>  
  
|<span data-ttu-id="c5ff7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="c5ff7-111">Attribute</span></span>|<span data-ttu-id="c5ff7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5ff7-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c5ff7-113">\<add></span><span class="sxs-lookup"><span data-stu-id="c5ff7-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="c5ff7-114">Adiciona uma conta de usuário para processos que hospedam [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços e recebem acesso de conexão para o serviço de compartilhamento</span><span class="sxs-lookup"><span data-stu-id="c5ff7-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5ff7-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c5ff7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c5ff7-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5ff7-116">Element</span></span>|<span data-ttu-id="c5ff7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5ff7-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5ff7-118">[\<NET. pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) ou [ \<NET. TCP >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="c5ff7-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="c5ff7-119">Especifica as configurações para o Pipe de rede ou serviços de compartilhamento de TCP.</span><span class="sxs-lookup"><span data-stu-id="c5ff7-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5ff7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5ff7-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
