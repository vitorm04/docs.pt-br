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
ms.openlocfilehash: 6a924b1998651c923c64429029a118dd1e9ede69
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198997"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="3808f-102">Elemento \<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="3808f-102">\<dependentAssembly> Element</span></span>

<span data-ttu-id="3808f-103">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="3808f-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="3808f-104">Use um `dependentAssembly` elemento para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="3808f-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="3808f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3808f-105">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3808f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3808f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3808f-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3808f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3808f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="3808f-108">Attributes</span></span>  

 <span data-ttu-id="3808f-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3808f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3808f-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3808f-110">Child Elements</span></span>  
  
|<span data-ttu-id="3808f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="3808f-111">Element</span></span>|<span data-ttu-id="3808f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3808f-112">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="3808f-113">Contém informações de identificação sobre o assembly.</span><span class="sxs-lookup"><span data-stu-id="3808f-113">Contains identifying information about the assembly.</span></span> <span data-ttu-id="3808f-114">Esse elemento deve ser incluído em cada `dependentAssembly` elemento.</span><span class="sxs-lookup"><span data-stu-id="3808f-114">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="3808f-115">Especifica onde o tempo de execução pode encontrar um assembly compartilhado se ele não estiver instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="3808f-115">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="3808f-116">Redireciona uma versão do assembly para outra.</span><span class="sxs-lookup"><span data-stu-id="3808f-116">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="3808f-117">Especifica se o tempo de execução aplica a política de Publicador para este assembly.</span><span class="sxs-lookup"><span data-stu-id="3808f-117">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3808f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3808f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3808f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="3808f-119">Element</span></span>|<span data-ttu-id="3808f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3808f-120">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="3808f-121">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="3808f-121">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="3808f-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3808f-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3808f-123">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3808f-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3808f-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3808f-124">Example</span></span>  

 <span data-ttu-id="3808f-125">O exemplo a seguir mostra como encapsular informações de assembly para dois assemblies.</span><span class="sxs-lookup"><span data-stu-id="3808f-125">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3808f-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="3808f-126">See also</span></span>

- [<span data-ttu-id="3808f-127">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="3808f-127">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3808f-128">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="3808f-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3808f-129">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="3808f-129">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
