---
title: Elemento <webRequestModules> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154537"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="b3c63-102">\<webRequestModules> Element (Network Settings) [Elemento webRequestModules> (configurações de rede)]</span><span class="sxs-lookup"><span data-stu-id="b3c63-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="b3c63-103">Especifica módulos a serem usados para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="b3c63-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[<span data-ttu-id="b3c63-104">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="b3c63-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b3c63-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b3c63-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="b3c63-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="b3c63-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c63-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3c63-107">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3c63-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b3c63-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b3c63-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b3c63-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3c63-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b3c63-110">Attributes</span></span>  
 <span data-ttu-id="b3c63-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b3c63-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b3c63-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b3c63-112">Child Elements</span></span>  
  
|<span data-ttu-id="b3c63-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="b3c63-113">**Element**</span></span>|<span data-ttu-id="b3c63-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b3c63-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b3c63-115">adicionar</span><span class="sxs-lookup"><span data-stu-id="b3c63-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="b3c63-116">Adiciona um módulo de solicitação web personalizado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3c63-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="b3c63-117">Claro</span><span class="sxs-lookup"><span data-stu-id="b3c63-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="b3c63-118">Remove todos os módulos de solicitação da Web registrados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3c63-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="b3c63-119">remover</span><span class="sxs-lookup"><span data-stu-id="b3c63-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="b3c63-120">Remove um módulo de solicitação web personalizado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3c63-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3c63-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b3c63-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b3c63-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="b3c63-122">**Element**</span></span>|<span data-ttu-id="b3c63-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b3c63-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b3c63-124">system.net</span><span class="sxs-lookup"><span data-stu-id="b3c63-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b3c63-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="b3c63-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3c63-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3c63-126">Remarks</span></span>  
 <span data-ttu-id="b3c63-127">O `webRequestModules` elemento registra descendentes <xref:System.Net.WebRequest> da classe para lidar com solicitações de informações para hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="b3c63-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="b3c63-128">Os módulos de <xref:System.Net.IWebRequestCreate> solicitação da Web devem implementar a interface.</span><span class="sxs-lookup"><span data-stu-id="b3c63-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="b3c63-129">O .NET Framework inclui módulos de solicitação `http://`da `https://`Web `file://`para URIs que começam com , e .</span><span class="sxs-lookup"><span data-stu-id="b3c63-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="b3c63-130">Você pode substituir os módulos padrão apenas registrando um módulo personalizado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b3c63-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b3c63-131">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="b3c63-131">Configuration Files</span></span>  
 <span data-ttu-id="b3c63-132">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b3c63-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3c63-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3c63-133">Example</span></span>  
 <span data-ttu-id="b3c63-134">O exemplo a seguir registra o módulo HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="b3c63-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="b3c63-135">Você deve substituir os valores de Versão e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="b3c63-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3c63-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3c63-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="b3c63-137">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="b3c63-137">Network Settings Schema</span></span>](index.md)
