---
title: '&lt;Adicionar&gt; elemento para webRequestModules (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: 4c823f366baf51b35c15a87c2a9f6c9c4d3102d0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188517"
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="bd625-102">&lt;Adicionar&gt; elemento para webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="bd625-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="bd625-103">Adiciona um módulo de solicitação da Web personalizado para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd625-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="bd625-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bd625-104">\<configuration></span></span>  
<span data-ttu-id="bd625-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="bd625-105">\<system.net></span></span>  
<span data-ttu-id="bd625-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="bd625-106">\<webRequestModules></span></span>  
<span data-ttu-id="bd625-107">\<add></span><span class="sxs-lookup"><span data-stu-id="bd625-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd625-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd625-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd625-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bd625-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bd625-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bd625-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd625-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="bd625-111">Attributes</span></span>  
  
|<span data-ttu-id="bd625-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="bd625-112">**Attribute**</span></span>|<span data-ttu-id="bd625-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="bd625-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="bd625-114">O prefixo URI para solicitações manipuladas por esse módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="bd625-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="bd625-115">O nome do tipo totalmente qualificado (indicado pelo <xref:System.Type.FullName%2A> propriedade) e o nome do assembly (indicado pelo <xref:System.Reflection.Assembly.FullName%2A> propriedade), separados por uma vírgula, que implementa este módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="bd625-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd625-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bd625-116">Child Elements</span></span>  
 <span data-ttu-id="bd625-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bd625-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd625-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bd625-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bd625-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="bd625-119">**Element**</span></span>|<span data-ttu-id="bd625-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="bd625-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bd625-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="bd625-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="bd625-122">Especifica os módulos para usá-lo para solicitar informações de hosts da rede.</span><span class="sxs-lookup"><span data-stu-id="bd625-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd625-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd625-123">Remarks</span></span>  
 <span data-ttu-id="bd625-124">O `prefix` atributo define o prefixo URI que usa o módulo de solicitação da Web especificado.</span><span class="sxs-lookup"><span data-stu-id="bd625-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="bd625-125">Módulos de solicitação da Web geralmente são registrados para lidar com um protocolo específico, como HTTP ou FTP, mas podem ser registrados para manipular uma solicitação para um servidor específico ou um caminho em um servidor.</span><span class="sxs-lookup"><span data-stu-id="bd625-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="bd625-126">O módulo de solicitação da Web é criado quando um prefixo URI correspondente é passado para o <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="bd625-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="bd625-127">O valor para o `prefix` atributo deve ser os caracteres à esquerda de um URI válido.</span><span class="sxs-lookup"><span data-stu-id="bd625-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="bd625-128">Por exemplo `http` ou `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="bd625-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="bd625-129">O valor para o `type` atributo deve ser um nome de tipo válido e o nome do assembly correspondente, separados por vírgula.</span><span class="sxs-lookup"><span data-stu-id="bd625-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="bd625-130">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="bd625-130">Configuration Files</span></span>  
 <span data-ttu-id="bd625-131">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="bd625-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd625-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd625-132">Example</span></span>  
 <span data-ttu-id="bd625-133">O exemplo a seguir registra um módulo de solicitação da Web personalizado para HTTP.</span><span class="sxs-lookup"><span data-stu-id="bd625-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="bd625-134">Você deve substituir os valores de versão e PublicKeyToken com os valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="bd625-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd625-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd625-135">See Also</span></span>  
- <xref:System.Net.WebRequest>  
- [<span data-ttu-id="bd625-136">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="bd625-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
