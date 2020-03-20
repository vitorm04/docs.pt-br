---
title: Elemento <dependentAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
ms.openlocfilehash: 2de8c752867d00708173d11d1851f415a2e8518d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154199"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="d7bcc-102">\<dependenteElemento> montagem</span><span class="sxs-lookup"><span data-stu-id="d7bcc-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="d7bcc-103">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="d7bcc-104">Use `dependentAssembly` um elemento para cada montagem.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
<span data-ttu-id="d7bcc-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7bcc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d7bcc-106">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7bcc-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d7bcc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<montagem>vinculante**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="d7bcc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="d7bcc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependente>de montagem**</span><span class="sxs-lookup"><span data-stu-id="d7bcc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7bcc-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7bcc-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7bcc-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d7bcc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d7bcc-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7bcc-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d7bcc-112">Attributes</span></span>  
 <span data-ttu-id="d7bcc-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7bcc-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d7bcc-114">Child Elements</span></span>  
  
|<span data-ttu-id="d7bcc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7bcc-115">Element</span></span>|<span data-ttu-id="d7bcc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7bcc-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="d7bcc-117">Contém informações de identificação sobre a montagem.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="d7bcc-118">Este elemento deve ser `dependentAssembly` incluído em cada elemento.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="d7bcc-119">Especifica onde o tempo de execução pode encontrar um conjunto compartilhado se ele não estiver instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="d7bcc-120">Redireciona uma versão do assembly para outra.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="d7bcc-121">Especifica se o tempo de execução aplica a política do editor para esta montagem.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7bcc-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d7bcc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d7bcc-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7bcc-123">Element</span></span>|<span data-ttu-id="d7bcc-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7bcc-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="d7bcc-125">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="d7bcc-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d7bcc-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d7bcc-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7bcc-128">Example</span></span>  
 <span data-ttu-id="d7bcc-129">O exemplo a seguir mostra como encapsular as informações de montagem para duas assembléias.</span><span class="sxs-lookup"><span data-stu-id="d7bcc-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7bcc-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="d7bcc-130">See also</span></span>

- [<span data-ttu-id="d7bcc-131">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="d7bcc-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d7bcc-132">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="d7bcc-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d7bcc-133">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="d7bcc-133">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
