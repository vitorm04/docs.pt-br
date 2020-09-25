---
title: Elemento <defaultProxy> (Configurações de Rede)
description: O <defaultProxy> elemento de configurações de rede configura o servidor proxy http (Hypertext Transfer Protocol) no .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 806a30a52219ef9185f84a650d6a8eef8fb0dc8c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190300"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="0b6f8-103">Elemento \<defaultProxy> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="0b6f8-103">\<defaultProxy> Element (Network Settings)</span></span>

<span data-ttu-id="0b6f8-104">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="0b6f8-104">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="0b6f8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b6f8-105">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="True|False"  
  useDefaultCredentials="True|False">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b6f8-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0b6f8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0b6f8-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b6f8-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b6f8-108">Attributes</span></span>  
  
|<span data-ttu-id="0b6f8-109">**Element**</span><span class="sxs-lookup"><span data-stu-id="0b6f8-109">**Element**</span></span>|<span data-ttu-id="0b6f8-110">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0b6f8-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="0b6f8-111">Especifica se um proxy Web é usado.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-111">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="0b6f8-112">O valor padrão é `True`.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-112">The default value is `True`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="0b6f8-113">Especifica se as credenciais padrão para este host são usadas para acessar o proxy Web.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-113">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="0b6f8-114">O valor padrão é `False`.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-114">The default value is `False`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b6f8-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0b6f8-115">Child Elements</span></span>  
  
|<span data-ttu-id="0b6f8-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="0b6f8-116">**Element**</span></span>|<span data-ttu-id="0b6f8-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0b6f8-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0b6f8-118">bypasslist</span><span class="sxs-lookup"><span data-stu-id="0b6f8-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="0b6f8-119">Fornece um conjunto de expressões regulares que descrevem endereços que não usam o proxy.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-119">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="0b6f8-120">modulo</span><span class="sxs-lookup"><span data-stu-id="0b6f8-120">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="0b6f8-121">Adiciona um novo módulo de proxy ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-121">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="0b6f8-122">acionista</span><span class="sxs-lookup"><span data-stu-id="0b6f8-122">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="0b6f8-123">Define um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-123">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b6f8-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0b6f8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0b6f8-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="0b6f8-125">**Element**</span></span>|<span data-ttu-id="0b6f8-126">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0b6f8-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0b6f8-127">system.net</span><span class="sxs-lookup"><span data-stu-id="0b6f8-127">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="0b6f8-128">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-128">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b6f8-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b6f8-129">Remarks</span></span>  

 <span data-ttu-id="0b6f8-130">Se o elemento defaultProxy estiver vazio, as configurações de proxy do Internet Explorer serão usadas.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-130">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="0b6f8-131">Esse comportamento é diferente da versão 1,1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-131">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="0b6f8-132">Uma exceção é gerada se o elemento [Module](module-element-network-settings.md) especifica um tipo não público, o tipo não é derivado da <xref:System.Net.IWebProxy> classe, uma exceção do construtor sem parâmetros desse objeto ocorreu ou uma exceção ocorreu ao recuperar o proxy padrão especificado pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-132">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="0b6f8-133">A <xref:System.Exception.InnerException%2A> Propriedade na exceção deve ter mais informações sobre a causa raiz do erro.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-133">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0b6f8-134">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="0b6f8-134">Configuration Files</span></span>  

 <span data-ttu-id="0b6f8-135">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0b6f8-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b6f8-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b6f8-136">Example</span></span>  

 <span data-ttu-id="0b6f8-137">O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignora o proxy para acesso local e contoso.com.</span><span class="sxs-lookup"><span data-stu-id="0b6f8-137">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b6f8-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="0b6f8-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="0b6f8-139">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="0b6f8-139">Network Settings Schema</span></span>](index.md)
