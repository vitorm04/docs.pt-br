---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152574"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="db61c-101">\<> serviceTokenResolver</span><span class="sxs-lookup"><span data-stu-id="db61c-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="db61c-102">Registra o resolver token de serviço que é usado pelos manipuladores na coleção de manipuladores de tokens.</span><span class="sxs-lookup"><span data-stu-id="db61c-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="db61c-103">O resolvede token de serviço é usado para resolver o token de criptografia em tokens e mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="db61c-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="db61c-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="db61c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="db61c-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="db61c-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="db61c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="db61c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="db61c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="db61c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="db61c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<Configuradodefalha>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="db61c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="db61c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span><span class="sxs-lookup"><span data-stu-id="db61c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db61c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db61c-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db61c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="db61c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="db61c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="db61c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db61c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="db61c-113">Attributes</span></span>  
  
|<span data-ttu-id="db61c-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="db61c-114">Attribute</span></span>|<span data-ttu-id="db61c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="db61c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db61c-116">type</span><span class="sxs-lookup"><span data-stu-id="db61c-116">type</span></span>|<span data-ttu-id="db61c-117">Especifica o tipo de solução do token de serviço.</span><span class="sxs-lookup"><span data-stu-id="db61c-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="db61c-118">Ou <xref:System.IdentityModel.Selectors.SecurityTokenResolver> o tipo ou um tipo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> que deriva da classe.</span><span class="sxs-lookup"><span data-stu-id="db61c-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="db61c-119">Para obter mais informações `type` sobre como especificar o atributo, consulte [Referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="db61c-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="db61c-120">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="db61c-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db61c-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="db61c-121">Child Elements</span></span>  
 <span data-ttu-id="db61c-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="db61c-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db61c-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="db61c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="db61c-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="db61c-124">Element</span></span>|<span data-ttu-id="db61c-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="db61c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db61c-126">\<Configuradodefalha></span><span class="sxs-lookup"><span data-stu-id="db61c-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="db61c-127">Fornece configuração para uma coleção de manipuladores de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="db61c-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db61c-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="db61c-128">Remarks</span></span>  
 <span data-ttu-id="db61c-129">O resolvede token de serviço pode ser usado para resolver o token de criptografia em tokens e mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="db61c-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="db61c-130">Ele é usado para recuperar a chave que deve ser usada para descriptografar tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="db61c-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="db61c-131">Você deve `type` especificar o atributo.</span><span class="sxs-lookup"><span data-stu-id="db61c-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="db61c-132">O tipo especificado <xref:System.IdentityModel.Selectors.SecurityTokenResolver> pode ser um ou um <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tipo personalizado que deriva da classe.</span><span class="sxs-lookup"><span data-stu-id="db61c-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="db61c-133">Alguns manipuladores de token permitem que você especifique as configurações de resolução de token de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="db61c-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="db61c-134">As configurações em manipuladores de token individuais anulam as especificadas na coleção de manipuladores de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="db61c-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db61c-135">Especificando `<serviceTokenResolver>` o elemento como elemento filho do [ \<](identityconfiguration.md) elemento identityConfiguration>foi preterido, mas ainda é suportado para compatibilidade retrógrada.</span><span class="sxs-lookup"><span data-stu-id="db61c-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="db61c-136">As configurações `<securityTokenHandlerConfiguration>` do elemento sobrepõem as do `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="db61c-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db61c-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db61c-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
