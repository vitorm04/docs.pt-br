---
title: <windowsAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399108"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="52d31-102">\<WindowsAuthentication > de \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="52d31-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="52d31-103">Especifica as configurações de uma credencial de serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="52d31-103">Specifies the settings of a Windows service credential.</span></span>  
  
<span data-ttu-id="52d31-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="52d31-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="52d31-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="52d31-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="52d31-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="52d31-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="52d31-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="52d31-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="52d31-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="52d31-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="52d31-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="52d31-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="52d31-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> windowsAuthentication**</span><span class="sxs-lookup"><span data-stu-id="52d31-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52d31-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52d31-111">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52d31-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="52d31-112">Attributes and Elements</span></span>  
 <span data-ttu-id="52d31-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="52d31-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52d31-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="52d31-114">Attributes</span></span>  
  
|<span data-ttu-id="52d31-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="52d31-115">Attribute</span></span>|<span data-ttu-id="52d31-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="52d31-116">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="52d31-117">Um atributo booliano opcional que especifica se o sistema inclui grupos do Windows no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="52d31-117">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="52d31-118">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="52d31-118">The default is `true`.</span></span><br /><br /> <span data-ttu-id="52d31-119">Definir esse atributo para `true` tem um impacto no desempenho conforme ele resulta em uma expansão de grupo completo.</span><span class="sxs-lookup"><span data-stu-id="52d31-119">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="52d31-120">Defina esse atributo como `false` se você não precisar estabelecer a lista de grupos aos quais um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="52d31-120">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="52d31-121">Um atributo booliano opcional que especifica se chamadores anônimos e não autenticados são permitidos.</span><span class="sxs-lookup"><span data-stu-id="52d31-121">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="52d31-122">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="52d31-122">The default is `false`.</span></span><br /><br /> <span data-ttu-id="52d31-123">Quando o `clientCredentialType` atributo de uma associação é definido como `Windows`, o sistema não permite chamadores anônimos.</span><span class="sxs-lookup"><span data-stu-id="52d31-123">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="52d31-124">Isso significa que somente os chamadores autenticados de domínio ou grupo de trabalho têm permissão para acessar o sistema.</span><span class="sxs-lookup"><span data-stu-id="52d31-124">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="52d31-125">Você pode substituir esse comportamento usando esse atributo.</span><span class="sxs-lookup"><span data-stu-id="52d31-125">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="52d31-126">Use essa configuração com extrema cautela.</span><span class="sxs-lookup"><span data-stu-id="52d31-126">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52d31-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="52d31-127">Child Elements</span></span>  
 <span data-ttu-id="52d31-128">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="52d31-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52d31-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="52d31-129">Parent Elements</span></span>  
  
|<span data-ttu-id="52d31-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="52d31-130">Element</span></span>|<span data-ttu-id="52d31-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="52d31-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52d31-132">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="52d31-132">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="52d31-133">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="52d31-133">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52d31-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="52d31-134">Remarks</span></span>  
 <span data-ttu-id="52d31-135">Use este elemento para especificar se deseja permitir o acesso de usuários anônimos do `allowAnonymousLogons` Windows definindo o atributo.</span><span class="sxs-lookup"><span data-stu-id="52d31-135">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="52d31-136">Você também pode especificar se deseja incluir informações de grupo às quais os usuários pertencem ao AuthorizationContext definindo o `includeWindowsGroups` atributo.</span><span class="sxs-lookup"><span data-stu-id="52d31-136">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="52d31-137">Se ele for definido como `true` (a configuração padrão), o serviço poderá determinar os grupos do Windows aos quais o cliente pertence.</span><span class="sxs-lookup"><span data-stu-id="52d31-137">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52d31-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52d31-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
