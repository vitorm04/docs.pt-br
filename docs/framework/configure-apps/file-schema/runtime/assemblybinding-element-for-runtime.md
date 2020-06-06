---
title: Elemento <assemblyBinding> para <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154316"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="f934b-102">Elemento \<assemblyBinding> para \<runtime></span><span class="sxs-lookup"><span data-stu-id="f934b-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="f934b-103">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="f934b-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="f934b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f934b-104">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f934b-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f934b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f934b-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f934b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f934b-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f934b-107">Attributes</span></span>  
  
|<span data-ttu-id="f934b-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="f934b-108">Attribute</span></span>|<span data-ttu-id="f934b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f934b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f934b-110">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="f934b-110">**xmlns**</span></span>|<span data-ttu-id="f934b-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f934b-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="f934b-112">Especifica o namespace XML necessário para a associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="f934b-112">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="f934b-113">Use a cadeia de caracteres "urn: schemas-microsoft-com: asm. v1" como o valor.</span><span class="sxs-lookup"><span data-stu-id="f934b-113">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="f934b-114">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="f934b-114">**appliesTo**</span></span>|<span data-ttu-id="f934b-115">Especifica a versão de tempo de execução à qual o redirecionamento de assembly .NET Framework se aplica.</span><span class="sxs-lookup"><span data-stu-id="f934b-115">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="f934b-116">Esse atributo opcional usa um número de versão .NET Framework para indicar a qual versão ele se aplica.</span><span class="sxs-lookup"><span data-stu-id="f934b-116">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="f934b-117">Se nenhum atributo **AppliesTo** for especificado, o **\<assemblyBinding>** elemento se aplicará a todas as versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f934b-117">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="f934b-118">O atributo **AppliesTo** foi introduzido na versão .NET Framework 1,1; Ele é ignorado pelo .NET Framework versão 1,0.</span><span class="sxs-lookup"><span data-stu-id="f934b-118">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="f934b-119">Isso significa que todos os **\<assemblyBinding>** elementos são aplicados ao usar o .NET Framework versão 1,0, mesmo se um atributo **AppliesTo** for especificado.</span><span class="sxs-lookup"><span data-stu-id="f934b-119">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f934b-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f934b-120">Child Elements</span></span>  
  
|<span data-ttu-id="f934b-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f934b-121">Element</span></span>|<span data-ttu-id="f934b-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f934b-122">Description</span></span>|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="f934b-123">Encapsula a política de associação e o local do assembly para um assembly.</span><span class="sxs-lookup"><span data-stu-id="f934b-123">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="f934b-124">Use uma **\<dependentAssembly>** marca para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="f934b-124">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[\<probing>](probing-element.md)|<span data-ttu-id="f934b-125">Especifica subdiretórios que o Common Language Runtime pesquisa ao carregar assemblies.</span><span class="sxs-lookup"><span data-stu-id="f934b-125">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="f934b-126">Especifica se o runtime aplica a política do editor.</span><span class="sxs-lookup"><span data-stu-id="f934b-126">Specifies whether the runtime applies publisher policy.</span></span>|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="f934b-127">Especifica o nome completo do assembly que deve ser carregado dinamicamente quando um nome parcial é usado.</span><span class="sxs-lookup"><span data-stu-id="f934b-127">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f934b-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f934b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f934b-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="f934b-129">Element</span></span>|<span data-ttu-id="f934b-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="f934b-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f934b-131">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f934b-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f934b-132">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f934b-132">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f934b-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f934b-133">Example</span></span>  
 <span data-ttu-id="f934b-134">O exemplo a seguir mostra como redirecionar uma versão do assembly para outra e fornecer uma codebase.</span><span class="sxs-lookup"><span data-stu-id="f934b-134">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
  
 <span data-ttu-id="f934b-135">O exemplo a seguir mostra como usar o atributo **AppliesTo** para redirecionar a associação de um assembly .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f934b-135">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f934b-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="f934b-136">See also</span></span>

- [<span data-ttu-id="f934b-137">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="f934b-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f934b-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="f934b-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f934b-139">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="f934b-139">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
