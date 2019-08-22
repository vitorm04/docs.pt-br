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
ms.openlocfilehash: 7c8f8744d3ef1ca30eb05a4c8c3290d8a514714b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663507"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="1af81-102">\<Elemento de > publisherPolicy Apply</span><span class="sxs-lookup"><span data-stu-id="1af81-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="1af81-103">Especifica se o tempo de execução aplica a política do editor.</span><span class="sxs-lookup"><span data-stu-id="1af81-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="1af81-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1af81-104">\<configuration></span></span>  
<span data-ttu-id="1af81-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="1af81-105">\<runtime></span></span>  
<span data-ttu-id="1af81-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="1af81-106">\<assemblyBinding></span></span>  
<span data-ttu-id="1af81-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="1af81-107">\<dependentAssembly></span></span>  
<span data-ttu-id="1af81-108">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="1af81-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af81-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1af81-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1af81-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1af81-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1af81-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1af81-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1af81-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="1af81-112">Attributes</span></span>  
  
|<span data-ttu-id="1af81-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="1af81-113">Attribute</span></span>|<span data-ttu-id="1af81-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1af81-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="1af81-115">Especifica se a política do Publicador deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="1af81-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="1af81-116">aplicar atributo</span><span class="sxs-lookup"><span data-stu-id="1af81-116">apply Attribute</span></span>  
  
|<span data-ttu-id="1af81-117">Valor</span><span class="sxs-lookup"><span data-stu-id="1af81-117">Value</span></span>|<span data-ttu-id="1af81-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1af81-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="1af81-119">Aplica a política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="1af81-119">Applies publisher policy.</span></span> <span data-ttu-id="1af81-120">Essa é a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="1af81-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="1af81-121">Não aplica a política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="1af81-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1af81-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1af81-122">Child Elements</span></span>  
 <span data-ttu-id="1af81-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1af81-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1af81-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1af81-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1af81-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="1af81-125">Element</span></span>|<span data-ttu-id="1af81-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="1af81-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1af81-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1af81-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1af81-128">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="1af81-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1af81-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="1af81-129">Remarks</span></span>  
 <span data-ttu-id="1af81-130">Quando um fornecedor de componentes libera uma nova versão de um assembly, o fornecedor pode incluir uma política de editor para que os aplicativos que usam a versão antiga agora usem a nova versão.</span><span class="sxs-lookup"><span data-stu-id="1af81-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="1af81-131">Para especificar se a política de editor deve ser aplicada a um determinado assembly, coloque o  **\<elemento publisherPolicy Apply >** no  **\<elemento dependentAssembly >** .</span><span class="sxs-lookup"><span data-stu-id="1af81-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="1af81-132">A configuração padrão para o atributo **aplicar** é **Sim**.</span><span class="sxs-lookup"><span data-stu-id="1af81-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="1af81-133">A definição do atributo **aplicar** como **não** substitui as configurações **Sim** anteriores para um assembly.</span><span class="sxs-lookup"><span data-stu-id="1af81-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="1af81-134">A permissão é necessária para que um aplicativo ignore explicitamente a política do Publicador usando o [ \<elemento publisherPolicy Apply Apply = "no"/>](publisherpolicy-element.md) no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1af81-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="1af81-135">A permissão é concedida definindo o <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador <xref:System.Security.Permissions.SecurityPermission>no.</span><span class="sxs-lookup"><span data-stu-id="1af81-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="1af81-136">Para obter mais informações, consulte permissão de segurança de redirecionamento de [Associação de assembly](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="1af81-136">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1af81-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1af81-137">Example</span></span>  
 <span data-ttu-id="1af81-138">O exemplo a seguir desativa a política do Publicador para `myAssembly`o assembly,.</span><span class="sxs-lookup"><span data-stu-id="1af81-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1af81-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1af81-139">See also</span></span>

- [<span data-ttu-id="1af81-140">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1af81-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1af81-141">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="1af81-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1af81-142">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="1af81-142">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1af81-143">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="1af81-143">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
