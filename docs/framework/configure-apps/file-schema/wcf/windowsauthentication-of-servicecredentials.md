---
title: <windowsAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399108"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="e03b8-102">\<windowsAuthentication> de \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e03b8-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="e03b8-103">Especifica as configurações de uma credencial de serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="e03b8-103">Specifies the settings of a Windows service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="e03b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e03b8-104">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e03b8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e03b8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e03b8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e03b8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e03b8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e03b8-107">Attributes</span></span>  
  
|<span data-ttu-id="e03b8-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e03b8-108">Attribute</span></span>|<span data-ttu-id="e03b8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e03b8-109">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="e03b8-110">Um atributo booliano opcional que especifica se o sistema inclui grupos do Windows no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="e03b8-110">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="e03b8-111">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="e03b8-111">The default is `true`.</span></span><br /><br /> <span data-ttu-id="e03b8-112">Definir esse atributo para `true` tem um impacto no desempenho conforme ele resulta em uma expansão de grupo completo.</span><span class="sxs-lookup"><span data-stu-id="e03b8-112">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="e03b8-113">Defina esse atributo como `false` se você não precisar estabelecer a lista de grupos aos quais um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="e03b8-113">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="e03b8-114">Um atributo booliano opcional que especifica se chamadores anônimos e não autenticados são permitidos.</span><span class="sxs-lookup"><span data-stu-id="e03b8-114">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="e03b8-115">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="e03b8-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e03b8-116">Quando o `clientCredentialType` atributo de uma associação é definido como `Windows` , o sistema não permite chamadores anônimos.</span><span class="sxs-lookup"><span data-stu-id="e03b8-116">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="e03b8-117">Isso significa que somente os chamadores autenticados de domínio ou grupo de trabalho têm permissão para acessar o sistema.</span><span class="sxs-lookup"><span data-stu-id="e03b8-117">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="e03b8-118">Você pode substituir esse comportamento usando esse atributo.</span><span class="sxs-lookup"><span data-stu-id="e03b8-118">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="e03b8-119">Use essa configuração com extrema cautela.</span><span class="sxs-lookup"><span data-stu-id="e03b8-119">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e03b8-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e03b8-120">Child Elements</span></span>  
 <span data-ttu-id="e03b8-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e03b8-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e03b8-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e03b8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e03b8-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="e03b8-123">Element</span></span>|<span data-ttu-id="e03b8-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="e03b8-124">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="e03b8-125">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="e03b8-125">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e03b8-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e03b8-126">Remarks</span></span>  
 <span data-ttu-id="e03b8-127">Use este elemento para especificar se deseja permitir o acesso de usuários anônimos do Windows definindo o `allowAnonymousLogons` atributo.</span><span class="sxs-lookup"><span data-stu-id="e03b8-127">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="e03b8-128">Você também pode especificar se deseja incluir informações de grupo às quais os usuários pertencem ao AuthorizationContext definindo o `includeWindowsGroups` atributo.</span><span class="sxs-lookup"><span data-stu-id="e03b8-128">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="e03b8-129">Se ele for definido como `true` (a configuração padrão), o serviço poderá determinar os grupos do Windows aos quais o cliente pertence.</span><span class="sxs-lookup"><span data-stu-id="e03b8-129">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03b8-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="e03b8-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
