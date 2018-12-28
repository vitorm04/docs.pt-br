---
title: '&lt;investigação&gt; elemento'
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
ms.openlocfilehash: a5b9be3050da21c0a99931ca70cf990b0b8bf1fe
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612291"
---
# <a name="ltprobinggt-element"></a><span data-ttu-id="48466-102">&lt;investigação&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="48466-102">&lt;probing&gt; Element</span></span>
<span data-ttu-id="48466-103">Especifica os subdiretórios do aplicativo base para o common language runtime quando o carregamento de assemblies de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="48466-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="48466-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="48466-104">\<configuration></span></span>  
<span data-ttu-id="48466-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="48466-105">\<runtime></span></span>  
<span data-ttu-id="48466-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="48466-106">\<assemblyBinding></span></span>  
<span data-ttu-id="48466-107">\<investigação ></span><span class="sxs-lookup"><span data-stu-id="48466-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48466-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48466-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48466-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="48466-109">Attributes and Elements</span></span>  
 <span data-ttu-id="48466-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="48466-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48466-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="48466-111">Attributes</span></span>  
  
|<span data-ttu-id="48466-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="48466-112">Attribute</span></span>|<span data-ttu-id="48466-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="48466-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="48466-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="48466-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="48466-115">Especifica os subdiretórios do diretório de base do aplicativo que podem conter assemblies.</span><span class="sxs-lookup"><span data-stu-id="48466-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="48466-116">Delimite cada subdiretório com um ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="48466-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48466-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="48466-117">Child Elements</span></span>  
 <span data-ttu-id="48466-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="48466-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48466-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="48466-119">Parent Elements</span></span>  
  
|<span data-ttu-id="48466-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="48466-120">Element</span></span>|<span data-ttu-id="48466-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="48466-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="48466-122">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="48466-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="48466-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48466-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="48466-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="48466-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="48466-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48466-125">Example</span></span>  
 <span data-ttu-id="48466-126">O exemplo a seguir mostra como especificar o tempo de execução deve procurar assemblies de base e subdiretórios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="48466-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48466-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48466-127">See Also</span></span>  
- [<span data-ttu-id="48466-128">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="48466-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="48466-129">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="48466-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="48466-130">Especificando o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="48466-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
- [<span data-ttu-id="48466-131">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="48466-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
