---
title: <add> de <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: cd4b9fd02eee2de1d0e8be185ffb69c0eae1cd58
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181720"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="022f9-102">\<add> de \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="022f9-102">\<add> of \<allowAccounts></span></span>

<span data-ttu-id="022f9-103">Especifica uma conta de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="022f9-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="022f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="022f9-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="022f9-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="022f9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="022f9-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="022f9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="022f9-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="022f9-107">Attributes</span></span>  
  
|<span data-ttu-id="022f9-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="022f9-108">Attribute</span></span>|<span data-ttu-id="022f9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="022f9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="022f9-110">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="022f9-110">securityIdentifier</span></span>|<span data-ttu-id="022f9-111">Uma cadeia de caracteres que especifica um identificador exclusivo usado para identificar uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="022f9-111">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="022f9-112">Os valores padrão são LocalSystem, Administrators, NS, LS e IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="022f9-112">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="022f9-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="022f9-113">Child Elements</span></span>  

 <span data-ttu-id="022f9-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="022f9-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="022f9-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="022f9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="022f9-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="022f9-116">Element</span></span>|<span data-ttu-id="022f9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="022f9-117">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="022f9-118">Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="022f9-118">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="022f9-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="022f9-119">Example</span></span>  

 <span data-ttu-id="022f9-120">O exemplo de configuração a seguir adiciona os cinco identificadores padrão para contas de usuário a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="022f9-120">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>
  <!-- LocalSystem account -->
  <add securityIdentifier="S-1-5-18" />
  <!-- LocalService account -->
  <add securityIdentifier="S-1-5-19" />
  <!-- Administrators account -->
  <add securityIdentifier="S-1-5-20" />
  <!-- Network Service account -->
  <add securityIdentifier="S-1-5-32-544" />
  <!-- IIS_IUSRS account (Vista only) -->
  <add securityIdentifier="S-1-5-32-568" />
</allowAccounts>
```  
  
## <a name="see-also"></a><span data-ttu-id="022f9-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="022f9-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
