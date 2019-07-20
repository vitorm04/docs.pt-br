---
title: Elemento <defaultProxy> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 5947808cd137fc4cd280ac683a3e9a14b0d4644d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363868"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="a4137-102">\<Elemento de > de defaultProxy (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="a4137-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="a4137-103">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="a4137-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="a4137-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a4137-104">\<configuration></span></span>  
<span data-ttu-id="a4137-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a4137-105">\<system.net></span></span>  
<span data-ttu-id="a4137-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="a4137-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4137-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4137-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4137-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a4137-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a4137-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a4137-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4137-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a4137-110">Attributes</span></span>  
  
|<span data-ttu-id="a4137-111">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a4137-111">**Element**</span></span>|<span data-ttu-id="a4137-112">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a4137-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="a4137-113">Especifica se um proxy Web é usado.</span><span class="sxs-lookup"><span data-stu-id="a4137-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="a4137-114">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="a4137-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="a4137-115">Especifica se as credenciais padrão para este host são usadas para acessar o proxy Web.</span><span class="sxs-lookup"><span data-stu-id="a4137-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="a4137-116">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="a4137-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4137-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a4137-117">Child Elements</span></span>  
  
|<span data-ttu-id="a4137-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a4137-118">**Element**</span></span>|<span data-ttu-id="a4137-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a4137-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a4137-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="a4137-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="a4137-121">Fornece um conjunto de expressões regulares que descrevem endereços que não usam o proxy.</span><span class="sxs-lookup"><span data-stu-id="a4137-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="a4137-122">module</span><span class="sxs-lookup"><span data-stu-id="a4137-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="a4137-123">Adiciona um novo módulo de proxy ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a4137-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="a4137-124">acionista</span><span class="sxs-lookup"><span data-stu-id="a4137-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="a4137-125">Define um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="a4137-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4137-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a4137-126">Parent Elements</span></span>  
  
|<span data-ttu-id="a4137-127">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a4137-127">**Element**</span></span>|<span data-ttu-id="a4137-128">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a4137-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a4137-129">system.net</span><span class="sxs-lookup"><span data-stu-id="a4137-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="a4137-130">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="a4137-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4137-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4137-131">Remarks</span></span>  
 <span data-ttu-id="a4137-132">Se o elemento defaultProxy estiver vazio, as configurações de proxy do Internet Explorer serão usadas.</span><span class="sxs-lookup"><span data-stu-id="a4137-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="a4137-133">Esse comportamento é diferente da versão 1,1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4137-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a4137-134">Uma exceção é gerada se o elemento [Module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) especifica um tipo não público, o tipo não é derivado da <xref:System.Net.IWebProxy> classe, uma exceção do construtor sem parâmetros desse objeto ocorreu ou ocorreu uma exceção ao recuperar o proxy padrão especificado pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="a4137-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="a4137-135">A <xref:System.Exception.InnerException%2A> Propriedade na exceção deve ter mais informações sobre a causa raiz do erro.</span><span class="sxs-lookup"><span data-stu-id="a4137-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a4137-136">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="a4137-136">Configuration Files</span></span>  
 <span data-ttu-id="a4137-137">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a4137-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4137-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4137-138">Example</span></span>  
 <span data-ttu-id="a4137-139">O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignora o proxy para acesso local e contoso.com.</span><span class="sxs-lookup"><span data-stu-id="a4137-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4137-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4137-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a4137-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="a4137-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
