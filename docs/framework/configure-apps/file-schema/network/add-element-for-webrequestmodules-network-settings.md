---
title: Elemento <add> para webRequestModules (Configurações de Rede)
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
ms.openlocfilehash: 76dad0c0b75d20627e9f57fd1bb467bf17c9294c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088510"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="04c1a-102">\<adicionar o elemento > para webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="04c1a-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="04c1a-103">Adiciona um módulo de solicitação da Web personalizado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04c1a-103">Adds a custom Web request module to the application.</span></span>  

<span data-ttu-id="04c1a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="04c1a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="04c1a-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="04c1a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="04c1a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="04c1a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="04c1a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**adicionar >**</span><span class="sxs-lookup"><span data-stu-id="04c1a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="04c1a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04c1a-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04c1a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="04c1a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="04c1a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="04c1a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04c1a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="04c1a-111">Attributes</span></span>  
  
|<span data-ttu-id="04c1a-112">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="04c1a-112">**Attribute**</span></span>|<span data-ttu-id="04c1a-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="04c1a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="04c1a-114">O prefixo de URI para solicitações tratadas por este módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="04c1a-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="04c1a-115">O nome do tipo totalmente qualificado (indicado pela propriedade <xref:System.Type.FullName%2A>) e o nome do assembly (indicado pela propriedade <xref:System.Reflection.Assembly.FullName%2A>), separados por uma vírgula, que implementa esse módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="04c1a-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04c1a-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="04c1a-116">Child Elements</span></span>  
 <span data-ttu-id="04c1a-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="04c1a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04c1a-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="04c1a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="04c1a-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="04c1a-119">**Element**</span></span>|<span data-ttu-id="04c1a-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="04c1a-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="04c1a-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="04c1a-121">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="04c1a-122">Especifica os módulos a serem usados para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="04c1a-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04c1a-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="04c1a-123">Remarks</span></span>  
 <span data-ttu-id="04c1a-124">O atributo `prefix` define o prefixo de URI que usa o módulo de solicitação da Web especificado.</span><span class="sxs-lookup"><span data-stu-id="04c1a-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="04c1a-125">Os módulos de solicitação da Web normalmente são registrados para lidar com um protocolo específico, como HTTP ou FTP, mas podem ser registrados para lidar com uma solicitação para um servidor ou caminho específico em um servidor.</span><span class="sxs-lookup"><span data-stu-id="04c1a-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="04c1a-126">O módulo de solicitação da Web é criado quando um prefixo de correspondência de URI é passado para o método <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04c1a-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="04c1a-127">O valor para o atributo `prefix` deve ser os caracteres à esquerda de um URI válido.</span><span class="sxs-lookup"><span data-stu-id="04c1a-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="04c1a-128">Por exemplo `http` ou `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="04c1a-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="04c1a-129">O valor para o atributo `type` deve ser um nome de tipo válido e um nome de assembly correspondente, separados por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="04c1a-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="04c1a-130">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="04c1a-130">Configuration Files</span></span>  
 <span data-ttu-id="04c1a-131">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="04c1a-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04c1a-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04c1a-132">Example</span></span>  
 <span data-ttu-id="04c1a-133">O exemplo a seguir registra um módulo de solicitação da Web personalizado para HTTP.</span><span class="sxs-lookup"><span data-stu-id="04c1a-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="04c1a-134">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="04c1a-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04c1a-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04c1a-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="04c1a-136">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="04c1a-136">Network Settings Schema</span></span>](index.md)
