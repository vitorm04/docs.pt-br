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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115844"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="cfd39-102">Elemento \<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="cfd39-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="cfd39-103">Especifica se o runtime aplica a política do editor.</span><span class="sxs-lookup"><span data-stu-id="cfd39-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="cfd39-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfd39-104">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfd39-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cfd39-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cfd39-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cfd39-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfd39-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="cfd39-107">Attributes</span></span>  
  
|<span data-ttu-id="cfd39-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="cfd39-108">Attribute</span></span>|<span data-ttu-id="cfd39-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfd39-109">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="cfd39-110">Especifica se a política do Publicador deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="cfd39-110">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="cfd39-111">aplicar atributo</span><span class="sxs-lookup"><span data-stu-id="cfd39-111">apply Attribute</span></span>  
  
|<span data-ttu-id="cfd39-112">Valor</span><span class="sxs-lookup"><span data-stu-id="cfd39-112">Value</span></span>|<span data-ttu-id="cfd39-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfd39-113">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="cfd39-114">Aplica a política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="cfd39-114">Applies publisher policy.</span></span> <span data-ttu-id="cfd39-115">Essa é a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="cfd39-115">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="cfd39-116">Não aplica a política do Publicador.</span><span class="sxs-lookup"><span data-stu-id="cfd39-116">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfd39-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cfd39-117">Child Elements</span></span>  

<span data-ttu-id="cfd39-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cfd39-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cfd39-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cfd39-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cfd39-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="cfd39-120">Element</span></span>|<span data-ttu-id="cfd39-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfd39-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="cfd39-122">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="cfd39-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="cfd39-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cfd39-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="cfd39-124">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="cfd39-124">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="cfd39-125">Use um `<dependentAssembly>` elemento para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="cfd39-125">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="cfd39-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cfd39-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfd39-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="cfd39-127">Remarks</span></span>  
 <span data-ttu-id="cfd39-128">Quando um fornecedor de componentes libera uma nova versão de um assembly, o fornecedor pode incluir uma política de editor para que os aplicativos que usam a versão antiga agora usem a nova versão.</span><span class="sxs-lookup"><span data-stu-id="cfd39-128">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="cfd39-129">Para especificar se a política de editor deve ser aplicada a um determinado assembly, coloque o **\<publisherPolicy>** elemento no **\<dependentAssembly>** elemento.</span><span class="sxs-lookup"><span data-stu-id="cfd39-129">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="cfd39-130">A configuração padrão para o atributo **aplicar** é **Sim**.</span><span class="sxs-lookup"><span data-stu-id="cfd39-130">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="cfd39-131">A definição do atributo **aplicar** como **não** substitui as configurações **Sim** anteriores para um assembly.</span><span class="sxs-lookup"><span data-stu-id="cfd39-131">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="cfd39-132">A permissão é necessária para que um aplicativo ignore explicitamente a política do editor usando o [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfd39-132">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="cfd39-133">A permissão é concedida definindo o <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador no <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="cfd39-133">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="cfd39-134">Para obter mais informações, consulte [permissão de segurança de redirecionamento de associação de assembly](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="cfd39-134">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfd39-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfd39-135">Example</span></span>  
 <span data-ttu-id="cfd39-136">O exemplo a seguir desativa a política do Publicador para o assembly, `myAssembly` .</span><span class="sxs-lookup"><span data-stu-id="cfd39-136">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cfd39-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfd39-137">See also</span></span>

- [<span data-ttu-id="cfd39-138">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="cfd39-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cfd39-139">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="cfd39-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cfd39-140">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="cfd39-140">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="cfd39-141">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="cfd39-141">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
