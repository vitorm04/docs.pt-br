---
title: '&lt;módulo&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 06c653d8759224e1112183a7e86e9797a97402af
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753762"
---
# <a name="ltmodulegt-element-network-settings"></a><span data-ttu-id="80ab1-102">&lt;módulo&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="80ab1-102">&lt;module&gt; Element (Network Settings)</span></span>
<span data-ttu-id="80ab1-103">Adiciona um novo módulo de proxy para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80ab1-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="80ab1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="80ab1-104">\<configuration></span></span>  
<span data-ttu-id="80ab1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="80ab1-105">\<system.net></span></span>  
<span data-ttu-id="80ab1-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="80ab1-106">\<defaultProxy></span></span>  
<span data-ttu-id="80ab1-107">\<módulo ></span><span class="sxs-lookup"><span data-stu-id="80ab1-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ab1-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80ab1-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80ab1-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="80ab1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="80ab1-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="80ab1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80ab1-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="80ab1-111">Attributes</span></span>  
  
|<span data-ttu-id="80ab1-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="80ab1-112">**Attribute**</span></span>|<span data-ttu-id="80ab1-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="80ab1-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="80ab1-114">O nome de tipo totalmente qualificado (indicado pelo <xref:System.Type.FullName%2A> propriedade) e o nome do assembly (indicado pelo <xref:System.Reflection.Assembly.FullName%2A> propriedade), separados por uma vírgula, que implementa o proxy.</span><span class="sxs-lookup"><span data-stu-id="80ab1-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80ab1-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="80ab1-115">Child Elements</span></span>  
 <span data-ttu-id="80ab1-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="80ab1-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80ab1-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="80ab1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="80ab1-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="80ab1-118">**Element**</span></span>|<span data-ttu-id="80ab1-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="80ab1-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="80ab1-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="80ab1-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="80ab1-121">Configura o servidor de proxy do protocolo HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="80ab1-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80ab1-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="80ab1-122">Remarks</span></span>  
 <span data-ttu-id="80ab1-123">O `module` elemento registra as classes de proxy que implementam o <xref:System.Net.IWebProxy> interface.</span><span class="sxs-lookup"><span data-stu-id="80ab1-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="80ab1-124">Depois de registrar a classe de proxy, `module` pode ser usado para solicitar informações por meio do proxy com suporte.</span><span class="sxs-lookup"><span data-stu-id="80ab1-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="80ab1-125">O valor para o `type` atributo deve ser o nome da classe do módulo e o nome de seu correspondente dinâmico Link Library (DLL).</span><span class="sxs-lookup"><span data-stu-id="80ab1-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="80ab1-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="80ab1-126">Configuration Files</span></span>  
 <span data-ttu-id="80ab1-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="80ab1-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80ab1-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80ab1-128">Example</span></span>  
 <span data-ttu-id="80ab1-129">O exemplo a seguir registra uma classe de proxy personalizado.</span><span class="sxs-lookup"><span data-stu-id="80ab1-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="80ab1-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80ab1-130">See Also</span></span>  
 <xref:System.Net.IWebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="80ab1-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="80ab1-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
