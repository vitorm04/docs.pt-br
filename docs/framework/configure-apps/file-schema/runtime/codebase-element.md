---
title: '&lt;Base de código&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d7563d3a0ba545bfd8d1b80981fcce607d230873
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028206"
---
# <a name="ltcodebasegt-element"></a><span data-ttu-id="0ae58-102">&lt;Base de código&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="0ae58-102">&lt;codeBase&gt; Element</span></span>
<span data-ttu-id="0ae58-103">Especifica onde o common language runtime pode encontrar um assembly.</span><span class="sxs-lookup"><span data-stu-id="0ae58-103">Specifies where the common language runtime can find an assembly.</span></span>  
  
 <span data-ttu-id="0ae58-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0ae58-104">\<configuration></span></span>  
<span data-ttu-id="0ae58-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="0ae58-105">\<runtime></span></span>  
<span data-ttu-id="0ae58-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="0ae58-106">\<assemblyBinding></span></span>  
<span data-ttu-id="0ae58-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="0ae58-107">\<dependentAssembly></span></span>  
<span data-ttu-id="0ae58-108">\<Base de código ></span><span class="sxs-lookup"><span data-stu-id="0ae58-108">\<codeBase></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ae58-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ae58-109">Syntax</span></span>  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ae58-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0ae58-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0ae58-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0ae58-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ae58-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="0ae58-112">Attributes</span></span>  
  
|<span data-ttu-id="0ae58-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="0ae58-113">Attribute</span></span>|<span data-ttu-id="0ae58-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ae58-114">Description</span></span>|  
|---------------|-----------------|  
|`href`|<span data-ttu-id="0ae58-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0ae58-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="0ae58-116">Especifica a URL onde o tempo de execução pode encontrar a versão especificada do assembly.</span><span class="sxs-lookup"><span data-stu-id="0ae58-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|  
|`version`|<span data-ttu-id="0ae58-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0ae58-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="0ae58-118">Especifica a versão do assembly a que a base de código aplica-se.</span><span class="sxs-lookup"><span data-stu-id="0ae58-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="0ae58-119">O formato de um número de versão do assembly é *Major*.</span><span class="sxs-lookup"><span data-stu-id="0ae58-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|  
  
## <a name="version-attribute"></a><span data-ttu-id="0ae58-120">Atributo de versão</span><span class="sxs-lookup"><span data-stu-id="0ae58-120">version Attribute</span></span>  
  
|<span data-ttu-id="0ae58-121">Valor</span><span class="sxs-lookup"><span data-stu-id="0ae58-121">Value</span></span>|<span data-ttu-id="0ae58-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ae58-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0ae58-123">Para cada parte do número de versão, os valores válidos são 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="0ae58-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="0ae58-124">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="0ae58-124">Not applicable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ae58-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0ae58-125">Child Elements</span></span>  
 <span data-ttu-id="0ae58-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0ae58-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ae58-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0ae58-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0ae58-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ae58-128">Element</span></span>|<span data-ttu-id="0ae58-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ae58-129">Description</span></span>|  
|-------------|-----------------|  
|`buildproviders`|<span data-ttu-id="0ae58-130">Define uma coleção de provedores de compilação usado para compilar os arquivos de recurso personalizado.</span><span class="sxs-lookup"><span data-stu-id="0ae58-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="0ae58-131">Você pode ter qualquer número de provedores de compilação.</span><span class="sxs-lookup"><span data-stu-id="0ae58-131">You can have any number of build providers.</span></span>|  
|`compilation`|<span data-ttu-id="0ae58-132">Configura todas as configurações de compilação que o ASP.NET usa.</span><span class="sxs-lookup"><span data-stu-id="0ae58-132">Configures all the compilation settings that ASP.NET uses.</span></span>|  
|`configuration`|<span data-ttu-id="0ae58-133">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ae58-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.web`|<span data-ttu-id="0ae58-134">Especifica o elemento raiz para a seção de configuração do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0ae58-134">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ae58-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ae58-135">Remarks</span></span>  
 <span data-ttu-id="0ae58-136">Para o tempo de execução usar o  **\<codeBase >** configuração em um arquivo de configuração do computador ou arquivo de política de editor, o arquivo também deve redirecionar a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="0ae58-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="0ae58-137">Arquivos de configuração de aplicativo podem ter uma configuração de base de código sem redirecionar a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="0ae58-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="0ae58-138">Depois de determinar qual versão de assembly a ser usada, o tempo de execução se aplica a configuração de base de código do arquivo que determina a versão.</span><span class="sxs-lookup"><span data-stu-id="0ae58-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="0ae58-139">Se nenhuma base de código estiver indicado, o tempo de execução investiga o assembly como de costume.</span><span class="sxs-lookup"><span data-stu-id="0ae58-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>  
  
 <span data-ttu-id="0ae58-140">Se o assembly tiver um nome forte, a configuração de base de código pode estar em qualquer lugar na intranet local ou na Internet.</span><span class="sxs-lookup"><span data-stu-id="0ae58-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="0ae58-141">Se o assembly é um assembly particular, a configuração de base de código deve ser um caminho relativo ao diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0ae58-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>  
  
 <span data-ttu-id="0ae58-142">Para assemblies sem um nome forte, a versão é ignorado e o carregador usará a primeira ocorrência desse \<codebase > dentro de \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="0ae58-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="0ae58-143">Se houver uma entrada no arquivo de configuração do aplicativo que redireciona associação a outro assembly, o redirecionamento terá precedência mesmo se a versão do assembly não corresponde a solicitação de associação.</span><span class="sxs-lookup"><span data-stu-id="0ae58-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesnt match the binding request.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ae58-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ae58-144">Example</span></span>  
 <span data-ttu-id="0ae58-145">O exemplo a seguir mostra como especificar onde o tempo de execução pode encontrar um assembly.</span><span class="sxs-lookup"><span data-stu-id="0ae58-145">The following example shows how to specify where the runtime can find an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ae58-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ae58-146">See Also</span></span>  
 [<span data-ttu-id="0ae58-147">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0ae58-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="0ae58-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0ae58-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0ae58-149">Especificando o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="0ae58-149">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="0ae58-150">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="0ae58-150">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
