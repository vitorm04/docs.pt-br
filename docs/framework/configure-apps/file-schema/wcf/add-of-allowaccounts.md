---
title: '&lt;adicionar&gt; &lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 2230b8d22a14c3df5eb3aa10872246febce015e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349685"
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="9c9d6-102">&lt;adicionar&gt; &lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="9c9d6-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="9c9d6-103">Especifica uma conta de usuário para processos que hospedam serviços do WCF e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="9c9d6-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="9c9d6-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="9c9d6-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c9d6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c9d6-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c9d6-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c9d6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="9c9d6-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c9d6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c9d6-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c9d6-108">Attributes</span></span>  
  
|<span data-ttu-id="9c9d6-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="9c9d6-109">Attribute</span></span>|<span data-ttu-id="9c9d6-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c9d6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c9d6-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="9c9d6-111">securityIdentifier</span></span>|<span data-ttu-id="9c9d6-112">Uma cadeia de caracteres que especifica um identificador exclusivo usado para identificar uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="9c9d6-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="9c9d6-113">Os valores padrão são LocalSystem, administradores, NS, LS e IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="9c9d6-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c9d6-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c9d6-114">Child Elements</span></span>  
 <span data-ttu-id="9c9d6-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9c9d6-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c9d6-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c9d6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9c9d6-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c9d6-117">Element</span></span>|<span data-ttu-id="9c9d6-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c9d6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c9d6-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="9c9d6-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="9c9d6-120">Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam serviços do WCF e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="9c9d6-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9c9d6-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c9d6-121">Example</span></span>  
 <span data-ttu-id="9c9d6-122">O exemplo de configuração a seguir adiciona os identificadores de cinco padrão para as contas de usuário para esta coleção.</span><span class="sxs-lookup"><span data-stu-id="9c9d6-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c9d6-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c9d6-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
