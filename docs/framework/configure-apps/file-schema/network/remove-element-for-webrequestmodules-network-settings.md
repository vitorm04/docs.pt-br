---
title: "&lt;remover&gt; elemento webRequestModules (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 391e5f2a7d9d8076ba9e9a3057e3d8899e2ce672
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="ca1b4-102">&lt;remover&gt; elemento webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="ca1b4-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="ca1b4-103">Remove um módulo personalizado de solicitação da Web do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca1b4-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="ca1b4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ca1b4-104">\<configuration></span></span>  
<span data-ttu-id="ca1b4-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="ca1b4-105">\<system.net></span></span>  
<span data-ttu-id="ca1b4-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="ca1b4-106">\<webRequestModules></span></span>  
<span data-ttu-id="ca1b4-107">\<Remover ></span><span class="sxs-lookup"><span data-stu-id="ca1b4-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca1b4-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca1b4-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca1b4-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ca1b4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ca1b4-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ca1b4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca1b4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ca1b4-111">Attributes</span></span>  
  
|<span data-ttu-id="ca1b4-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="ca1b4-112">**Attribute**</span></span>|<span data-ttu-id="ca1b4-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ca1b4-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="ca1b4-114">O prefixo do URI para solicitações tratadas por este módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="ca1b4-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca1b4-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ca1b4-115">Child Elements</span></span>  
 <span data-ttu-id="ca1b4-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ca1b4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca1b4-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ca1b4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ca1b4-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ca1b4-118">**Element**</span></span>|<span data-ttu-id="ca1b4-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ca1b4-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ca1b4-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="ca1b4-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="ca1b4-121">Especifica módulos a ser usado para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="ca1b4-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca1b4-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca1b4-122">Remarks</span></span>  
 <span data-ttu-id="ca1b4-123">O `remove` elemento remove o módulo de solicitação da Web registrado para o prefixo URI especificado.</span><span class="sxs-lookup"><span data-stu-id="ca1b4-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="ca1b4-124">O valor para o `prefix` atributo deve ser os caracteres à esquerda de um URI válido – por exemplo, "http" ou "http://www.contoso.com".</span><span class="sxs-lookup"><span data-stu-id="ca1b4-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "http://www.contoso.com".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ca1b4-125">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="ca1b4-125">Configuration Files</span></span>  
 <span data-ttu-id="ca1b4-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ca1b4-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca1b4-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca1b4-127">Example</span></span>  
 <span data-ttu-id="ca1b4-128">O exemplo a seguir remove o módulo de solicitação da Web existente para HTTP e, em seguida, registra um novo módulo de solicitação da Web personalizado para solicitações HTTP para www.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="ca1b4-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca1b4-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca1b4-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="ca1b4-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="ca1b4-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
