---
title: Elemento <module> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: 78f6418160b80096214c6e37268a5a90498d6d4d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089249"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="7f22e-102">Elemento de > do módulo \<(configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="7f22e-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="7f22e-103">Adiciona um novo módulo de proxy ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7f22e-103">Adds a new proxy module to the application.</span></span>  

<span data-ttu-id="7f22e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7f22e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7f22e-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7f22e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="7f22e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7f22e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="7f22e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**módulo** ></span><span class="sxs-lookup"><span data-stu-id="7f22e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7f22e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f22e-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f22e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7f22e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7f22e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7f22e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f22e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="7f22e-111">Attributes</span></span>  
  
|<span data-ttu-id="7f22e-112">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="7f22e-112">**Attribute**</span></span>|<span data-ttu-id="7f22e-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="7f22e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="7f22e-114">O nome do tipo totalmente qualificado (indicado pela propriedade <xref:System.Type.FullName%2A>) e o nome do assembly (indicado pela propriedade <xref:System.Reflection.Assembly.FullName%2A>), separados por uma vírgula, que implementa o proxy.</span><span class="sxs-lookup"><span data-stu-id="7f22e-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f22e-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7f22e-115">Child Elements</span></span>  
 <span data-ttu-id="7f22e-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7f22e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f22e-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7f22e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7f22e-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="7f22e-118">**Element**</span></span>|<span data-ttu-id="7f22e-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="7f22e-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7f22e-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="7f22e-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="7f22e-121">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="7f22e-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f22e-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f22e-122">Remarks</span></span>  
 <span data-ttu-id="7f22e-123">O elemento `module` registra as classes proxy que implementam a interface <xref:System.Net.IWebProxy>.</span><span class="sxs-lookup"><span data-stu-id="7f22e-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="7f22e-124">Depois de registrar a classe proxy, `module` pode ser usada para solicitar informações por meio do proxy com suporte.</span><span class="sxs-lookup"><span data-stu-id="7f22e-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="7f22e-125">O valor do atributo `type` deve ser o nome da classe do módulo e o nome da biblioteca de vínculo dinâmico (DLL) correspondente.</span><span class="sxs-lookup"><span data-stu-id="7f22e-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7f22e-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="7f22e-126">Configuration Files</span></span>  
 <span data-ttu-id="7f22e-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="7f22e-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f22e-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f22e-128">Example</span></span>  
 <span data-ttu-id="7f22e-129">O exemplo a seguir registra uma classe proxy Personalizada.</span><span class="sxs-lookup"><span data-stu-id="7f22e-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f22e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f22e-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="7f22e-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="7f22e-131">Network Settings Schema</span></span>](index.md)
