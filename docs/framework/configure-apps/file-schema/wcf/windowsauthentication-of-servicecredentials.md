---
title: <windowsAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 81793b0d58a95166bc23f98d46ce94a5f1e1d018
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940287"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="d0abe-102">\<WindowsAuthentication > de \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="d0abe-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="d0abe-103">Especifica as configurações de uma credencial de serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="d0abe-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="d0abe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0abe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0abe-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="d0abe-105">\<behaviors></span></span>  
<span data-ttu-id="d0abe-106">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="d0abe-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d0abe-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="d0abe-107">\<behavior></span></span>  
<span data-ttu-id="d0abe-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="d0abe-108">\<serviceCredentials></span></span>  
<span data-ttu-id="d0abe-109">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="d0abe-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0abe-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0abe-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0abe-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0abe-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d0abe-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d0abe-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0abe-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0abe-113">Attributes</span></span>  
  
|<span data-ttu-id="d0abe-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="d0abe-114">Attribute</span></span>|<span data-ttu-id="d0abe-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0abe-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="d0abe-116">Um atributo booliano opcional que especifica se o sistema inclui grupos do Windows no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="d0abe-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="d0abe-117">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="d0abe-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="d0abe-118">Definir esse atributo para `true` tem um impacto no desempenho conforme ele resulta em uma expansão de grupo completo.</span><span class="sxs-lookup"><span data-stu-id="d0abe-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="d0abe-119">Defina esse atributo como `false` se você não precisar estabelecer a lista de grupos aos quais um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="d0abe-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="d0abe-120">Um atributo booliano opcional que especifica se chamadores anônimos e não autenticados são permitidos.</span><span class="sxs-lookup"><span data-stu-id="d0abe-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="d0abe-121">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="d0abe-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="d0abe-122">Quando o `clientCredentialType` atributo de uma associação é definido como `Windows`, o sistema não permite chamadores anônimos.</span><span class="sxs-lookup"><span data-stu-id="d0abe-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="d0abe-123">Isso significa que somente os chamadores autenticados de domínio ou grupo de trabalho têm permissão para acessar o sistema.</span><span class="sxs-lookup"><span data-stu-id="d0abe-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="d0abe-124">Você pode substituir esse comportamento usando esse atributo.</span><span class="sxs-lookup"><span data-stu-id="d0abe-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="d0abe-125">Use essa configuração com extrema cautela.</span><span class="sxs-lookup"><span data-stu-id="d0abe-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0abe-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0abe-126">Child Elements</span></span>  
 <span data-ttu-id="d0abe-127">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d0abe-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0abe-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0abe-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d0abe-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0abe-129">Element</span></span>|<span data-ttu-id="d0abe-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0abe-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0abe-131">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="d0abe-131">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="d0abe-132">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="d0abe-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0abe-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0abe-133">Remarks</span></span>  
 <span data-ttu-id="d0abe-134">Use este elemento para especificar se deseja permitir o acesso de usuários anônimos do `allowAnonymousLogons` Windows definindo o atributo.</span><span class="sxs-lookup"><span data-stu-id="d0abe-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="d0abe-135">Você também pode especificar se deseja incluir informações de grupo às quais os usuários pertencem ao AuthorizationContext definindo o `includeWindowsGroups` atributo.</span><span class="sxs-lookup"><span data-stu-id="d0abe-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="d0abe-136">Se ele for definido como `true` (a configuração padrão), o serviço poderá determinar os grupos do Windows aos quais o cliente pertence.</span><span class="sxs-lookup"><span data-stu-id="d0abe-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0abe-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0abe-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
