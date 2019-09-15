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
ms.openlocfilehash: 475b7df55ed509157c1da0aeb8f979de238c72b5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971882"
---
# <a name="codebase-element"></a><span data-ttu-id="eff96-102">\<Elemento de > codeBase</span><span class="sxs-lookup"><span data-stu-id="eff96-102">\<codeBase> Element</span></span>

<span data-ttu-id="eff96-103">Especifica onde o Common Language Runtime pode encontrar um assembly.</span><span class="sxs-lookup"><span data-stu-id="eff96-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="eff96-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eff96-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eff96-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="eff96-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="eff96-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> assemblyBinding**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="eff96-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="eff96-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="eff96-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="eff96-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<codeBase>**</span><span class="sxs-lookup"><span data-stu-id="eff96-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**</span></span>

## <a name="syntax"></a><span data-ttu-id="eff96-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eff96-109">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eff96-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eff96-110">Attributes and Elements</span></span>

<span data-ttu-id="eff96-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eff96-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="eff96-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="eff96-112">Attributes</span></span>

|<span data-ttu-id="eff96-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="eff96-113">Attribute</span></span>|<span data-ttu-id="eff96-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="eff96-114">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="eff96-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="eff96-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="eff96-116">Especifica a URL em que o tempo de execução pode encontrar a versão especificada do assembly.</span><span class="sxs-lookup"><span data-stu-id="eff96-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="eff96-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="eff96-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="eff96-118">Especifica a versão do assembly à qual a codebase se aplica.</span><span class="sxs-lookup"><span data-stu-id="eff96-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="eff96-119">O formato de um número de versão do assembly é *Major. Minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="eff96-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="eff96-120">Atributo de versão</span><span class="sxs-lookup"><span data-stu-id="eff96-120">version Attribute</span></span>

|<span data-ttu-id="eff96-121">Valor</span><span class="sxs-lookup"><span data-stu-id="eff96-121">Value</span></span>|<span data-ttu-id="eff96-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="eff96-122">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="eff96-123">Os valores válidos para cada parte do número de versão são de 0 a 65535.</span><span class="sxs-lookup"><span data-stu-id="eff96-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="eff96-124">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="eff96-124">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="eff96-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eff96-125">Child Elements</span></span>

<span data-ttu-id="eff96-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="eff96-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="eff96-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eff96-127">Parent Elements</span></span>

|<span data-ttu-id="eff96-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="eff96-128">Element</span></span>|<span data-ttu-id="eff96-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="eff96-129">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="eff96-130">Define uma coleção de provedores de compilação usados para compilar arquivos de recursos personalizados.</span><span class="sxs-lookup"><span data-stu-id="eff96-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="eff96-131">Você pode ter qualquer número de provedores de compilação.</span><span class="sxs-lookup"><span data-stu-id="eff96-131">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="eff96-132">Define todas as configurações de compilação que o ASP.NET usa.</span><span class="sxs-lookup"><span data-stu-id="eff96-132">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="eff96-133">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eff96-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="eff96-134">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="eff96-134">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eff96-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="eff96-135">Remarks</span></span>

<span data-ttu-id="eff96-136">Para que o tempo de execução use a configuração de  **\<> codebase** em um arquivo de configuração de máquina ou arquivo de política do Publicador, o arquivo também deve redirecionar a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="eff96-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="eff96-137">Os arquivos de configuração do aplicativo podem ter uma configuração de CodeBase sem redirecionar a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="eff96-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="eff96-138">Depois de determinar qual versão do assembly usar, o tempo de execução aplica a configuração de codebase do arquivo que determina a versão.</span><span class="sxs-lookup"><span data-stu-id="eff96-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="eff96-139">Se nenhuma codebase for indicada, o tempo de execução investigará o assembly da maneira usual.</span><span class="sxs-lookup"><span data-stu-id="eff96-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="eff96-140">Se o assembly tiver um nome forte, a configuração de CodeBase poderá estar em qualquer lugar na intranet local ou na Internet.</span><span class="sxs-lookup"><span data-stu-id="eff96-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="eff96-141">Se o assembly for um assembly particular, a configuração de CodeBase deverá ser um caminho relativo ao diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eff96-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="eff96-142">Para assemblies sem um nome forte, a versão é ignorada e o carregador usa a primeira \<aparência da base \<de código > dentro do dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="eff96-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="eff96-143">Se houver uma entrada no arquivo de configuração de aplicativo que redireciona a associação a outro assembly, o redirecionamento terá precedência mesmo que a versão do assembly não corresponda à solicitação de associação.</span><span class="sxs-lookup"><span data-stu-id="eff96-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="eff96-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eff96-144">Example</span></span>

<span data-ttu-id="eff96-145">O exemplo a seguir mostra como especificar onde o tempo de execução pode encontrar um assembly.</span><span class="sxs-lookup"><span data-stu-id="eff96-145">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eff96-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eff96-146">See also</span></span>

- [<span data-ttu-id="eff96-147">Esquema de configurações de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="eff96-147">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="eff96-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="eff96-148">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="eff96-149">Especificar o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="eff96-149">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="eff96-150">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="eff96-150">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
