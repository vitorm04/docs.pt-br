---
title: Elemento <bindingRedirect>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: 7cdea10cc6e0562f6062470240b01743aa439bde
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658935"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="09c86-102">\<Elemento > bindingRedirect</span><span class="sxs-lookup"><span data-stu-id="09c86-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="09c86-103">Redireciona uma versão do assembly para outra.</span><span class="sxs-lookup"><span data-stu-id="09c86-103">Redirects one assembly version to another.</span></span>  
  
 <span data-ttu-id="09c86-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="09c86-104">\<configuration></span></span>  
<span data-ttu-id="09c86-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="09c86-105">\<runtime></span></span>  
<span data-ttu-id="09c86-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="09c86-106">\<assemblyBinding></span></span>  
<span data-ttu-id="09c86-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="09c86-107">\<dependentAssembly></span></span>  
<span data-ttu-id="09c86-108">\<bindingRedirect></span><span class="sxs-lookup"><span data-stu-id="09c86-108">\<bindingRedirect></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09c86-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09c86-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09c86-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="09c86-110">Attributes and Elements</span></span>  
 <span data-ttu-id="09c86-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="09c86-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09c86-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="09c86-112">Attributes</span></span>  
  
|<span data-ttu-id="09c86-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="09c86-113">Attribute</span></span>|<span data-ttu-id="09c86-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="09c86-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="09c86-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="09c86-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="09c86-116">Especifica a versão do assembly que foi originalmente solicitada.</span><span class="sxs-lookup"><span data-stu-id="09c86-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="09c86-117">O formato de um número de versão do assembly é *Major. Minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="09c86-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="09c86-118">Os valores válidos para cada parte desse número de versão estão entre 0 e 65535.</span><span class="sxs-lookup"><span data-stu-id="09c86-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="09c86-119">Você também pode especificar um intervalo de versões no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="09c86-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="09c86-120">*n. n. n-n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="09c86-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="09c86-121">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="09c86-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="09c86-122">Especifica a versão do assembly a ser usada em vez da versão solicitada originalmente no formato: *n* . n. n. n</span><span class="sxs-lookup"><span data-stu-id="09c86-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="09c86-123">Esse valor pode especificar uma versão anterior do `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="09c86-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09c86-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="09c86-124">Child Elements</span></span>  
  
|<span data-ttu-id="09c86-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="09c86-125">Element</span></span>|<span data-ttu-id="09c86-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="09c86-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09c86-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09c86-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="09c86-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="09c86-128">Parent Elements</span></span>  
  
|<span data-ttu-id="09c86-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="09c86-129">Element</span></span>|<span data-ttu-id="09c86-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="09c86-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="09c86-131">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="09c86-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="09c86-132">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="09c86-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="09c86-133">Encapsula local do assembly e política de associação para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="09c86-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="09c86-134">Use um elemento dependentAssembly para cada assembly.</span><span class="sxs-lookup"><span data-stu-id="09c86-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="09c86-135">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="09c86-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09c86-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="09c86-136">Remarks</span></span>  
 <span data-ttu-id="09c86-137">Ao criar um aplicativo .NET Framework com base em um assembly com nome forte, o aplicativo usará essa versão do assembly em tempo de execução por padrão, mesmo se uma nova versão estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="09c86-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="09c86-138">No entanto, você pode configurar o aplicativo para ser executado com base em uma versão mais nova do assembly.</span><span class="sxs-lookup"><span data-stu-id="09c86-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="09c86-139">Para obter detalhes sobre como o tempo de execução usa esses arquivos para determinar qual versão do assembly usar, consulte [como o tempo de execução localiza assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="09c86-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="09c86-140">Você pode redirecionar mais de uma versão do assembly ao incluir vários elementos `bindingRedirect` em um elemento `dependentAssembly`.</span><span class="sxs-lookup"><span data-stu-id="09c86-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="09c86-141">Você também pode redirecionar de uma versão mais recente para uma versão anterior do assembly.</span><span class="sxs-lookup"><span data-stu-id="09c86-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="09c86-142">O redirecionamento de associação de assembly explícito em um arquivo de configuração do aplicativo requer uma permissão de segurança.</span><span class="sxs-lookup"><span data-stu-id="09c86-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="09c86-143">Isso se aplica ao redirecionamento de assemblies do .NET Framework e assemblies de terceiros.</span><span class="sxs-lookup"><span data-stu-id="09c86-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="09c86-144">A permissão é concedida definindo o <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador <xref:System.Security.Permissions.SecurityPermission>no.</span><span class="sxs-lookup"><span data-stu-id="09c86-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="09c86-145">Para obter mais informações, consulte permissão de segurança de redirecionamento de [Associação de assembly](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="09c86-145">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09c86-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09c86-146">Example</span></span>  
 <span data-ttu-id="09c86-147">O exemplo a seguir mostra como redirecionar uma versão do assembly para outra.</span><span class="sxs-lookup"><span data-stu-id="09c86-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
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
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09c86-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09c86-148">See also</span></span>

- [<span data-ttu-id="09c86-149">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="09c86-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="09c86-150">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="09c86-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="09c86-151">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="09c86-151">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
