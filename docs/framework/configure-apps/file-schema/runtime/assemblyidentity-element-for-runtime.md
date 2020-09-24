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
ms.openlocfilehash: f3e74b05ac0fd7c57963f2aad047ba3f2d63a10a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170175"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="7a713-102">Elemento \<assemblyIdentity> para \<runtime></span><span class="sxs-lookup"><span data-stu-id="7a713-102">\<assemblyIdentity> Element for \<runtime></span></span>

<span data-ttu-id="7a713-103">Contém informações de identificação sobre o assembly.</span><span class="sxs-lookup"><span data-stu-id="7a713-103">Contains identifying information about the assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a><span data-ttu-id="7a713-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a713-104">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a713-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7a713-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7a713-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7a713-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a713-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="7a713-107">Attributes</span></span>  
  
|<span data-ttu-id="7a713-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="7a713-108">Attribute</span></span>|<span data-ttu-id="7a713-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a713-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="7a713-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="7a713-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="7a713-111">O nome do assembly</span><span class="sxs-lookup"><span data-stu-id="7a713-111">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="7a713-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="7a713-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7a713-113">Uma cadeia de caracteres que especifica o idioma e o país/região do assembly.</span><span class="sxs-lookup"><span data-stu-id="7a713-113">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="7a713-114">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="7a713-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7a713-115">Um valor hexadecimal que especifica o nome forte do assembly.</span><span class="sxs-lookup"><span data-stu-id="7a713-115">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="7a713-116">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="7a713-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7a713-117">Um dos valores "x86", "amd64", "MSIL" ou "IA64", especificando a arquitetura do processador para um assembly que contém código específico do processador.</span><span class="sxs-lookup"><span data-stu-id="7a713-117">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="7a713-118">Os valores não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="7a713-118">The values are not case-sensitive.</span></span> <span data-ttu-id="7a713-119">Se o atributo for atribuído a qualquer outro valor, todo o `<assemblyIdentity>` elemento será ignorado.</span><span class="sxs-lookup"><span data-stu-id="7a713-119">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="7a713-120">Consulte <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="7a713-120">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="7a713-121">Atributo processorArchitecture</span><span class="sxs-lookup"><span data-stu-id="7a713-121">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="7a713-122">Valor</span><span class="sxs-lookup"><span data-stu-id="7a713-122">Value</span></span>|<span data-ttu-id="7a713-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a713-123">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="7a713-124">Somente arquitetura AMD x86-64.</span><span class="sxs-lookup"><span data-stu-id="7a713-124">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="7a713-125">Somente a arquitetura Itanium da Intel.</span><span class="sxs-lookup"><span data-stu-id="7a713-125">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="7a713-126">Neutro em relação ao processador e bits por palavra.</span><span class="sxs-lookup"><span data-stu-id="7a713-126">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="7a713-127">Um processador x86 de 32 bits, nativo ou no ambiente Windows no Windows (WOW) em uma plataforma de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7a713-127">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a713-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7a713-128">Child Elements</span></span>  

 <span data-ttu-id="7a713-129">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7a713-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a713-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7a713-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7a713-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a713-131">Element</span></span>|<span data-ttu-id="7a713-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a713-132">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="7a713-133">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="7a713-133">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="7a713-134">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a713-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="7a713-135">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="7a713-135">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="7a713-136">Use um `<dependentAssembly>` elemento para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="7a713-136">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="7a713-137">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7a713-137">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a713-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a713-138">Remarks</span></span>  

 <span data-ttu-id="7a713-139">Cada **\<dependentAssembly>** elemento deve ter um **\<assemblyIdentity>** elemento filho.</span><span class="sxs-lookup"><span data-stu-id="7a713-139">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="7a713-140">Se o `processorArchitecture` atributo estiver presente, o `<assemblyIdentity>` elemento se aplicará somente ao assembly com a arquitetura de processador correspondente.</span><span class="sxs-lookup"><span data-stu-id="7a713-140">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="7a713-141">Se o `processorArchitecture` atributo não estiver presente, o `<assemblyIdentity>` elemento poderá ser aplicado a um assembly com qualquer arquitetura de processador.</span><span class="sxs-lookup"><span data-stu-id="7a713-141">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="7a713-142">O exemplo a seguir mostra um arquivo de configuração para dois assemblies com o mesmo nome direcionado a duas arquiteturas de processador diferentes, e cujas versões não foram mantidas em sincronia. Quando o aplicativo é executado na plataforma x86, o primeiro `<assemblyIdentity>` elemento se aplica e o outro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="7a713-142">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="7a713-143">Se o aplicativo for executado em uma plataforma diferente de x86 ou ia64, ambos serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="7a713-143">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="7a713-144">Se um arquivo de configuração contiver um `<assemblyIdentity>` elemento sem `processorArchitecture` atributo e não contiver um elemento que corresponda à plataforma, o elemento sem o `processorArchitecture` atributo será usado.</span><span class="sxs-lookup"><span data-stu-id="7a713-144">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a713-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7a713-145">Example</span></span>  

 <span data-ttu-id="7a713-146">O exemplo a seguir mostra como fornecer informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="7a713-146">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a713-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="7a713-147">See also</span></span>

- [<span data-ttu-id="7a713-148">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="7a713-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7a713-149">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="7a713-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7a713-150">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="7a713-150">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
