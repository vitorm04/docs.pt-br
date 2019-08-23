---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c62f29c53d807cab397ff09c6163d924a71ea319
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926605"
---
# <a name="allowaccounts"></a><span data-ttu-id="a203d-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="a203d-101">\<allowAccounts></span></span>
<span data-ttu-id="a203d-102">Contém uma coleção de elementos de configuração que especificam contas de usuário para processos que hospedam serviços Windows Communication Foundation (WCF) e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="a203d-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="a203d-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="a203d-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a203d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a203d-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a203d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a203d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a203d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a203d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a203d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a203d-107">Attributes</span></span>  
 <span data-ttu-id="a203d-108">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a203d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a203d-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a203d-109">Child Elements</span></span>  
  
|<span data-ttu-id="a203d-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="a203d-110">Attribute</span></span>|<span data-ttu-id="a203d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a203d-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="a203d-112">\<add></span><span class="sxs-lookup"><span data-stu-id="a203d-112">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="a203d-113">Adiciona uma conta de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento</span><span class="sxs-lookup"><span data-stu-id="a203d-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a203d-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a203d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a203d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="a203d-115">Element</span></span>|<span data-ttu-id="a203d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a203d-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a203d-117">[> > NET. pipe ou net. TCP \<](net-pipe.md) [ \<](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="a203d-117">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="a203d-118">Especifica as definições de configuração para o pipe de rede ou para os serviços de compartilhamento de TCP.</span><span class="sxs-lookup"><span data-stu-id="a203d-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a203d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a203d-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
