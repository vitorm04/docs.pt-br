---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398411"
---
# <a name="allowaccounts"></a><span data-ttu-id="9ab13-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="9ab13-101">\<allowAccounts></span></span>
<span data-ttu-id="9ab13-102">Contém uma coleção de elementos de configuração que especificam contas de usuário para processos que hospedam serviços Windows Communication Foundation (WCF) e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="9ab13-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="9ab13-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9ab13-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9ab13-104">&nbsp;&nbsp;[ **\<sistema. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="9ab13-104">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="9ab13-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de net. pipe**](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="9ab13-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="9ab13-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> allowAccounts**</span><span class="sxs-lookup"><span data-stu-id="9ab13-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ab13-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ab13-107">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ab13-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9ab13-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9ab13-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9ab13-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ab13-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9ab13-110">Attributes</span></span>  
 <span data-ttu-id="9ab13-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9ab13-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ab13-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9ab13-112">Child Elements</span></span>  
  
|<span data-ttu-id="9ab13-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9ab13-113">Attribute</span></span>|<span data-ttu-id="9ab13-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ab13-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="9ab13-115">\<add></span><span class="sxs-lookup"><span data-stu-id="9ab13-115">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="9ab13-116">Adiciona uma conta de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento</span><span class="sxs-lookup"><span data-stu-id="9ab13-116">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ab13-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9ab13-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9ab13-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9ab13-118">Element</span></span>|<span data-ttu-id="9ab13-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ab13-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ab13-120">[> > NET. pipe ou net. TCP \<](net-pipe.md) [ \<](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="9ab13-120">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="9ab13-121">Especifica as definições de configuração para o pipe de rede ou para os serviços de compartilhamento de TCP.</span><span class="sxs-lookup"><span data-stu-id="9ab13-121">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ab13-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ab13-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
