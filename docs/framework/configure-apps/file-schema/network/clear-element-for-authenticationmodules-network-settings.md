---
title: '&lt;Limpar&gt; elemento para authenticationModules (configurações de rede)'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ef12a475dde103023d3411fb68efb3bdb4f6d116
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47076687"
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="08e0d-102">&lt;Limpar&gt; elemento para authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="08e0d-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="08e0d-103">Limpa todos os módulos de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08e0d-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="08e0d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="08e0d-104">\<configuration></span></span>  
<span data-ttu-id="08e0d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="08e0d-105">\<system.net></span></span>  
<span data-ttu-id="08e0d-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="08e0d-106">\<authenticationModules></span></span>  
<span data-ttu-id="08e0d-107">\<Limpar ></span><span class="sxs-lookup"><span data-stu-id="08e0d-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08e0d-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08e0d-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08e0d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08e0d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="08e0d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08e0d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08e0d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="08e0d-111">Attributes</span></span>  
 <span data-ttu-id="08e0d-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="08e0d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="08e0d-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08e0d-113">Child Elements</span></span>  
 <span data-ttu-id="08e0d-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="08e0d-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08e0d-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08e0d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="08e0d-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="08e0d-116">**Element**</span></span>|<span data-ttu-id="08e0d-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="08e0d-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="08e0d-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="08e0d-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="08e0d-119">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="08e0d-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08e0d-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="08e0d-120">Remarks</span></span>  
 <span data-ttu-id="08e0d-121">O `clear` elemento remove todos os módulos de autenticação que foram definidos anteriormente no arquivo de configuração ou em um nível mais alto na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="08e0d-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="08e0d-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="08e0d-122">Configuration Files</span></span>  
 <span data-ttu-id="08e0d-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="08e0d-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08e0d-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08e0d-124">Example</span></span>  
 <span data-ttu-id="08e0d-125">O exemplo a seguir remove todos os módulos de autenticação configurado.</span><span class="sxs-lookup"><span data-stu-id="08e0d-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08e0d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08e0d-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="08e0d-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="08e0d-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
