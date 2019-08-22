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
ms.openlocfilehash: 851a63b41dfb5d3b4058e1373148f48d47d9d6ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664077"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="4f8f0-102">\<Elemento de > de módulo (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="4f8f0-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="4f8f0-103">Adiciona um novo módulo de proxy ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="4f8f0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4f8f0-104">\<configuration></span></span>  
<span data-ttu-id="4f8f0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4f8f0-105">\<system.net></span></span>  
<span data-ttu-id="4f8f0-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="4f8f0-106">\<defaultProxy></span></span>  
<span data-ttu-id="4f8f0-107">\<> de módulo</span><span class="sxs-lookup"><span data-stu-id="4f8f0-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f8f0-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f8f0-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f8f0-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f8f0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4f8f0-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f8f0-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f8f0-111">Attributes</span></span>  
  
|<span data-ttu-id="4f8f0-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="4f8f0-112">**Attribute**</span></span>|<span data-ttu-id="4f8f0-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4f8f0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="4f8f0-114">O nome do tipo totalmente qualificado (indicado pela <xref:System.Type.FullName%2A> Propriedade) e o nome do assembly (indicado <xref:System.Reflection.Assembly.FullName%2A> pela propriedade), separados por uma vírgula, que implementa o proxy.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f8f0-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f8f0-115">Child Elements</span></span>  
 <span data-ttu-id="4f8f0-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f8f0-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4f8f0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4f8f0-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="4f8f0-118">**Element**</span></span>|<span data-ttu-id="4f8f0-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4f8f0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4f8f0-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="4f8f0-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="4f8f0-121">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="4f8f0-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f8f0-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f8f0-122">Remarks</span></span>  
 <span data-ttu-id="4f8f0-123">O `module` elemento registra as classes proxy que implementam a <xref:System.Net.IWebProxy> interface.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="4f8f0-124">Depois de registrar a classe proxy, `module` o pode ser usado para solicitar informações por meio do proxy com suporte.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="4f8f0-125">O valor do `type` atributo deve ser o nome da classe do módulo e o nome da biblioteca de vínculo dinâmico (DLL) correspondente.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4f8f0-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="4f8f0-126">Configuration Files</span></span>  
 <span data-ttu-id="4f8f0-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="4f8f0-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f8f0-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f8f0-128">Example</span></span>  
 <span data-ttu-id="4f8f0-129">O exemplo a seguir registra uma classe proxy Personalizada.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f8f0-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f8f0-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="4f8f0-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="4f8f0-131">Network Settings Schema</span></span>](index.md)
