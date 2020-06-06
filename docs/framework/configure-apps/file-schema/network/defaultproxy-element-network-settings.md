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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698204"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="6abd3-102">Elemento \<defaultProxy> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="6abd3-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="6abd3-103">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="6abd3-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="6abd3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6abd3-104">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6abd3-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6abd3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6abd3-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6abd3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6abd3-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="6abd3-107">Attributes</span></span>  
  
|<span data-ttu-id="6abd3-108">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6abd3-108">**Element**</span></span>|<span data-ttu-id="6abd3-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6abd3-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="6abd3-110">Especifica se um proxy Web é usado.</span><span class="sxs-lookup"><span data-stu-id="6abd3-110">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="6abd3-111">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="6abd3-111">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="6abd3-112">Especifica se as credenciais padrão para este host são usadas para acessar o proxy Web.</span><span class="sxs-lookup"><span data-stu-id="6abd3-112">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="6abd3-113">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="6abd3-113">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6abd3-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6abd3-114">Child Elements</span></span>  
  
|<span data-ttu-id="6abd3-115">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6abd3-115">**Element**</span></span>|<span data-ttu-id="6abd3-116">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6abd3-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6abd3-117">bypasslist</span><span class="sxs-lookup"><span data-stu-id="6abd3-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="6abd3-118">Fornece um conjunto de expressões regulares que descrevem endereços que não usam o proxy.</span><span class="sxs-lookup"><span data-stu-id="6abd3-118">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="6abd3-119">modulo</span><span class="sxs-lookup"><span data-stu-id="6abd3-119">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="6abd3-120">Adiciona um novo módulo de proxy ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6abd3-120">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="6abd3-121">proxy</span><span class="sxs-lookup"><span data-stu-id="6abd3-121">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="6abd3-122">Define um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="6abd3-122">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6abd3-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6abd3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6abd3-124">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6abd3-124">**Element**</span></span>|<span data-ttu-id="6abd3-125">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6abd3-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6abd3-126">system.net</span><span class="sxs-lookup"><span data-stu-id="6abd3-126">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="6abd3-127">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="6abd3-127">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6abd3-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="6abd3-128">Remarks</span></span>  
 <span data-ttu-id="6abd3-129">Se o elemento defaultProxy estiver vazio, as configurações de proxy do Internet Explorer serão usadas.</span><span class="sxs-lookup"><span data-stu-id="6abd3-129">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="6abd3-130">Esse comportamento é diferente da versão 1,1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6abd3-130">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="6abd3-131">Uma exceção é gerada se o elemento [Module](module-element-network-settings.md) especifica um tipo não público, o tipo não é derivado da <xref:System.Net.IWebProxy> classe, uma exceção do construtor sem parâmetros desse objeto ocorreu ou uma exceção ocorreu ao recuperar o proxy padrão especificado pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="6abd3-131">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="6abd3-132">A <xref:System.Exception.InnerException%2A> Propriedade na exceção deve ter mais informações sobre a causa raiz do erro.</span><span class="sxs-lookup"><span data-stu-id="6abd3-132">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6abd3-133">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6abd3-133">Configuration Files</span></span>  
 <span data-ttu-id="6abd3-134">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6abd3-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6abd3-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6abd3-135">Example</span></span>  
 <span data-ttu-id="6abd3-136">O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignora o proxy para acesso local e contoso.com.</span><span class="sxs-lookup"><span data-stu-id="6abd3-136">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6abd3-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="6abd3-137">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="6abd3-138">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="6abd3-138">Network Settings Schema</span></span>](index.md)
