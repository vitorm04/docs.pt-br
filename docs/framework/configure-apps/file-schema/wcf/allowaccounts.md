---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 3432d33c0cd65af03d2b1ac1302ca2c8ff3e0f43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201636"
---
# \<allowAccounts>

<span data-ttu-id="10414-101">Contém uma coleção de elementos de configuração que especificam contas de usuário para processos que hospedam serviços Windows Communication Foundation (WCF) e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="10414-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="10414-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10414-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10414-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="10414-103">Attributes and Elements</span></span>  

 <span data-ttu-id="10414-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="10414-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10414-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="10414-105">Attributes</span></span>  

 <span data-ttu-id="10414-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="10414-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10414-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="10414-107">Child Elements</span></span>  
  
|<span data-ttu-id="10414-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="10414-108">Attribute</span></span>|<span data-ttu-id="10414-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="10414-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="10414-110">Adiciona uma conta de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento</span><span class="sxs-lookup"><span data-stu-id="10414-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10414-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="10414-111">Parent Elements</span></span>  
  
|<span data-ttu-id="10414-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="10414-112">Element</span></span>|<span data-ttu-id="10414-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="10414-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10414-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="10414-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="10414-115">Especifica as definições de configuração para o pipe de rede ou para os serviços de compartilhamento de TCP.</span><span class="sxs-lookup"><span data-stu-id="10414-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10414-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="10414-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
