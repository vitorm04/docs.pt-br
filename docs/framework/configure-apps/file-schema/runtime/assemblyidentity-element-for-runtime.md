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
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154303"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="04aa4-102">\<montagemElemento> \<de identidade para> de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="04aa4-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="04aa4-103">Contém informações de identificação sobre a montagem.</span><span class="sxs-lookup"><span data-stu-id="04aa4-103">Contains identifying information about the assembly.</span></span>  
  
<span data-ttu-id="04aa4-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="04aa4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="04aa4-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="04aa4-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="04aa4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<montagem>vinculante**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="04aa4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="04aa4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependente>de montagem**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="04aa4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="04aa4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<montagemIdentidade>**</span><span class="sxs-lookup"><span data-stu-id="04aa4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04aa4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04aa4-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04aa4-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="04aa4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="04aa4-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="04aa4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04aa4-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="04aa4-112">Attributes</span></span>  
  
|<span data-ttu-id="04aa4-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="04aa4-113">Attribute</span></span>|<span data-ttu-id="04aa4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="04aa4-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="04aa4-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="04aa4-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="04aa4-116">O nome da assembléia</span><span class="sxs-lookup"><span data-stu-id="04aa4-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="04aa4-117">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="04aa4-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="04aa4-118">Uma seqüência que especifica o idioma e o país/região da montagem.</span><span class="sxs-lookup"><span data-stu-id="04aa4-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="04aa4-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="04aa4-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="04aa4-120">Um valor hexadecimal que especifica o nome forte da montagem.</span><span class="sxs-lookup"><span data-stu-id="04aa4-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="04aa4-121">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="04aa4-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="04aa4-122">Um dos valores "x86", "amd64", "msil" ou "ia64", especificando a arquitetura do processador para um conjunto que contém código específico do processador.</span><span class="sxs-lookup"><span data-stu-id="04aa4-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="04aa4-123">Os valores não são sensíveis a maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="04aa4-123">The values are not case-sensitive.</span></span> <span data-ttu-id="04aa4-124">Se o atributo for atribuído a `<assemblyIdentity>` qualquer outro valor, todo o elemento será ignorado.</span><span class="sxs-lookup"><span data-stu-id="04aa4-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="04aa4-125">Consulte <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="04aa4-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="04aa4-126">atributo de arquitetura do processador</span><span class="sxs-lookup"><span data-stu-id="04aa4-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="04aa4-127">Valor</span><span class="sxs-lookup"><span data-stu-id="04aa4-127">Value</span></span>|<span data-ttu-id="04aa4-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="04aa4-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="04aa4-129">Somente arquitetura AMD x86-64.</span><span class="sxs-lookup"><span data-stu-id="04aa4-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="04aa4-130">Somente arquitetura Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="04aa4-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="04aa4-131">Neutro em relação ao processador e bits por palavra.</span><span class="sxs-lookup"><span data-stu-id="04aa4-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="04aa4-132">Um processador x86 de 32 bits, nativo ou no ambiente Windows on Windows (WOW) em uma plataforma de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="04aa4-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04aa4-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="04aa4-133">Child Elements</span></span>  
 <span data-ttu-id="04aa4-134">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="04aa4-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04aa4-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="04aa4-135">Parent Elements</span></span>  
  
|<span data-ttu-id="04aa4-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="04aa4-136">Element</span></span>|<span data-ttu-id="04aa4-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="04aa4-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="04aa4-138">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="04aa4-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="04aa4-139">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04aa4-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="04aa4-140">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="04aa4-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="04aa4-141">Use `<dependentAssembly>` um elemento para cada montagem.</span><span class="sxs-lookup"><span data-stu-id="04aa4-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="04aa4-142">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="04aa4-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04aa4-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="04aa4-143">Remarks</span></span>  
 <span data-ttu-id="04aa4-144">Cada \*\* \<\*\* elemento de>de montagem dependente deve ter um \*\* \<elemento de>\*\* filho de uma montagem.</span><span class="sxs-lookup"><span data-stu-id="04aa4-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="04aa4-145">Se `processorArchitecture` o atributo `<assemblyIdentity>` estiver presente, o elemento se aplica apenas ao conjunto com a arquitetura correspondente do processador.</span><span class="sxs-lookup"><span data-stu-id="04aa4-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="04aa4-146">Se `processorArchitecture` o atributo não `<assemblyIdentity>` estiver presente, o elemento pode ser aplicado a um conjunto com qualquer arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="04aa4-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="04aa4-147">O exemplo a seguir mostra um arquivo de configuração para dois conjuntos com o mesmo nome que visam duas arquiteturas diferentes de dois processadores, e cujas versões não foram mantidas em sincronia. Quando o aplicativo é executado na plataforma `<assemblyIdentity>` x86, o primeiro elemento se aplica e o outro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="04aa4-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="04aa4-148">Se o aplicativo for executado em uma plataforma diferente de x86 ou ia64, ambos serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="04aa4-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="04aa4-149">Se um arquivo `<assemblyIdentity>` de configuração contiver um elemento sem `processorArchitecture` atributo e `processorArchitecture` não contiver um elemento que corresponda à plataforma, o elemento sem o atributo será usado.</span><span class="sxs-lookup"><span data-stu-id="04aa4-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04aa4-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04aa4-150">Example</span></span>  
 <span data-ttu-id="04aa4-151">O exemplo a seguir mostra como fornecer informações sobre uma montagem.</span><span class="sxs-lookup"><span data-stu-id="04aa4-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04aa4-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="04aa4-152">See also</span></span>

- [<span data-ttu-id="04aa4-153">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="04aa4-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="04aa4-154">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="04aa4-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="04aa4-155">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="04aa4-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
