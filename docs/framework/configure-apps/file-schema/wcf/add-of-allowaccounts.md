---
title: '&lt;adicionar&gt; &lt;allowAccounts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09ab06bb94249e79743335da1a360f6b668b1d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="450ba-102">&lt;adicionar&gt; &lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="450ba-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="450ba-103">Especifica uma conta de usuário para processos que hospedam [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="450ba-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="450ba-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="450ba-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="450ba-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="450ba-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="450ba-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="450ba-106">Attributes and Elements</span></span>  
 <span data-ttu-id="450ba-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="450ba-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="450ba-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="450ba-108">Attributes</span></span>  
  
|<span data-ttu-id="450ba-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="450ba-109">Attribute</span></span>|<span data-ttu-id="450ba-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="450ba-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="450ba-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="450ba-111">securityIdentifier</span></span>|<span data-ttu-id="450ba-112">Uma cadeia de caracteres que especifica um identificador exclusivo usado para identificar uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="450ba-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="450ba-113">Os valores padrão são LocalSystem, administradores, NS, LS e IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="450ba-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="450ba-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="450ba-114">Child Elements</span></span>  
 <span data-ttu-id="450ba-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="450ba-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="450ba-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="450ba-116">Parent Elements</span></span>  
  
|<span data-ttu-id="450ba-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="450ba-117">Element</span></span>|<span data-ttu-id="450ba-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="450ba-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="450ba-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="450ba-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="450ba-120">Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="450ba-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="450ba-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="450ba-121">Example</span></span>  
 <span data-ttu-id="450ba-122">O exemplo de configuração a seguir adiciona os identificadores de cinco padrão para as contas de usuário para esta coleção.</span><span class="sxs-lookup"><span data-stu-id="450ba-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="450ba-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="450ba-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
