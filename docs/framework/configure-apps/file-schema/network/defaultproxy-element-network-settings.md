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
ms.openlocfilehash: 0945629c1395917bc1cf825f2ba84d20afa99957
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698204"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="603b3-102">Elemento \<defaultProxy > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="603b3-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="603b3-103">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="603b3-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[<span data-ttu-id="603b3-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="603b3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="603b3-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="603b3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="603b3-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultProxy >**</span><span class="sxs-lookup"><span data-stu-id="603b3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="603b3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="603b3-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="603b3-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="603b3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="603b3-109">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="603b3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="603b3-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="603b3-110">Attributes</span></span>  
  
|<span data-ttu-id="603b3-111">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="603b3-111">**Element**</span></span>|<span data-ttu-id="603b3-112">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="603b3-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="603b3-113">Especifica se um proxy Web é usado.</span><span class="sxs-lookup"><span data-stu-id="603b3-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="603b3-114">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="603b3-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="603b3-115">Especifica se as credenciais padrão para este host são usadas para acessar o proxy Web.</span><span class="sxs-lookup"><span data-stu-id="603b3-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="603b3-116">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="603b3-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="603b3-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="603b3-117">Child Elements</span></span>  
  
|<span data-ttu-id="603b3-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="603b3-118">**Element**</span></span>|<span data-ttu-id="603b3-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="603b3-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="603b3-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="603b3-120">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="603b3-121">Fornece um conjunto de expressões regulares que descrevem endereços que não usam o proxy.</span><span class="sxs-lookup"><span data-stu-id="603b3-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="603b3-122">module</span><span class="sxs-lookup"><span data-stu-id="603b3-122">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="603b3-123">Adiciona um novo módulo de proxy ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="603b3-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="603b3-124">acionista</span><span class="sxs-lookup"><span data-stu-id="603b3-124">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="603b3-125">Define um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="603b3-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="603b3-126">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="603b3-126">Parent Elements</span></span>  
  
|<span data-ttu-id="603b3-127">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="603b3-127">**Element**</span></span>|<span data-ttu-id="603b3-128">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="603b3-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="603b3-129">system.net</span><span class="sxs-lookup"><span data-stu-id="603b3-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="603b3-130">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="603b3-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="603b3-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="603b3-131">Remarks</span></span>  
 <span data-ttu-id="603b3-132">Se o elemento defaultProxy estiver vazio, as configurações de proxy do Internet Explorer serão usadas.</span><span class="sxs-lookup"><span data-stu-id="603b3-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="603b3-133">Esse comportamento é diferente da versão 1,1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="603b3-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="603b3-134">Uma exceção é gerada se o elemento [Module](module-element-network-settings.md) especifica um tipo não público, o tipo não é derivado da classe <xref:System.Net.IWebProxy>, uma exceção do construtor sem parâmetros desse objeto ocorreu ou ocorreu uma exceção ao recuperar o proxy padrão especificado pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="603b3-134">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="603b3-135">A propriedade <xref:System.Exception.InnerException%2A> na exceção deve ter mais informações sobre a causa raiz do erro.</span><span class="sxs-lookup"><span data-stu-id="603b3-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="603b3-136">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="603b3-136">Configuration Files</span></span>  
 <span data-ttu-id="603b3-137">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="603b3-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="603b3-138">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="603b3-138">Example</span></span>  
 <span data-ttu-id="603b3-139">O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignora o proxy para acesso local e contoso.com.</span><span class="sxs-lookup"><span data-stu-id="603b3-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="603b3-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="603b3-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="603b3-141">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="603b3-141">Network Settings Schema</span></span>](index.md)
