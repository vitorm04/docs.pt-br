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
ms.openlocfilehash: a06daa0b2aa5374c9959cbbe778d62856819a40e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663860"
---
# <a name="codebase-element"></a><span data-ttu-id="877d3-102">\<Elemento de > codeBase</span><span class="sxs-lookup"><span data-stu-id="877d3-102">\<codeBase> Element</span></span>

<span data-ttu-id="877d3-103">Especifica onde o Common Language Runtime pode encontrar um assembly.</span><span class="sxs-lookup"><span data-stu-id="877d3-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="877d3-104">\<> \<de tempo de \<execução de configuração \<> assemblyBinding > dependentAssembly > \<codebase ></span><span class="sxs-lookup"><span data-stu-id="877d3-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span></span>

## <a name="syntax"></a><span data-ttu-id="877d3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="877d3-105">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="877d3-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="877d3-106">Attributes and Elements</span></span>

<span data-ttu-id="877d3-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="877d3-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="877d3-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="877d3-108">Attributes</span></span>

|<span data-ttu-id="877d3-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="877d3-109">Attribute</span></span>|<span data-ttu-id="877d3-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="877d3-110">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="877d3-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="877d3-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="877d3-112">Especifica a URL em que o tempo de execução pode encontrar a versão especificada do assembly.</span><span class="sxs-lookup"><span data-stu-id="877d3-112">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="877d3-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="877d3-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="877d3-114">Especifica a versão do assembly à qual a codebase se aplica.</span><span class="sxs-lookup"><span data-stu-id="877d3-114">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="877d3-115">O formato de um número de versão do assembly é *Major. Minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="877d3-115">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="877d3-116">Atributo de versão</span><span class="sxs-lookup"><span data-stu-id="877d3-116">version Attribute</span></span>

|<span data-ttu-id="877d3-117">Valor</span><span class="sxs-lookup"><span data-stu-id="877d3-117">Value</span></span>|<span data-ttu-id="877d3-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="877d3-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="877d3-119">Os valores válidos para cada parte do número de versão são de 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="877d3-119">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="877d3-120">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="877d3-120">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="877d3-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="877d3-121">Child Elements</span></span>

<span data-ttu-id="877d3-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="877d3-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="877d3-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="877d3-123">Parent Elements</span></span>

|<span data-ttu-id="877d3-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="877d3-124">Element</span></span>|<span data-ttu-id="877d3-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="877d3-125">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="877d3-126">Define uma coleção de provedores de compilação usados para compilar arquivos de recursos personalizados.</span><span class="sxs-lookup"><span data-stu-id="877d3-126">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="877d3-127">Você pode ter qualquer número de provedores de compilação.</span><span class="sxs-lookup"><span data-stu-id="877d3-127">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="877d3-128">Define todas as configurações de compilação que o ASP.NET usa.</span><span class="sxs-lookup"><span data-stu-id="877d3-128">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="877d3-129">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="877d3-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="877d3-130">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="877d3-130">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="877d3-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="877d3-131">Remarks</span></span>

<span data-ttu-id="877d3-132">Para que o tempo de execução use a configuração de  **\<> codebase** em um arquivo de configuração de máquina ou arquivo de política do Publicador, o arquivo também deve redirecionar a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="877d3-132">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="877d3-133">Os arquivos de configuração do aplicativo podem ter uma configuração de CodeBase sem redirecionar a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="877d3-133">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="877d3-134">Depois de determinar qual versão do assembly usar, o tempo de execução aplica a configuração de codebase do arquivo que determina a versão.</span><span class="sxs-lookup"><span data-stu-id="877d3-134">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="877d3-135">Se nenhuma codebase for indicada, o tempo de execução investigará o assembly da maneira usual.</span><span class="sxs-lookup"><span data-stu-id="877d3-135">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="877d3-136">Se o assembly tiver um nome forte, a configuração de CodeBase poderá estar em qualquer lugar na intranet local ou na Internet.</span><span class="sxs-lookup"><span data-stu-id="877d3-136">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="877d3-137">Se o assembly for um assembly particular, a configuração de CodeBase deverá ser um caminho relativo ao diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="877d3-137">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="877d3-138">Para assemblies sem um nome forte, a versão é ignorada e o carregador usa a primeira \<aparência da base \<de código > dentro do dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="877d3-138">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="877d3-139">Se houver uma entrada no arquivo de configuração de aplicativo que redireciona a associação a outro assembly, o redirecionamento terá precedência mesmo que a versão do assembly não corresponda à solicitação de associação.</span><span class="sxs-lookup"><span data-stu-id="877d3-139">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="877d3-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="877d3-140">Example</span></span>

<span data-ttu-id="877d3-141">O exemplo a seguir mostra como especificar onde o tempo de execução pode encontrar um assembly.</span><span class="sxs-lookup"><span data-stu-id="877d3-141">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="877d3-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="877d3-142">See also</span></span>

- [<span data-ttu-id="877d3-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="877d3-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="877d3-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="877d3-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="877d3-145">Especificando o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="877d3-145">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="877d3-146">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="877d3-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
