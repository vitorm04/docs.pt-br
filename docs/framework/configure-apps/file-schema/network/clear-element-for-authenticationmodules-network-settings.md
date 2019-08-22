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
ms.openlocfilehash: 12ac146926103b40073d34f48895b0645c8a8ed2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659476"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="fb984-102">\<limpar > elemento para authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="fb984-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="fb984-103">Limpa todos os módulos de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb984-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="fb984-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="fb984-104">\<configuration></span></span>  
<span data-ttu-id="fb984-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fb984-105">\<system.net></span></span>  
<span data-ttu-id="fb984-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="fb984-106">\<authenticationModules></span></span>  
<span data-ttu-id="fb984-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="fb984-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb984-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb984-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb984-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fb984-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fb984-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fb984-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb984-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb984-111">Attributes</span></span>  
 <span data-ttu-id="fb984-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fb984-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fb984-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fb984-113">Child Elements</span></span>  
 <span data-ttu-id="fb984-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fb984-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb984-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fb984-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fb984-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="fb984-116">**Element**</span></span>|<span data-ttu-id="fb984-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="fb984-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fb984-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="fb984-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="fb984-119">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="fb984-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb984-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb984-120">Remarks</span></span>  
 <span data-ttu-id="fb984-121">O `clear` elemento remove todos os módulos de autenticação que foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="fb984-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fb984-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="fb984-122">Configuration Files</span></span>  
 <span data-ttu-id="fb984-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="fb984-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb984-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb984-124">Example</span></span>  
 <span data-ttu-id="fb984-125">O exemplo a seguir remove todos os módulos de autenticação configurados.</span><span class="sxs-lookup"><span data-stu-id="fb984-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb984-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb984-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="fb984-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="fb984-127">Network Settings Schema</span></span>](index.md)
