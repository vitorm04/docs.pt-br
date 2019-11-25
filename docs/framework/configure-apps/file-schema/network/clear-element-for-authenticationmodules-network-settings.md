---
title: Elemento <clear> para authenticationModules (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: e3abd1b4c76ebda885703ccf961d58657b582f19
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087506"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="281e4-102">\<limpar > elemento para authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="281e4-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="281e4-103">Limpa todos os módulos de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="281e4-103">Clears all authentication modules from the application.</span></span>  

<span data-ttu-id="281e4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="281e4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="281e4-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="281e4-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="281e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="281e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="281e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**desmarque >**</span><span class="sxs-lookup"><span data-stu-id="281e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="281e4-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="281e4-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="281e4-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="281e4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="281e4-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="281e4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="281e4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="281e4-111">Attributes</span></span>  
 <span data-ttu-id="281e4-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="281e4-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="281e4-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="281e4-113">Child Elements</span></span>  
 <span data-ttu-id="281e4-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="281e4-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="281e4-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="281e4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="281e4-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="281e4-116">**Element**</span></span>|<span data-ttu-id="281e4-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="281e4-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="281e4-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="281e4-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="281e4-119">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="281e4-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="281e4-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="281e4-120">Remarks</span></span>  
 <span data-ttu-id="281e4-121">O elemento `clear` remove todos os módulos de autenticação que foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="281e4-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="281e4-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="281e4-122">Configuration Files</span></span>  
 <span data-ttu-id="281e4-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="281e4-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="281e4-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="281e4-124">Example</span></span>  
 <span data-ttu-id="281e4-125">O exemplo a seguir remove todos os módulos de autenticação configurados.</span><span class="sxs-lookup"><span data-stu-id="281e4-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="281e4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="281e4-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="281e4-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="281e4-127">Network Settings Schema</span></span>](index.md)
