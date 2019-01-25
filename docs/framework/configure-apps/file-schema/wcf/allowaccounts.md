---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c1c4630e6191dbbe02688a4e4a9db9e18b8d36d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508398"
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="57c20-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="57c20-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="57c20-103">Contém uma coleção de elementos de configuração que especificam contas para processos que hospedam serviços Windows Communication Foundation (WCF) de usuário e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="57c20-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="57c20-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="57c20-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57c20-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57c20-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57c20-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="57c20-106">Attributes and Elements</span></span>  
 <span data-ttu-id="57c20-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="57c20-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57c20-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="57c20-108">Attributes</span></span>  
 <span data-ttu-id="57c20-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="57c20-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57c20-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="57c20-110">Child Elements</span></span>  
  
|<span data-ttu-id="57c20-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="57c20-111">Attribute</span></span>|<span data-ttu-id="57c20-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="57c20-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="57c20-113">\<add></span><span class="sxs-lookup"><span data-stu-id="57c20-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="57c20-114">Adiciona uma conta de usuário para processos que hospedam serviços do WCF e recebem acesso de conexão para o serviço de compartilhamento</span><span class="sxs-lookup"><span data-stu-id="57c20-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57c20-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="57c20-115">Parent Elements</span></span>  
  
|<span data-ttu-id="57c20-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="57c20-116">Element</span></span>|<span data-ttu-id="57c20-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="57c20-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57c20-118">[\<NET. pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) ou [ \<NET. TCP >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="57c20-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="57c20-119">Especifica as configurações para o Pipe de rede ou serviços de compartilhamento de TCP.</span><span class="sxs-lookup"><span data-stu-id="57c20-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57c20-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57c20-120">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
