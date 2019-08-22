---
title: Elemento <remove> para webRequestModules (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: 20a586e945a889d1fd8a8d4c5c09c8b790c56fc3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664023"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="8baea-102">\<remover o elemento > para webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8baea-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="8baea-103">Remove um módulo de solicitação da Web personalizado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8baea-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="8baea-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8baea-104">\<configuration></span></span>  
<span data-ttu-id="8baea-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8baea-105">\<system.net></span></span>  
<span data-ttu-id="8baea-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="8baea-106">\<webRequestModules></span></span>  
<span data-ttu-id="8baea-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="8baea-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8baea-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8baea-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8baea-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8baea-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8baea-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8baea-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8baea-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="8baea-111">Attributes</span></span>  
  
|<span data-ttu-id="8baea-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="8baea-112">**Attribute**</span></span>|<span data-ttu-id="8baea-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="8baea-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="8baea-114">O prefixo de URI para solicitações tratadas por este módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="8baea-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8baea-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8baea-115">Child Elements</span></span>  
 <span data-ttu-id="8baea-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8baea-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8baea-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8baea-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8baea-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="8baea-118">**Element**</span></span>|<span data-ttu-id="8baea-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="8baea-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8baea-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="8baea-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="8baea-121">Especifica os módulos a serem usados para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="8baea-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8baea-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="8baea-122">Remarks</span></span>  
 <span data-ttu-id="8baea-123">O `remove` elemento remove o módulo de solicitação da Web registrado para o prefixo de URI especificado.</span><span class="sxs-lookup"><span data-stu-id="8baea-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="8baea-124">O valor `prefix` do atributo deve ser os caracteres à esquerda de um URI válido, por exemplo, "`http`" ou "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="8baea-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8baea-125">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="8baea-125">Configuration Files</span></span>  
 <span data-ttu-id="8baea-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8baea-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8baea-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8baea-127">Example</span></span>  

<span data-ttu-id="8baea-128">O exemplo a seguir remove o módulo de solicitação da Web existente para HTTP e registra um novo módulo de solicitação da Web personalizado `www.contoso.com`para solicitações HTTP para.</span><span class="sxs-lookup"><span data-stu-id="8baea-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="8baea-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8baea-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="8baea-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="8baea-130">Network Settings Schema</span></span>](index.md)
