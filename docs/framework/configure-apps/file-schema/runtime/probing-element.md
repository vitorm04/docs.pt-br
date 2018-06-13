---
title: '&lt;sondando&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cab16e83466b5954bfebac07dd79c9a8b5e4594
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744997"
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="a1f64-102">&lt;sondando&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="a1f64-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="a1f64-103">Especifica os subdiretórios do aplicativo base para o common language runtime pesquisar durante o carregamento de assemblies.</span><span class="sxs-lookup"><span data-stu-id="a1f64-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="a1f64-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a1f64-104">\<configuration></span></span>  
<span data-ttu-id="a1f64-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="a1f64-105">\<runtime></span></span>  
<span data-ttu-id="a1f64-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="a1f64-106">\<assemblyBinding></span></span>  
<span data-ttu-id="a1f64-107">\<sondando ></span><span class="sxs-lookup"><span data-stu-id="a1f64-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f64-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1f64-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1f64-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a1f64-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a1f64-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a1f64-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1f64-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1f64-111">Attributes</span></span>  
  
|<span data-ttu-id="a1f64-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="a1f64-112">Attribute</span></span>|<span data-ttu-id="a1f64-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1f64-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="a1f64-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a1f64-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a1f64-115">Especifica os subdiretórios do diretório de base do aplicativo que podem conter assemblies.</span><span class="sxs-lookup"><span data-stu-id="a1f64-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="a1f64-116">Delimite cada subpasta com um ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="a1f64-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1f64-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a1f64-117">Child Elements</span></span>  
 <span data-ttu-id="a1f64-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a1f64-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1f64-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a1f64-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a1f64-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1f64-120">Element</span></span>|<span data-ttu-id="a1f64-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1f64-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a1f64-122">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="a1f64-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a1f64-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1f64-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a1f64-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a1f64-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a1f64-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1f64-125">Example</span></span>  
 <span data-ttu-id="a1f64-126">O exemplo a seguir mostra como especificar o tempo de execução deve procurar por assemblies de subdiretórios base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1f64-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1f64-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1f64-127">See Also</span></span>  
 [<span data-ttu-id="a1f64-128">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a1f64-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a1f64-129">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a1f64-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a1f64-130">Especificando o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="a1f64-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="a1f64-131">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="a1f64-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
