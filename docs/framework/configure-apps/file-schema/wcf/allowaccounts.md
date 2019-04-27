---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: f9def3004b116afdc629de136cdfe0b0eb6e75c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673531"
---
# <a name="allowaccounts"></a><span data-ttu-id="c615d-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="c615d-101">\<allowAccounts></span></span>
<span data-ttu-id="c615d-102">Contém uma coleção de elementos de configuração que especificam contas para processos que hospedam serviços Windows Communication Foundation (WCF) de usuário e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="c615d-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="c615d-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="c615d-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c615d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c615d-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c615d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c615d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c615d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c615d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c615d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c615d-107">Attributes</span></span>  
 <span data-ttu-id="c615d-108">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c615d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c615d-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c615d-109">Child Elements</span></span>  
  
|<span data-ttu-id="c615d-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="c615d-110">Attribute</span></span>|<span data-ttu-id="c615d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c615d-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c615d-112">\<add></span><span class="sxs-lookup"><span data-stu-id="c615d-112">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="c615d-113">Adiciona uma conta de usuário para processos que hospedam serviços do WCF e recebem acesso de conexão para o serviço de compartilhamento</span><span class="sxs-lookup"><span data-stu-id="c615d-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c615d-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c615d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c615d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c615d-115">Element</span></span>|<span data-ttu-id="c615d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c615d-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c615d-117">[\<NET. pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) ou [ \<NET. TCP >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="c615d-117">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="c615d-118">Especifica as configurações para o Pipe de rede ou serviços de compartilhamento de TCP.</span><span class="sxs-lookup"><span data-stu-id="c615d-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c615d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c615d-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
