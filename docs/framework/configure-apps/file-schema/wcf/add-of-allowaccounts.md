---
title: <add> de <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 1c6764b37b2aa5349b8ccf63e6b7c2bc580b69b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186596"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="65bd8-102">\<Adicionar > de \<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="65bd8-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="65bd8-103">Especifica uma conta de usuário para processos que hospedam serviços do WCF e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="65bd8-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="65bd8-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="65bd8-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65bd8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65bd8-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65bd8-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="65bd8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="65bd8-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="65bd8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65bd8-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="65bd8-108">Attributes</span></span>  
  
|<span data-ttu-id="65bd8-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="65bd8-109">Attribute</span></span>|<span data-ttu-id="65bd8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="65bd8-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65bd8-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="65bd8-111">securityIdentifier</span></span>|<span data-ttu-id="65bd8-112">Uma cadeia de caracteres que especifica um identificador exclusivo usado para identificar uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="65bd8-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="65bd8-113">Os valores padrão são IIS_USRS, administradores, NS, LS e LocalSystem.</span><span class="sxs-lookup"><span data-stu-id="65bd8-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65bd8-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="65bd8-114">Child Elements</span></span>  
 <span data-ttu-id="65bd8-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="65bd8-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65bd8-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="65bd8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="65bd8-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="65bd8-117">Element</span></span>|<span data-ttu-id="65bd8-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="65bd8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65bd8-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="65bd8-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="65bd8-120">Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam serviços do WCF e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="65bd8-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="65bd8-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65bd8-121">Example</span></span>  
 <span data-ttu-id="65bd8-122">O exemplo de configuração a seguir adiciona os identificadores de padrão de cinco contas de usuário a essa coleção.</span><span class="sxs-lookup"><span data-stu-id="65bd8-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="65bd8-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65bd8-123">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
