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
ms.openlocfilehash: 0829f57d8dca91c2d895085dceaeea422229537c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176195"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="74fe6-102">Elemento \<remove> para authenticationModules (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="74fe6-102">\<remove> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="74fe6-103">Remove um módulo de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74fe6-103">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="74fe6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74fe6-104">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74fe6-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="74fe6-105">Attributes and Elements</span></span>  

 <span data-ttu-id="74fe6-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="74fe6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74fe6-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="74fe6-107">Attributes</span></span>  
  
|<span data-ttu-id="74fe6-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="74fe6-108">**Attribute**</span></span>|<span data-ttu-id="74fe6-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="74fe6-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="74fe6-110">**tipo**</span><span class="sxs-lookup"><span data-stu-id="74fe6-110">**type**</span></span>|<span data-ttu-id="74fe6-111">O nome do módulo de autenticação a ser removido.</span><span class="sxs-lookup"><span data-stu-id="74fe6-111">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74fe6-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="74fe6-112">Child Elements</span></span>  

 <span data-ttu-id="74fe6-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="74fe6-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74fe6-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="74fe6-114">Parent Elements</span></span>  
  
|<span data-ttu-id="74fe6-115">**Element**</span><span class="sxs-lookup"><span data-stu-id="74fe6-115">**Element**</span></span>|<span data-ttu-id="74fe6-116">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="74fe6-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="74fe6-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="74fe6-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="74fe6-118">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="74fe6-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74fe6-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="74fe6-119">Remarks</span></span>  

 <span data-ttu-id="74fe6-120">O `remove` elemento remove módulos de autenticação que foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="74fe6-120">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="74fe6-121">O valor do `type` atributo deve ser um nome de classe válido.</span><span class="sxs-lookup"><span data-stu-id="74fe6-121">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="74fe6-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="74fe6-122">Configuration Files</span></span>  

 <span data-ttu-id="74fe6-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="74fe6-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74fe6-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74fe6-124">Example</span></span>  

 <span data-ttu-id="74fe6-125">O exemplo a seguir remove um módulo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="74fe6-125">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74fe6-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="74fe6-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="74fe6-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="74fe6-127">Network Settings Schema</span></span>](index.md)
