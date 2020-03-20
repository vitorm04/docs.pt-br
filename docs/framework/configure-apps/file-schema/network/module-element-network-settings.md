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
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154823"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="17e55-102">\<módulo> Element (Configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="17e55-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="17e55-103">Adiciona um novo módulo proxy ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17e55-103">Adds a new proxy module to the application.</span></span>  

<span data-ttu-id="17e55-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="17e55-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="17e55-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="17e55-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="17e55-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de proxy padrão**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="17e55-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="17e55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<módulo>**</span><span class="sxs-lookup"><span data-stu-id="17e55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span></span>

## <a name="syntax"></a><span data-ttu-id="17e55-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17e55-108">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17e55-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="17e55-109">Attributes and Elements</span></span>  
 <span data-ttu-id="17e55-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="17e55-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17e55-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="17e55-111">Attributes</span></span>  
  
|<span data-ttu-id="17e55-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="17e55-112">**Attribute**</span></span>|<span data-ttu-id="17e55-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="17e55-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="17e55-114">O nome do tipo totalmente <xref:System.Type.FullName%2A> qualificado (indicado pela propriedade) e <xref:System.Reflection.Assembly.FullName%2A> o nome de montagem (indicado pela propriedade), separados por uma comma, que implementa o proxy.</span><span class="sxs-lookup"><span data-stu-id="17e55-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17e55-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="17e55-115">Child Elements</span></span>  
 <span data-ttu-id="17e55-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="17e55-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17e55-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="17e55-117">Parent Elements</span></span>  
  
|<span data-ttu-id="17e55-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="17e55-118">**Element**</span></span>|<span data-ttu-id="17e55-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="17e55-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="17e55-120">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="17e55-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="17e55-121">Configura o servidor proxy Hypertext Transfer Protocol (HTTP).</span><span class="sxs-lookup"><span data-stu-id="17e55-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17e55-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="17e55-122">Remarks</span></span>  
 <span data-ttu-id="17e55-123">O `module` elemento registra classes proxy <xref:System.Net.IWebProxy> que implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="17e55-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="17e55-124">Depois de registrar a `module` classe proxy, pode ser usado para solicitar informações através do proxy suportado.</span><span class="sxs-lookup"><span data-stu-id="17e55-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="17e55-125">O valor `type` para o atributo deve ser o nome da classe do módulo e o nome de sua Biblioteca de Link Dinâmico correspondente (DLL).</span><span class="sxs-lookup"><span data-stu-id="17e55-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="17e55-126">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="17e55-126">Configuration Files</span></span>  
 <span data-ttu-id="17e55-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="17e55-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17e55-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17e55-128">Example</span></span>  
 <span data-ttu-id="17e55-129">O exemplo a seguir registra uma classe proxy personalizada.</span><span class="sxs-lookup"><span data-stu-id="17e55-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17e55-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="17e55-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="17e55-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="17e55-131">Network Settings Schema</span></span>](index.md)
