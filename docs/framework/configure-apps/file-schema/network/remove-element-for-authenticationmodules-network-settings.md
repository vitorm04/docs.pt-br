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
ms.openlocfilehash: d171fea193bbae068e69b8976abb8e56a5623f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154771"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="f886b-102">\<remover> Elemento para autenticaçãoMódulos (Configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="f886b-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="f886b-103">Remove um módulo de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f886b-103">Removes an authentication module from the application.</span></span>  

<span data-ttu-id="f886b-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f886b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f886b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f886b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="f886b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<autenticaçãoMódulos>**](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f886b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="f886b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remover>**</span><span class="sxs-lookup"><span data-stu-id="f886b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f886b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f886b-108">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f886b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f886b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f886b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f886b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f886b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f886b-111">Attributes</span></span>  
  
|<span data-ttu-id="f886b-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="f886b-112">**Attribute**</span></span>|<span data-ttu-id="f886b-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="f886b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="f886b-114">**type**</span><span class="sxs-lookup"><span data-stu-id="f886b-114">**type**</span></span>|<span data-ttu-id="f886b-115">O nome do módulo de autenticação a ser removido.</span><span class="sxs-lookup"><span data-stu-id="f886b-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f886b-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f886b-116">Child Elements</span></span>  
 <span data-ttu-id="f886b-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f886b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f886b-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f886b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f886b-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="f886b-119">**Element**</span></span>|<span data-ttu-id="f886b-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="f886b-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f886b-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="f886b-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="f886b-122">Especifica módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="f886b-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f886b-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="f886b-123">Remarks</span></span>  
 <span data-ttu-id="f886b-124">O `remove` elemento remove módulos de autenticação definidos anteriormente no arquivo de configuração ou em um nível mais alto na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="f886b-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="f886b-125">O valor `type` para o atributo deve ser um nome de classe válido.</span><span class="sxs-lookup"><span data-stu-id="f886b-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f886b-126">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="f886b-126">Configuration Files</span></span>  
 <span data-ttu-id="f886b-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f886b-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f886b-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f886b-128">Example</span></span>  
 <span data-ttu-id="f886b-129">O exemplo a seguir remove um módulo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="f886b-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f886b-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="f886b-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="f886b-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="f886b-131">Network Settings Schema</span></span>](index.md)
