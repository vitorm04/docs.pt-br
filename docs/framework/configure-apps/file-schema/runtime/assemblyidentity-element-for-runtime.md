---
title: '&lt;assemblyIdentity&gt; elemento para &lt;tempo de execução&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5d985d1620b7dec324c0113bcd5652cede044950
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a><span data-ttu-id="a43d8-102">&lt;assemblyIdentity&gt; elemento para &lt;tempo de execução&gt;</span><span class="sxs-lookup"><span data-stu-id="a43d8-102">&lt;assemblyIdentity&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="a43d8-103">Contém informações de identificação sobre o assembly.</span><span class="sxs-lookup"><span data-stu-id="a43d8-103">Contains identifying information about the assembly.</span></span>  
  
 <span data-ttu-id="a43d8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a43d8-104">\<configuration></span></span>  
<span data-ttu-id="a43d8-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="a43d8-105">\<runtime></span></span>  
<span data-ttu-id="a43d8-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="a43d8-106">\<assemblyBinding></span></span>  
<span data-ttu-id="a43d8-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="a43d8-107">\<dependentAssembly></span></span>  
<span data-ttu-id="a43d8-108">\<assemblyIdentity ></span><span class="sxs-lookup"><span data-stu-id="a43d8-108">\<assemblyIdentity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a43d8-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a43d8-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a43d8-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a43d8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a43d8-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a43d8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a43d8-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a43d8-112">Attributes</span></span>  
  
|<span data-ttu-id="a43d8-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a43d8-113">Attribute</span></span>|<span data-ttu-id="a43d8-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a43d8-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a43d8-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a43d8-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="a43d8-116">O nome do assembly</span><span class="sxs-lookup"><span data-stu-id="a43d8-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="a43d8-117">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a43d8-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a43d8-118">Uma cadeia de caracteres que especifica o idioma e país/região do assembly.</span><span class="sxs-lookup"><span data-stu-id="a43d8-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="a43d8-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a43d8-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a43d8-120">Um valor hexadecimal que especifica o nome forte do assembly.</span><span class="sxs-lookup"><span data-stu-id="a43d8-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="a43d8-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="a43d8-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a43d8-122">Um dos valores de "x86", "amd64", "msil" ou "ia64", especificando a arquitetura do processador para um assembly que contém o código específico do processador.</span><span class="sxs-lookup"><span data-stu-id="a43d8-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="a43d8-123">Os valores não diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="a43d8-123">The values are not case-sensitive.</span></span> <span data-ttu-id="a43d8-124">Se o atributo é atribuído a qualquer outro valor, todo o `<assemblyIdentity>` elemento será ignorado.</span><span class="sxs-lookup"><span data-stu-id="a43d8-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="a43d8-125">Consulte <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="a43d8-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="a43d8-126">processorArchitecture atributo</span><span class="sxs-lookup"><span data-stu-id="a43d8-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="a43d8-127">Valor</span><span class="sxs-lookup"><span data-stu-id="a43d8-127">Value</span></span>|<span data-ttu-id="a43d8-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="a43d8-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="a43d8-129">Apenas um processador AMD da 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a43d8-129">A 64-bit AMD processor only.</span></span>|  
|`ia64`|<span data-ttu-id="a43d8-130">Apenas um processador da 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a43d8-130">A 64-bit Intel processor only.</span></span>|  
|`msil`|<span data-ttu-id="a43d8-131">Neutro em relação ao processador e bits por palavra</span><span class="sxs-lookup"><span data-stu-id="a43d8-131">Neutral with respect to processor and bits-per-word</span></span>|  
|`x86`|<span data-ttu-id="a43d8-132">Um processador de 32 bits, ou nativo ou no Windows no ambiente do Windows (WOW) em uma plataforma de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a43d8-132">A 32-bit Intel processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a43d8-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a43d8-133">Child Elements</span></span>  
 <span data-ttu-id="a43d8-134">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a43d8-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a43d8-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a43d8-135">Parent Elements</span></span>  
  
|<span data-ttu-id="a43d8-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="a43d8-136">Element</span></span>|<span data-ttu-id="a43d8-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="a43d8-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a43d8-138">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="a43d8-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a43d8-139">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a43d8-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="a43d8-140">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="a43d8-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="a43d8-141">Use um `<dependentAssembly>` elemento para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="a43d8-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="a43d8-142">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a43d8-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a43d8-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="a43d8-143">Remarks</span></span>  
 <span data-ttu-id="a43d8-144">Cada  **\<dependentAssembly >** elemento deve ter um  **\<assemblyIdentity >** elemento filho.</span><span class="sxs-lookup"><span data-stu-id="a43d8-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="a43d8-145">Se o `processorArchitecture` atributo estiver presente, o `<assemblyIdentity>` elemento se aplica somente ao assembly com a arquitetura de processador correspondente.</span><span class="sxs-lookup"><span data-stu-id="a43d8-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="a43d8-146">Se o `processorArchitecture` atributo não estiver presente, o `<assemblyIdentity>` elemento pode ser aplicado a um assembly com qualquer arquitetura de processador.</span><span class="sxs-lookup"><span data-stu-id="a43d8-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="a43d8-147">O exemplo a seguir mostra um arquivo de configuração para dois assemblies com o mesmo nome de destino diferentes duas duas arquiteturas de processador e cujas versões não tem sido mantidas em sincronia. Quando o aplicativo executa em x86 plataforma primeiro `<assemblyIdentity>` elemento se aplica e a outra é ignorada.</span><span class="sxs-lookup"><span data-stu-id="a43d8-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="a43d8-148">Se o aplicativo é executado em uma plataforma que não seja x86 ou ia64, ambos serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="a43d8-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="a43d8-149">Se um arquivo de configuração contém uma `<assemblyIdentity>` elemento sem nenhum `processorArchitecture` de atributos e não contém um elemento que corresponda à plataforma, o elemento sem o `processorArchitecture` atributo será usado.</span><span class="sxs-lookup"><span data-stu-id="a43d8-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a43d8-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a43d8-150">Example</span></span>  
 <span data-ttu-id="a43d8-151">O exemplo a seguir mostra como fornecer informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="a43d8-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a43d8-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a43d8-152">See Also</span></span>  
 [<span data-ttu-id="a43d8-153">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a43d8-153">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a43d8-154">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a43d8-154">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a43d8-155">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="a43d8-155">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
