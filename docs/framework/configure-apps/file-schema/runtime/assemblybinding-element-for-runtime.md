---
title: "&lt;assemblyBinding&gt; elemento para &lt;tempo de execução&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d5ef09f5d7b2dce366c605c8d8f4e6c456920b35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a><span data-ttu-id="704dd-102">&lt;assemblyBinding&gt; elemento para &lt;tempo de execução&gt;</span><span class="sxs-lookup"><span data-stu-id="704dd-102">&lt;assemblyBinding&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="704dd-103">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="704dd-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
 <span data-ttu-id="704dd-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="704dd-104">\<configuration></span></span>  
<span data-ttu-id="704dd-105">\<tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="704dd-105">\<runtime></span></span>  
<span data-ttu-id="704dd-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="704dd-106">\<assemblyBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="704dd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="704dd-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="704dd-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="704dd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="704dd-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="704dd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="704dd-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="704dd-110">Attributes</span></span>  
  
|<span data-ttu-id="704dd-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="704dd-111">Attribute</span></span>|<span data-ttu-id="704dd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="704dd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="704dd-113">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="704dd-113">**xmlns**</span></span>|<span data-ttu-id="704dd-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="704dd-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="704dd-115">Especifica o namespace XML necessário para a associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="704dd-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="704dd-116">Use a cadeia de caracteres "urn: schemas-microsoft-v1" como o valor.</span><span class="sxs-lookup"><span data-stu-id="704dd-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="704dd-117">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="704dd-117">**appliesTo**</span></span>|<span data-ttu-id="704dd-118">Especifica a versão de tempo de execução que se aplica o redirecionamento de assembly do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="704dd-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="704dd-119">Esse atributo opcional usa um número de versão do .NET Framework para indicar qual versão aplica-se a.</span><span class="sxs-lookup"><span data-stu-id="704dd-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="704dd-120">Se nenhum atributo **appliesTo** for especificado, o elemento **\<assemblyBinding>** se aplica a todas as versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="704dd-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="704dd-121">O **appliesTo** atributo foi introduzido no .NET Framework versão 1.1; ele será ignorado pelo .NET Framework versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="704dd-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="704dd-122">Isso significa que todos os elementos **\<assemblyBinding>** são aplicados ao usar o .NET Framework versão 1.0, mesmo se um atributo **appliesTo** for especificado.</span><span class="sxs-lookup"><span data-stu-id="704dd-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="704dd-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="704dd-123">Child Elements</span></span>  
  
|<span data-ttu-id="704dd-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="704dd-124">Element</span></span>|<span data-ttu-id="704dd-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="704dd-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="704dd-126">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="704dd-126">\<dependentAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|<span data-ttu-id="704dd-127">Encapsula o local de assembly e política de associação para um assembly.</span><span class="sxs-lookup"><span data-stu-id="704dd-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="704dd-128">Use um  **\<dependentAssembly >** marca para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="704dd-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="704dd-129">\<probing></span><span class="sxs-lookup"><span data-stu-id="704dd-129">\<probing></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|<span data-ttu-id="704dd-130">Especifica os subdiretórios do common language runtime procura ao carregar assemblies.</span><span class="sxs-lookup"><span data-stu-id="704dd-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="704dd-131">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="704dd-131">\<publisherPolicy></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|<span data-ttu-id="704dd-132">Especifica se o tempo de execução aplica a política do editor.</span><span class="sxs-lookup"><span data-stu-id="704dd-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="704dd-133">\<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="704dd-133">\<qualifyAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|<span data-ttu-id="704dd-134">Especifica o nome completo do assembly que deve ser carregado dinamicamente quando um nome parcial é usado.</span><span class="sxs-lookup"><span data-stu-id="704dd-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="704dd-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="704dd-135">Parent Elements</span></span>  
  
|<span data-ttu-id="704dd-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="704dd-136">Element</span></span>|<span data-ttu-id="704dd-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="704dd-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="704dd-138">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="704dd-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="704dd-139">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="704dd-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="704dd-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="704dd-140">Example</span></span>  
 <span data-ttu-id="704dd-141">O exemplo a seguir mostra como redirecionar uma versão de assembly para outro e fornecer uma base de código.</span><span class="sxs-lookup"><span data-stu-id="704dd-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="704dd-142">O exemplo a seguir mostra como usar o **appliesTo** atributo para redirecionar a associação de um assembly do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="704dd-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="704dd-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="704dd-143">See Also</span></span>  
 [<span data-ttu-id="704dd-144">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="704dd-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="704dd-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="704dd-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="704dd-146">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="704dd-146">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
