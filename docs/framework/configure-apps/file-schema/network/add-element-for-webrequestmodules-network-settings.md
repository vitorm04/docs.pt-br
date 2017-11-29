---
title: "&lt;Adicionar&gt; elemento webRequestModules (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fd407f77e75bce4bdbc37acd5f28bbe39f92d564
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="2d4c1-102">&lt;Adicionar&gt; elemento webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="2d4c1-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="2d4c1-103">Adiciona um módulo de solicitação da Web personalizado para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="2d4c1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2d4c1-104">\<configuration></span></span>  
<span data-ttu-id="2d4c1-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="2d4c1-105">\<system.net></span></span>  
<span data-ttu-id="2d4c1-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="2d4c1-106">\<webRequestModules></span></span>  
<span data-ttu-id="2d4c1-107">\<add></span><span class="sxs-lookup"><span data-stu-id="2d4c1-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d4c1-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d4c1-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d4c1-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2d4c1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2d4c1-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d4c1-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2d4c1-111">Attributes</span></span>  
  
|<span data-ttu-id="2d4c1-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="2d4c1-112">**Attribute**</span></span>|<span data-ttu-id="2d4c1-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2d4c1-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="2d4c1-114">O prefixo do URI para solicitações tratadas por este módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="2d4c1-115">O nome de tipo totalmente qualificado (indicado pelo <xref:System.Type.FullName%2A> propriedade) e o nome do assembly (indicado pelo <xref:System.Reflection.Assembly.FullName%2A> propriedade), separados por uma vírgula, que implementa este módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d4c1-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2d4c1-116">Child Elements</span></span>  
 <span data-ttu-id="2d4c1-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d4c1-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2d4c1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2d4c1-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2d4c1-119">**Element**</span></span>|<span data-ttu-id="2d4c1-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2d4c1-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2d4c1-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="2d4c1-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="2d4c1-122">Especifica módulos a ser usado para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d4c1-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d4c1-123">Remarks</span></span>  
 <span data-ttu-id="2d4c1-124">O `prefix` atributo define o prefixo URI que usa o módulo de solicitação da Web especificado.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="2d4c1-125">Módulos de solicitação da Web geralmente são registrados para lidar com um protocolo específico, como HTTP ou FTP, mas podem ser registrados para manipular uma solicitação para um servidor específico ou em um servidor.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="2d4c1-126">O módulo de solicitação da Web é criado quando um correspondência de prefixo do URI é passado para o <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="2d4c1-127">O valor para o `prefix` atributo deve ser os caracteres à esquerda de um URI válido – por exemplo, "http" ou "http://www.contoso.com".</span><span class="sxs-lookup"><span data-stu-id="2d4c1-127">The value for the `prefix` attribute should be the leading characters of a valid URI --for example, "http", or "http://www.contoso.com".</span></span>  
  
 <span data-ttu-id="2d4c1-128">O valor para o `type` atributo deve ser um nome de tipo válido e o nome de assembly correspondente, separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-128">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma .</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2d4c1-129">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="2d4c1-129">Configuration Files</span></span>  
 <span data-ttu-id="2d4c1-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2d4c1-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d4c1-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d4c1-131">Example</span></span>  
 <span data-ttu-id="2d4c1-132">O exemplo a seguir registra um módulo de solicitação da Web personalizado para HTTP.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-132">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="2d4c1-133">Você deve substituir os valores de versão e PublicKeyToken com os valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="2d4c1-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d4c1-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d4c1-134">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="2d4c1-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="2d4c1-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
