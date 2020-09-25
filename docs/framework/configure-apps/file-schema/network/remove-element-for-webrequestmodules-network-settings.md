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
ms.openlocfilehash: 65e8b1f2088015b86d4f981f07875d236a11a617
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176182"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="84e5d-102">Elemento \<remove> para webRequestModules (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="84e5d-102">\<remove> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="84e5d-103">Remove um módulo de solicitação da Web personalizado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84e5d-103">Removes a custom Web request module from the application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**
  
## <a name="syntax"></a><span data-ttu-id="84e5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84e5d-104">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84e5d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="84e5d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="84e5d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="84e5d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84e5d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="84e5d-107">Attributes</span></span>  
  
|<span data-ttu-id="84e5d-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="84e5d-108">**Attribute**</span></span>|<span data-ttu-id="84e5d-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="84e5d-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="84e5d-110">O prefixo de URI para solicitações tratadas por este módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="84e5d-110">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84e5d-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="84e5d-111">Child Elements</span></span>  

 <span data-ttu-id="84e5d-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="84e5d-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84e5d-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="84e5d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="84e5d-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="84e5d-114">**Element**</span></span>|<span data-ttu-id="84e5d-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="84e5d-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="84e5d-116">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="84e5d-116">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="84e5d-117">Especifica os módulos a serem usados para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="84e5d-117">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84e5d-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="84e5d-118">Remarks</span></span>  

 <span data-ttu-id="84e5d-119">O `remove` elemento remove o módulo de solicitação da Web registrado para o prefixo de URI especificado.</span><span class="sxs-lookup"><span data-stu-id="84e5d-119">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="84e5d-120">O valor do `prefix` atributo deve ser os caracteres à esquerda de um URI válido, por exemplo, " `http` " ou " `http://www.contoso.com` ".</span><span class="sxs-lookup"><span data-stu-id="84e5d-120">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="84e5d-121">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="84e5d-121">Configuration Files</span></span>  

 <span data-ttu-id="84e5d-122">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="84e5d-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84e5d-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84e5d-123">Example</span></span>  

<span data-ttu-id="84e5d-124">O exemplo a seguir remove o módulo de solicitação da Web existente para HTTP e registra um novo módulo de solicitação da Web personalizado para solicitações HTTP para `www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="84e5d-124">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="84e5d-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="84e5d-125">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="84e5d-126">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="84e5d-126">Network Settings Schema</span></span>](index.md)
