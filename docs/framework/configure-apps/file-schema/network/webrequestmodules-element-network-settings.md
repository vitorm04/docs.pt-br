---
title: '&lt;webRequestModules&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7cd25b980afa067ac78fc081c0a7a8e65a23258b
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838249"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a><span data-ttu-id="380c7-102">&lt;webRequestModules&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="380c7-102">&lt;webRequestModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="380c7-103">Especifica os módulos para usá-lo para solicitar informações de hosts da rede.</span><span class="sxs-lookup"><span data-stu-id="380c7-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="380c7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="380c7-104">\<configuration></span></span>  
<span data-ttu-id="380c7-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="380c7-105">\<system.net></span></span>  
<span data-ttu-id="380c7-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="380c7-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="380c7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="380c7-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="380c7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="380c7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="380c7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="380c7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="380c7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="380c7-110">Attributes</span></span>  
 <span data-ttu-id="380c7-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="380c7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="380c7-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="380c7-112">Child Elements</span></span>  
  
|<span data-ttu-id="380c7-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="380c7-113">**Element**</span></span>|<span data-ttu-id="380c7-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="380c7-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="380c7-115">add</span><span class="sxs-lookup"><span data-stu-id="380c7-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="380c7-116">Adiciona um módulo de solicitação da Web personalizado para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="380c7-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="380c7-117">clear</span><span class="sxs-lookup"><span data-stu-id="380c7-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="380c7-118">Remove todos os módulos de solicitação da Web registrados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="380c7-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="380c7-119">remove</span><span class="sxs-lookup"><span data-stu-id="380c7-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="380c7-120">Remove um módulo de solicitação da Web personalizado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="380c7-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="380c7-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="380c7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="380c7-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="380c7-122">**Element**</span></span>|<span data-ttu-id="380c7-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="380c7-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="380c7-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="380c7-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="380c7-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="380c7-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="380c7-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="380c7-126">Remarks</span></span>  
 <span data-ttu-id="380c7-127">O `webRequestModules` descendentes do elemento registra o <xref:System.Net.WebRequest> classe para manipular solicitações de informações e os hosts da rede.</span><span class="sxs-lookup"><span data-stu-id="380c7-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="380c7-128">Módulos de solicitação da Web devem implementar o <xref:System.Net.IWebRequestCreate> interface.</span><span class="sxs-lookup"><span data-stu-id="380c7-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="380c7-129">O .NET Framework inclui módulos de solicitação da Web para URIs que começam com `http://`, `https://`, e `file://`.</span><span class="sxs-lookup"><span data-stu-id="380c7-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="380c7-130">Você pode substituir os módulos padrão somente por registrar um módulo personalizado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="380c7-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="380c7-131">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="380c7-131">Configuration Files</span></span>  
 <span data-ttu-id="380c7-132">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="380c7-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="380c7-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="380c7-133">Example</span></span>  
 <span data-ttu-id="380c7-134">O exemplo a seguir registra o módulo HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="380c7-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="380c7-135">Você deve substituir os valores de versão e PublicKeyToken com os valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="380c7-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="380c7-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="380c7-136">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [<span data-ttu-id="380c7-137">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="380c7-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
