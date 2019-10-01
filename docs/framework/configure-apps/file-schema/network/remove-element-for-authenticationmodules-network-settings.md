---
title: Elemento <remove> para authenticationModules (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: 9b73c0dc1fe161616c08ef0501241d55e9fea9bc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697937"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="d1230-102">\<remove > elemento para authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="d1230-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="d1230-103">Remove um módulo de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d1230-103">Removes an authentication module from the application.</span></span>  
  
[<span data-ttu-id="d1230-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="d1230-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="d1230-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d1230-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="d1230-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d1230-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="d1230-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="d1230-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1230-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1230-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1230-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d1230-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d1230-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d1230-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1230-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="d1230-111">Attributes</span></span>  
  
|<span data-ttu-id="d1230-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="d1230-112">**Attribute**</span></span>|<span data-ttu-id="d1230-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d1230-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="d1230-114">**type**</span><span class="sxs-lookup"><span data-stu-id="d1230-114">**type**</span></span>|<span data-ttu-id="d1230-115">O nome do módulo de autenticação a ser removido.</span><span class="sxs-lookup"><span data-stu-id="d1230-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1230-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d1230-116">Child Elements</span></span>  
 <span data-ttu-id="d1230-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d1230-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1230-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d1230-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d1230-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d1230-119">**Element**</span></span>|<span data-ttu-id="d1230-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d1230-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d1230-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="d1230-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="d1230-122">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="d1230-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1230-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1230-123">Remarks</span></span>  
 <span data-ttu-id="d1230-124">O elemento `remove` remove módulos de autenticação que foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="d1230-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="d1230-125">O valor do atributo `type` deve ser um nome de classe válido.</span><span class="sxs-lookup"><span data-stu-id="d1230-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d1230-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="d1230-126">Configuration Files</span></span>  
 <span data-ttu-id="d1230-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="d1230-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1230-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1230-128">Example</span></span>  
 <span data-ttu-id="d1230-129">O exemplo a seguir remove um módulo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="d1230-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1230-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1230-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="d1230-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="d1230-131">Network Settings Schema</span></span>](index.md)
