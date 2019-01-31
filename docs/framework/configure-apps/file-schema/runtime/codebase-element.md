---
title: Elemento <codeBase>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: ebf7e2624cc36fb6a758afef38e2054669061dff
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269647"
---
# <a name="codebase-element"></a><span data-ttu-id="a51d7-102">\<Base de código > elemento</span><span class="sxs-lookup"><span data-stu-id="a51d7-102">\<codeBase> Element</span></span>
<span data-ttu-id="a51d7-103">Especifica onde o common language runtime pode encontrar um assembly.</span><span class="sxs-lookup"><span data-stu-id="a51d7-103">Specifies where the common language runtime can find an assembly.</span></span>  
  
 <span data-ttu-id="a51d7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a51d7-104">\<configuration></span></span>  
<span data-ttu-id="a51d7-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="a51d7-105">\<runtime></span></span>  
<span data-ttu-id="a51d7-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="a51d7-106">\<assemblyBinding></span></span>  
<span data-ttu-id="a51d7-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="a51d7-107">\<dependentAssembly></span></span>  
<span data-ttu-id="a51d7-108">\<codeBase></span><span class="sxs-lookup"><span data-stu-id="a51d7-108">\<codeBase></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a51d7-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a51d7-109">Syntax</span></span>  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a51d7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a51d7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a51d7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a51d7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a51d7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a51d7-112">Attributes</span></span>  
  
|<span data-ttu-id="a51d7-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a51d7-113">Attribute</span></span>|<span data-ttu-id="a51d7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a51d7-114">Description</span></span>|  
|---------------|-----------------|  
|`href`|<span data-ttu-id="a51d7-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a51d7-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="a51d7-116">Especifica a URL onde o tempo de execução pode encontrar a versão especificada do assembly.</span><span class="sxs-lookup"><span data-stu-id="a51d7-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|  
|`version`|<span data-ttu-id="a51d7-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a51d7-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="a51d7-118">Especifica a versão do assembly a que a base de código aplica-se.</span><span class="sxs-lookup"><span data-stu-id="a51d7-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="a51d7-119">O formato de um número de versão do assembly é *Major*.</span><span class="sxs-lookup"><span data-stu-id="a51d7-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|  
  
## <a name="version-attribute"></a><span data-ttu-id="a51d7-120">Atributo de versão</span><span class="sxs-lookup"><span data-stu-id="a51d7-120">version Attribute</span></span>  
  
|<span data-ttu-id="a51d7-121">Valor</span><span class="sxs-lookup"><span data-stu-id="a51d7-121">Value</span></span>|<span data-ttu-id="a51d7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a51d7-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a51d7-123">Para cada parte do número de versão, os valores válidos são 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="a51d7-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="a51d7-124">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="a51d7-124">Not applicable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a51d7-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a51d7-125">Child Elements</span></span>  
 <span data-ttu-id="a51d7-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a51d7-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a51d7-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a51d7-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a51d7-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="a51d7-128">Element</span></span>|<span data-ttu-id="a51d7-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="a51d7-129">Description</span></span>|  
|-------------|-----------------|  
|`buildproviders`|<span data-ttu-id="a51d7-130">Define uma coleção de provedores de compilação usado para compilar os arquivos de recurso personalizado.</span><span class="sxs-lookup"><span data-stu-id="a51d7-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="a51d7-131">Você pode ter qualquer número de provedores de compilação.</span><span class="sxs-lookup"><span data-stu-id="a51d7-131">You can have any number of build providers.</span></span>|  
|`compilation`|<span data-ttu-id="a51d7-132">Configura todas as configurações de compilação que o ASP.NET usa.</span><span class="sxs-lookup"><span data-stu-id="a51d7-132">Configures all the compilation settings that ASP.NET uses.</span></span>|  
|`configuration`|<span data-ttu-id="a51d7-133">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a51d7-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.web`|<span data-ttu-id="a51d7-134">Especifica o elemento raiz para a seção de configuração do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a51d7-134">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a51d7-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="a51d7-135">Remarks</span></span>  
 <span data-ttu-id="a51d7-136">Para o tempo de execução usar o  **\<codeBase >** configuração em um arquivo de configuração do computador ou arquivo de política de editor, o arquivo também deve redirecionar a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="a51d7-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="a51d7-137">Arquivos de configuração de aplicativo podem ter uma configuração de base de código sem redirecionar a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="a51d7-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="a51d7-138">Depois de determinar qual versão de assembly a ser usada, o tempo de execução se aplica a configuração de base de código do arquivo que determina a versão.</span><span class="sxs-lookup"><span data-stu-id="a51d7-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="a51d7-139">Se nenhuma base de código estiver indicado, o tempo de execução investiga o assembly como de costume.</span><span class="sxs-lookup"><span data-stu-id="a51d7-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>  
  
 <span data-ttu-id="a51d7-140">Se o assembly tiver um nome forte, a configuração de base de código pode estar em qualquer lugar na intranet local ou na Internet.</span><span class="sxs-lookup"><span data-stu-id="a51d7-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="a51d7-141">Se o assembly é um assembly particular, a configuração de base de código deve ser um caminho relativo ao diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a51d7-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>  
  
 <span data-ttu-id="a51d7-142">Para assemblies sem um nome forte, a versão é ignorado e o carregador usará a primeira ocorrência desse \<codebase > dentro de \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="a51d7-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="a51d7-143">Se houver uma entrada no arquivo de configuração do aplicativo que redireciona associação a outro assembly, o redirecionamento terá precedência mesmo se a versão do assembly não corresponde a solicitação de associação.</span><span class="sxs-lookup"><span data-stu-id="a51d7-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesnt match the binding request.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a51d7-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a51d7-144">Example</span></span>  
 <span data-ttu-id="a51d7-145">O exemplo a seguir mostra como especificar onde o tempo de execução pode encontrar um assembly.</span><span class="sxs-lookup"><span data-stu-id="a51d7-145">The following example shows how to specify where the runtime can find an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a51d7-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a51d7-146">See also</span></span>
- [<span data-ttu-id="a51d7-147">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a51d7-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="a51d7-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a51d7-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a51d7-149">Especificando o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="a51d7-149">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [<span data-ttu-id="a51d7-150">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="a51d7-150">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
