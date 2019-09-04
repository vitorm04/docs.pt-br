---
title: Elemento <assemblyIdentity> para <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: 7cce12f6fb4b957d740cd590bd84851fa16a117d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252791"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="6e8c7-102">\<elemento de > AssemblyIdentity \<para tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="6e8c7-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="6e8c7-103">Contém informações de identificação sobre o assembly.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-103">Contains identifying information about the assembly.</span></span>  
  
<span data-ttu-id="6e8c7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e8c7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6e8c7-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e8c7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6e8c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> assemblyBinding**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="6e8c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="6e8c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e8c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="6e8c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<assemblyIdentity>**</span><span class="sxs-lookup"><span data-stu-id="6e8c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e8c7-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e8c7-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e8c7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6e8c7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6e8c7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e8c7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6e8c7-112">Attributes</span></span>  
  
|<span data-ttu-id="6e8c7-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="6e8c7-113">Attribute</span></span>|<span data-ttu-id="6e8c7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e8c7-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="6e8c7-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="6e8c7-116">O nome do assembly</span><span class="sxs-lookup"><span data-stu-id="6e8c7-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="6e8c7-117">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6e8c7-118">Uma cadeia de caracteres que especifica o idioma e o país/região do assembly.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="6e8c7-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6e8c7-120">Um valor hexadecimal que especifica o nome forte do assembly.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="6e8c7-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6e8c7-122">Um dos valores "x86", "amd64", "MSIL" ou "IA64", especificando a arquitetura do processador para um assembly que contém código específico do processador.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="6e8c7-123">Os valores não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-123">The values are not case-sensitive.</span></span> <span data-ttu-id="6e8c7-124">Se o atributo for atribuído a qualquer outro valor, todo `<assemblyIdentity>` o elemento será ignorado.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="6e8c7-125">Consulte <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="6e8c7-126">Atributo processorArchitecture</span><span class="sxs-lookup"><span data-stu-id="6e8c7-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="6e8c7-127">Valor</span><span class="sxs-lookup"><span data-stu-id="6e8c7-127">Value</span></span>|<span data-ttu-id="6e8c7-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e8c7-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="6e8c7-129">Somente arquitetura AMD x86-64.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="6e8c7-130">Somente a arquitetura Itanium da Intel.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="6e8c7-131">Neutro em relação ao processador e bits por palavra.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="6e8c7-132">Um processador x86 de 32 bits, nativo ou no ambiente Windows no Windows (WOW) em uma plataforma de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e8c7-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6e8c7-133">Child Elements</span></span>  
 <span data-ttu-id="6e8c7-134">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e8c7-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6e8c7-135">Parent Elements</span></span>  
  
|<span data-ttu-id="6e8c7-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e8c7-136">Element</span></span>|<span data-ttu-id="6e8c7-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e8c7-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="6e8c7-138">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="6e8c7-139">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="6e8c7-140">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="6e8c7-141">Use um `<dependentAssembly>` elemento para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="6e8c7-142">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e8c7-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e8c7-143">Remarks</span></span>  
 <span data-ttu-id="6e8c7-144">**Cada\<elemento de > dependentAssembly** deve ter um  **\<AssemblyIdentity >** elemento filho.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="6e8c7-145">Se o `processorArchitecture` atributo estiver presente, o `<assemblyIdentity>` elemento se aplicará somente ao assembly com a arquitetura de processador correspondente.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="6e8c7-146">Se o `processorArchitecture` atributo não estiver presente, o `<assemblyIdentity>` elemento poderá ser aplicado a um assembly com qualquer arquitetura de processador.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="6e8c7-147">O exemplo a seguir mostra um arquivo de configuração para dois assemblies com o mesmo nome direcionado a duas arquiteturas de processador diferentes, e cujas versões não foram mantidas em sincronia. Quando o aplicativo é executado na plataforma x86, o primeiro `<assemblyIdentity>` elemento se aplica e o outro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="6e8c7-148">Se o aplicativo for executado em uma plataforma diferente de x86 ou ia64, ambos serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="6e8c7-149">Se um arquivo de configuração contiver um `<assemblyIdentity>` elemento `processorArchitecture` sem atributo e não contiver um elemento que corresponda à plataforma, o elemento sem o `processorArchitecture` atributo será usado.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e8c7-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e8c7-150">Example</span></span>  
 <span data-ttu-id="6e8c7-151">O exemplo a seguir mostra como fornecer informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="6e8c7-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e8c7-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e8c7-152">See also</span></span>

- [<span data-ttu-id="6e8c7-153">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6e8c7-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6e8c7-154">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6e8c7-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6e8c7-155">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="6e8c7-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
