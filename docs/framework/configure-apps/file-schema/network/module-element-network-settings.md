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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154823"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="d6e9e-102">Elemento \<module> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="d6e9e-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="d6e9e-103">Adiciona um novo módulo de proxy ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d6e9e-103">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="d6e9e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6e9e-104">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6e9e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d6e9e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d6e9e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d6e9e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6e9e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6e9e-107">Attributes</span></span>  
  
|<span data-ttu-id="d6e9e-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="d6e9e-108">**Attribute**</span></span>|<span data-ttu-id="d6e9e-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d6e9e-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="d6e9e-110">O nome do tipo totalmente qualificado (indicado pela <xref:System.Type.FullName%2A> Propriedade) e o nome do assembly (indicado pela <xref:System.Reflection.Assembly.FullName%2A> Propriedade), separados por uma vírgula, que implementa o proxy.</span><span class="sxs-lookup"><span data-stu-id="d6e9e-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6e9e-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d6e9e-111">Child Elements</span></span>  
 <span data-ttu-id="d6e9e-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d6e9e-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6e9e-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d6e9e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d6e9e-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d6e9e-114">**Element**</span></span>|<span data-ttu-id="d6e9e-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d6e9e-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d6e9e-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="d6e9e-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="d6e9e-117">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="d6e9e-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6e9e-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6e9e-118">Remarks</span></span>  
 <span data-ttu-id="d6e9e-119">O `module` elemento registra as classes proxy que implementam a <xref:System.Net.IWebProxy> interface.</span><span class="sxs-lookup"><span data-stu-id="d6e9e-119">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="d6e9e-120">Depois de registrar a classe proxy, o `module` pode ser usado para solicitar informações por meio do proxy com suporte.</span><span class="sxs-lookup"><span data-stu-id="d6e9e-120">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="d6e9e-121">O valor do `type` atributo deve ser o nome da classe do módulo e o nome da biblioteca de vínculo dinâmico (DLL) correspondente.</span><span class="sxs-lookup"><span data-stu-id="d6e9e-121">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d6e9e-122">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="d6e9e-122">Configuration Files</span></span>  
 <span data-ttu-id="d6e9e-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="d6e9e-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6e9e-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6e9e-124">Example</span></span>  
 <span data-ttu-id="d6e9e-125">O exemplo a seguir registra uma classe proxy Personalizada.</span><span class="sxs-lookup"><span data-stu-id="d6e9e-125">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6e9e-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="d6e9e-126">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="d6e9e-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="d6e9e-127">Network Settings Schema</span></span>](index.md)
