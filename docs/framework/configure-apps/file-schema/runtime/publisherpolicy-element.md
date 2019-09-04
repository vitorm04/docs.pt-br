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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc206e584440778858e61fc0bab51fc8ffa2009a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252374"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="34728-102">\<Elemento de > publisherPolicy Apply</span><span class="sxs-lookup"><span data-stu-id="34728-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="34728-103">Especifica se o tempo de execução aplica a política do editor.</span><span class="sxs-lookup"><span data-stu-id="34728-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
<span data-ttu-id="34728-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="34728-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="34728-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="34728-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="34728-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> assemblyBinding**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="34728-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="34728-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="34728-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="34728-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> publisherPolicy Apply**</span><span class="sxs-lookup"><span data-stu-id="34728-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34728-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34728-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34728-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="34728-110">Attributes and Elements</span></span>  
 <span data-ttu-id="34728-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="34728-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34728-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="34728-112">Attributes</span></span>  
  
|<span data-ttu-id="34728-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="34728-113">Attribute</span></span>|<span data-ttu-id="34728-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="34728-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="34728-115">Especifica se a política do Publicador deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="34728-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="34728-116">aplicar atributo</span><span class="sxs-lookup"><span data-stu-id="34728-116">apply Attribute</span></span>  
  
|<span data-ttu-id="34728-117">Valor</span><span class="sxs-lookup"><span data-stu-id="34728-117">Value</span></span>|<span data-ttu-id="34728-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="34728-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="34728-119">Aplica a política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="34728-119">Applies publisher policy.</span></span> <span data-ttu-id="34728-120">Essa é a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="34728-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="34728-121">Não aplica a política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="34728-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34728-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="34728-122">Child Elements</span></span>  

<span data-ttu-id="34728-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="34728-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34728-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="34728-124">Parent Elements</span></span>  
  
|<span data-ttu-id="34728-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="34728-125">Element</span></span>|<span data-ttu-id="34728-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="34728-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="34728-127">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="34728-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="34728-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34728-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="34728-129">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="34728-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="34728-130">Use um `<dependentAssembly>` elemento para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="34728-130">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="34728-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="34728-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34728-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="34728-132">Remarks</span></span>  
 <span data-ttu-id="34728-133">Quando um fornecedor de componentes libera uma nova versão de um assembly, o fornecedor pode incluir uma política de editor para que os aplicativos que usam a versão antiga agora usem a nova versão.</span><span class="sxs-lookup"><span data-stu-id="34728-133">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="34728-134">Para especificar se a política de editor deve ser aplicada a um determinado assembly, coloque o  **\<elemento publisherPolicy Apply >** no  **\<elemento dependentAssembly >** .</span><span class="sxs-lookup"><span data-stu-id="34728-134">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="34728-135">A configuração padrão para o atributo **aplicar** é **Sim**.</span><span class="sxs-lookup"><span data-stu-id="34728-135">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="34728-136">A definição do atributo **aplicar** como **não** substitui as configurações **Sim** anteriores para um assembly.</span><span class="sxs-lookup"><span data-stu-id="34728-136">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="34728-137">A permissão é necessária para que um aplicativo ignore explicitamente a política do Publicador usando o [ \<elemento publisherPolicy Apply Apply = "no"/>](publisherpolicy-element.md) no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34728-137">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="34728-138">A permissão é concedida definindo o <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador <xref:System.Security.Permissions.SecurityPermission>no.</span><span class="sxs-lookup"><span data-stu-id="34728-138">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="34728-139">Para obter mais informações, consulte permissão de segurança de redirecionamento de [Associação de assembly](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="34728-139">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34728-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34728-140">Example</span></span>  
 <span data-ttu-id="34728-141">O exemplo a seguir desativa a política do Publicador para `myAssembly`o assembly,.</span><span class="sxs-lookup"><span data-stu-id="34728-141">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34728-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34728-142">See also</span></span>

- [<span data-ttu-id="34728-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="34728-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="34728-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="34728-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="34728-145">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="34728-145">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="34728-146">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="34728-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
