---
title: <add> de <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398385"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="87781-102">\<Adicionar > de \<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="87781-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="87781-103">Especifica uma conta de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="87781-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="87781-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87781-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="87781-105">&nbsp;&nbsp;[ **\<sistema. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="87781-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="87781-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de net. pipe**](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="87781-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="87781-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> allowAccounts**](allowaccounts.md)</span><span class="sxs-lookup"><span data-stu-id="87781-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)</span></span>\
<span data-ttu-id="87781-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="87781-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87781-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87781-109">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87781-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="87781-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87781-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="87781-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87781-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="87781-112">Attributes</span></span>  
  
|<span data-ttu-id="87781-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="87781-113">Attribute</span></span>|<span data-ttu-id="87781-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="87781-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87781-115">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="87781-115">securityIdentifier</span></span>|<span data-ttu-id="87781-116">Uma cadeia de caracteres que especifica um identificador exclusivo usado para identificar uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="87781-116">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="87781-117">Os valores padrão são LocalSystem, Administrators, NS, LS e IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="87781-117">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87781-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="87781-118">Child Elements</span></span>  
 <span data-ttu-id="87781-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="87781-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87781-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="87781-120">Parent Elements</span></span>  
  
|<span data-ttu-id="87781-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="87781-121">Element</span></span>|<span data-ttu-id="87781-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="87781-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87781-123">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="87781-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="87781-124">Uma coleção de elementos de configuração que contêm `securityIdentifier` um atributo para especificar contas de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="87781-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="87781-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87781-125">Example</span></span>  
 <span data-ttu-id="87781-126">O exemplo de configuração a seguir adiciona os cinco identificadores padrão para contas de usuário a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="87781-126">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="87781-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87781-127">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
