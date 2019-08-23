---
title: <add> de <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 1ed0b5025ab969c45d7440f2a209426c5c87f549
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920285"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="6aa89-102">\<Adicionar > de \<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="6aa89-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="6aa89-103">Especifica uma conta de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="6aa89-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="6aa89-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="6aa89-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aa89-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6aa89-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6aa89-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6aa89-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6aa89-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6aa89-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6aa89-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="6aa89-108">Attributes</span></span>  
  
|<span data-ttu-id="6aa89-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="6aa89-109">Attribute</span></span>|<span data-ttu-id="6aa89-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6aa89-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6aa89-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="6aa89-111">securityIdentifier</span></span>|<span data-ttu-id="6aa89-112">Uma cadeia de caracteres que especifica um identificador exclusivo usado para identificar uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="6aa89-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="6aa89-113">Os valores padrão são LocalSystem, Administrators, NS, LS e IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="6aa89-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6aa89-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6aa89-114">Child Elements</span></span>  
 <span data-ttu-id="6aa89-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6aa89-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6aa89-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6aa89-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6aa89-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="6aa89-117">Element</span></span>|<span data-ttu-id="6aa89-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="6aa89-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6aa89-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="6aa89-119">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="6aa89-120">Uma coleção de elementos de configuração que contêm `securityIdentifier` um atributo para especificar contas de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="6aa89-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6aa89-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6aa89-121">Example</span></span>  
 <span data-ttu-id="6aa89-122">O exemplo de configuração a seguir adiciona os cinco identificadores padrão para contas de usuário a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="6aa89-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6aa89-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6aa89-123">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
