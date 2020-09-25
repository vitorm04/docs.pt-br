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
ms.openlocfilehash: ad641f93e93f627dae1c7d0bda4620093c4567b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205042"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="923fe-102">Elemento \<module> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="923fe-102">\<module> Element (Network Settings)</span></span>

<span data-ttu-id="923fe-103">Adiciona um novo módulo de proxy ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="923fe-103">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="923fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="923fe-104">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="923fe-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="923fe-105">Attributes and Elements</span></span>  

 <span data-ttu-id="923fe-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="923fe-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="923fe-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="923fe-107">Attributes</span></span>  
  
|<span data-ttu-id="923fe-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="923fe-108">**Attribute**</span></span>|<span data-ttu-id="923fe-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="923fe-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="923fe-110">O nome do tipo totalmente qualificado (indicado pela <xref:System.Type.FullName%2A> Propriedade) e o nome do assembly (indicado pela <xref:System.Reflection.Assembly.FullName%2A> Propriedade), separados por uma vírgula, que implementa o proxy.</span><span class="sxs-lookup"><span data-stu-id="923fe-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="923fe-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="923fe-111">Child Elements</span></span>  

 <span data-ttu-id="923fe-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="923fe-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="923fe-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="923fe-113">Parent Elements</span></span>  
  
|<span data-ttu-id="923fe-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="923fe-114">**Element**</span></span>|<span data-ttu-id="923fe-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="923fe-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="923fe-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="923fe-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="923fe-117">Configura o servidor proxy HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="923fe-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="923fe-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="923fe-118">Remarks</span></span>  

 <span data-ttu-id="923fe-119">O `module` elemento registra as classes proxy que implementam a <xref:System.Net.IWebProxy> interface.</span><span class="sxs-lookup"><span data-stu-id="923fe-119">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="923fe-120">Depois de registrar a classe proxy, o `module` pode ser usado para solicitar informações por meio do proxy com suporte.</span><span class="sxs-lookup"><span data-stu-id="923fe-120">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="923fe-121">O valor do `type` atributo deve ser o nome da classe do módulo e o nome da biblioteca de vínculo dinâmico (DLL) correspondente.</span><span class="sxs-lookup"><span data-stu-id="923fe-121">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="923fe-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="923fe-122">Configuration Files</span></span>  

 <span data-ttu-id="923fe-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="923fe-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="923fe-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="923fe-124">Example</span></span>  

 <span data-ttu-id="923fe-125">O exemplo a seguir registra uma classe proxy Personalizada.</span><span class="sxs-lookup"><span data-stu-id="923fe-125">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="923fe-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="923fe-126">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="923fe-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="923fe-127">Network Settings Schema</span></span>](index.md)
