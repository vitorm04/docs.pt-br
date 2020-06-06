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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154537"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="e1d9e-102">Elemento \<webRequestModules> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="e1d9e-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="e1d9e-103">Especifica os módulos a serem usados para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a><span data-ttu-id="e1d9e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1d9e-104">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1d9e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e1d9e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e1d9e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1d9e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1d9e-107">Attributes</span></span>  
 <span data-ttu-id="e1d9e-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1d9e-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e1d9e-109">Child Elements</span></span>  
  
|<span data-ttu-id="e1d9e-110">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e1d9e-110">**Element**</span></span>|<span data-ttu-id="e1d9e-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e1d9e-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e1d9e-112">adicionar</span><span class="sxs-lookup"><span data-stu-id="e1d9e-112">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="e1d9e-113">Adiciona um módulo de solicitação da Web personalizado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-113">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="e1d9e-114">formatação</span><span class="sxs-lookup"><span data-stu-id="e1d9e-114">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="e1d9e-115">Remove todos os módulos de solicitação da Web registrados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-115">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="e1d9e-116">remove</span><span class="sxs-lookup"><span data-stu-id="e1d9e-116">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="e1d9e-117">Remove um módulo de solicitação da Web personalizado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-117">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1d9e-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e1d9e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e1d9e-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e1d9e-119">**Element**</span></span>|<span data-ttu-id="e1d9e-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e1d9e-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e1d9e-121">system.net</span><span class="sxs-lookup"><span data-stu-id="e1d9e-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="e1d9e-122">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1d9e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1d9e-123">Remarks</span></span>  
 <span data-ttu-id="e1d9e-124">O `webRequestModules` elemento registra os descendentes da <xref:System.Net.WebRequest> classe para tratar as solicitações de informações para os hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-124">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="e1d9e-125">Os módulos de solicitação da Web devem implementar a <xref:System.Net.IWebRequestCreate> interface.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-125">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="e1d9e-126">O .NET Framework inclui módulos de solicitação da Web para URIs que começam com `http://` , `https://` e `file://` .</span><span class="sxs-lookup"><span data-stu-id="e1d9e-126">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="e1d9e-127">Você pode substituir os módulos padrão somente registrando um módulo personalizado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-127">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e1d9e-128">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="e1d9e-128">Configuration Files</span></span>  
 <span data-ttu-id="e1d9e-129">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e1d9e-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1d9e-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1d9e-130">Example</span></span>  
 <span data-ttu-id="e1d9e-131">O exemplo a seguir registra o módulo HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-131">The following example registers the default HTTP module.</span></span> <span data-ttu-id="e1d9e-132">Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1d9e-132">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1d9e-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="e1d9e-133">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="e1d9e-134">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e1d9e-134">Network Settings Schema</span></span>](index.md)
