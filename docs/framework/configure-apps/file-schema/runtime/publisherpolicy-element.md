---
title: Elemento <publisherPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: 89fa8a991cc7d0352eb0a13cdfd3a6063ea468e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115844"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="c497f-102">\<elemento de > publisherPolicy Apply</span><span class="sxs-lookup"><span data-stu-id="c497f-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="c497f-103">Especifica se o runtime aplica a política do editor.</span><span class="sxs-lookup"><span data-stu-id="c497f-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
<span data-ttu-id="c497f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c497f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c497f-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="c497f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c497f-106">&nbsp; &nbsp; &nbsp; &nbsp;[ **\<assemblyBinding**](assemblybinding-element-for-runtime.md) > </span><span class="sxs-lookup"><span data-stu-id="c497f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="c497f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="c497f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="c497f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<publisherpolicy apply >**</span><span class="sxs-lookup"><span data-stu-id="c497f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c497f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c497f-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c497f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c497f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c497f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c497f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c497f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c497f-112">Attributes</span></span>  
  
|<span data-ttu-id="c497f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="c497f-113">Attribute</span></span>|<span data-ttu-id="c497f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c497f-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="c497f-115">Especifica se a política do Publicador deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="c497f-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="c497f-116">aplicar atributo</span><span class="sxs-lookup"><span data-stu-id="c497f-116">apply Attribute</span></span>  
  
|<span data-ttu-id="c497f-117">Valor</span><span class="sxs-lookup"><span data-stu-id="c497f-117">Value</span></span>|<span data-ttu-id="c497f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c497f-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="c497f-119">Aplica a política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="c497f-119">Applies publisher policy.</span></span> <span data-ttu-id="c497f-120">Essa é a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="c497f-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="c497f-121">Não aplica a política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="c497f-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c497f-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c497f-122">Child Elements</span></span>  

<span data-ttu-id="c497f-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c497f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c497f-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c497f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c497f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="c497f-125">Element</span></span>|<span data-ttu-id="c497f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="c497f-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="c497f-127">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="c497f-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="c497f-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c497f-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="c497f-129">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="c497f-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="c497f-130">Use um elemento `<dependentAssembly>` para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="c497f-130">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="c497f-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c497f-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c497f-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="c497f-132">Remarks</span></span>  
 <span data-ttu-id="c497f-133">Quando um fornecedor de componentes libera uma nova versão de um assembly, o fornecedor pode incluir uma política de editor para que os aplicativos que usam a versão antiga agora usem a nova versão.</span><span class="sxs-lookup"><span data-stu-id="c497f-133">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="c497f-134">Para especificar se a política de editor deve ser aplicada a um determinado assembly, coloque o elemento **\<publisherpolicy apply >** no elemento **\<dependentAssembly >** .</span><span class="sxs-lookup"><span data-stu-id="c497f-134">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="c497f-135">A configuração padrão para o atributo **aplicar** é **Sim**.</span><span class="sxs-lookup"><span data-stu-id="c497f-135">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="c497f-136">A definição do atributo **aplicar** como **não** substitui as configurações **Sim** anteriores para um assembly.</span><span class="sxs-lookup"><span data-stu-id="c497f-136">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="c497f-137">A permissão é necessária para que um aplicativo ignore explicitamente a política do Publicador usando o elemento [\<publisherPolicy Apply Apply = "no"/>](publisherpolicy-element.md) no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c497f-137">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="c497f-138">A permissão é concedida pela definição do sinalizador de <xref:System.Security.Permissions.SecurityPermissionFlag> no <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="c497f-138">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="c497f-139">Para obter mais informações, consulte [permissão de segurança de redirecionamento de associação de assembly](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="c497f-139">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c497f-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c497f-140">Example</span></span>  
 <span data-ttu-id="c497f-141">O exemplo a seguir desativa a política do Publicador para o assembly, `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="c497f-141">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c497f-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c497f-142">See also</span></span>

- [<span data-ttu-id="c497f-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c497f-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c497f-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c497f-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c497f-145">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="c497f-145">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c497f-146">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="c497f-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
