---
title: "Compatibilidade de políticas de segurança de acesso de código e migração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29e81f5e83bc3cbf9467c7940ba6acfd0a8c99b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="2056b-102">Compatibilidade de políticas de segurança de acesso de código e migração</span><span class="sxs-lookup"><span data-stu-id="2056b-102">Code Access Security Policy Compatibility and Migration</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="2056b-103">A parte da política de segurança de acesso ao código (CAS) se tornou obsoleta no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2056b-103">The policy portion of code access security (CAS) has been made obsolete in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="2056b-104">Como resultado, você pode encontrar avisos de compilação e exceções de tempo de execução se você chamar os tipos de política obsoleto e membros [explicitamente](#explicit_use) ou [implicitamente](#implicit_use) (por meio de outros tipos e membros).</span><span class="sxs-lookup"><span data-stu-id="2056b-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>  
  
 <span data-ttu-id="2056b-105">Você pode evitar os erros e avisos ao:</span><span class="sxs-lookup"><span data-stu-id="2056b-105">You can avoid the warnings and errors by either:</span></span>  
  
-   <span data-ttu-id="2056b-106">[Migrando](#migration) para o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] substituições para as chamadas obsoletas.</span><span class="sxs-lookup"><span data-stu-id="2056b-106">[Migrating](#migration) to the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] replacements for the obsolete calls.</span></span>  
  
     <span data-ttu-id="2056b-107">\- ou -</span><span class="sxs-lookup"><span data-stu-id="2056b-107">\- or -</span></span>  
  
-   <span data-ttu-id="2056b-108">Usando o [o elemento de configuração < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) para aceitar o comportamento de política de CAS herdado.</span><span class="sxs-lookup"><span data-stu-id="2056b-108">Using the [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>  
  
 <span data-ttu-id="2056b-109">Esse tópico contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="2056b-109">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="2056b-110">Uso explícito</span><span class="sxs-lookup"><span data-stu-id="2056b-110">Explicit Use</span></span>](#explicit_use)  
  
-   [<span data-ttu-id="2056b-111">Uso implícito</span><span class="sxs-lookup"><span data-stu-id="2056b-111">Implicit Use</span></span>](#implicit_use)  
  
-   [<span data-ttu-id="2056b-112">Erros e avisos</span><span class="sxs-lookup"><span data-stu-id="2056b-112">Errors and Warnings</span></span>](#errors_and_warnings)  
  
-   [<span data-ttu-id="2056b-113">Migração: Substituição para chamadas obsoletas</span><span class="sxs-lookup"><span data-stu-id="2056b-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)  
  
-   [<span data-ttu-id="2056b-114">Compatibilidade: Usando a opção de política de CAS herdado</span><span class="sxs-lookup"><span data-stu-id="2056b-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a><span data-ttu-id="2056b-115">Uso explícito</span><span class="sxs-lookup"><span data-stu-id="2056b-115">Explicit Use</span></span>  
 <span data-ttu-id="2056b-116">Membros que diretamente manipulam a política de segurança ou exigem a política de CAS para a área restrita estão obsoletos e gerarão erros por padrão.</span><span class="sxs-lookup"><span data-stu-id="2056b-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>  
  
 <span data-ttu-id="2056b-117">Exemplos são:</span><span class="sxs-lookup"><span data-stu-id="2056b-117">Examples of these are:</span></span>  
  
-   <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>  
  
<a name="implicit_use"></a>   
## <a name="implicit-use"></a><span data-ttu-id="2056b-118">Uso implícito</span><span class="sxs-lookup"><span data-stu-id="2056b-118">Implicit Use</span></span>  
 <span data-ttu-id="2056b-119">Carregamento do assembly várias sobrecargas produzir erros devido a seu uso implícito de política de CAS.</span><span class="sxs-lookup"><span data-stu-id="2056b-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="2056b-120">Essas sobrecargas usam uma <xref:System.Security.Policy.Evidence> parâmetro que é usado para resolver a política de CAS e fornecer uma permissão de conceder o conjunto para um assembly.</span><span class="sxs-lookup"><span data-stu-id="2056b-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>  
  
 <span data-ttu-id="2056b-121">Aqui estão alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="2056b-121">Here are some examples.</span></span> <span data-ttu-id="2056b-122">As sobrecargas obsoletas são aqueles que usam <xref:System.Security.Policy.Evidence> como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="2056b-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>  
  
-   <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
<a name="errors_and_warnings"></a>   
## <a name="errors-and-warnings"></a><span data-ttu-id="2056b-123">Erros e Avisos</span><span class="sxs-lookup"><span data-stu-id="2056b-123">Errors and Warnings</span></span>  
 <span data-ttu-id="2056b-124">Os tipos obsoletos e membros geram as seguintes mensagens de erro quando eles são usados.</span><span class="sxs-lookup"><span data-stu-id="2056b-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="2056b-125">Observe que o <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> próprio tipo não é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2056b-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>  
  
 <span data-ttu-id="2056b-126">Aviso de tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="2056b-126">Compile-time warning:</span></span>  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 <span data-ttu-id="2056b-127">Exceção de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="2056b-127">Run-time exception:</span></span>  
  
 <span data-ttu-id="2056b-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="2056b-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="2056b-129">Migração: Substituição para chamadas obsoletas</span><span class="sxs-lookup"><span data-stu-id="2056b-129">Migration: Replacement for Obsolete Calls</span></span>  
  
### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="2056b-130">Determinando o nível de confiança de um Assembly</span><span class="sxs-lookup"><span data-stu-id="2056b-130">Determining an Assembly’s Trust Level</span></span>  
 <span data-ttu-id="2056b-131">Política de CAS geralmente é usada para determinar um assembly ou conceder o conjunto de permissão do domínio de aplicativo ou nível de confiança.</span><span class="sxs-lookup"><span data-stu-id="2056b-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="2056b-132">O [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expõe as seguintes propriedades úteis que não é necessário para resolver a política de segurança:</span><span class="sxs-lookup"><span data-stu-id="2056b-132">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes the following useful properties that do not need to resolve security policy:</span></span>  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a><span data-ttu-id="2056b-133">Área de segurança de domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="2056b-133">Application Domain Sandboxing</span></span>  
 <span data-ttu-id="2056b-134">O <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> método normalmente é usado para configurar de modo seguro os assemblies em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2056b-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="2056b-135">O [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expõe membros que não precisam usar <xref:System.Security.Policy.PolicyLevel> para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="2056b-135">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="2056b-136">Para obter mais informações, consulte [como: executar código parcialmente confiável em uma área restrita](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="2056b-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="2056b-137">Determinar uma permissão de segurança ou razoável parcialmente definida para o código confiável</span><span class="sxs-lookup"><span data-stu-id="2056b-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>  
 <span data-ttu-id="2056b-138">Hosts muitas vezes precisam determinar as permissões que são apropriadas para o código de área restrita hospedado.</span><span class="sxs-lookup"><span data-stu-id="2056b-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="2056b-139">Antes do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], política de CAS fornece uma forma de fazer isso com o <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="2056b-139">Before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2056b-140">Como uma substituição, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] fornece o <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> método, que retorna uma permissão de segurança, o padrão definido para a evidência fornecida.</span><span class="sxs-lookup"><span data-stu-id="2056b-140">As a replacement, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="2056b-141">Cenários de não-Sandboxing: Sobrecargas para cargas de Assembly</span><span class="sxs-lookup"><span data-stu-id="2056b-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>  
 <span data-ttu-id="2056b-142">O motivo para usar uma sobrecarga de carregamento do assembly pode ser usar parâmetros que não estão disponíveis, em vez de modo seguro do assembly.</span><span class="sxs-lookup"><span data-stu-id="2056b-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="2056b-143">Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], sobrecargas de carregamento do assembly que não exigem um <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objeto como um parâmetro, por exemplo, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, habilitar esse cenário.</span><span class="sxs-lookup"><span data-stu-id="2056b-143">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>  
  
 <span data-ttu-id="2056b-144">Se você quiser sandbox um assembly, use o <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="2056b-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="2056b-145">Compatibilidade: Usando a opção de política de CAS herdado</span><span class="sxs-lookup"><span data-stu-id="2056b-145">Compatibility: Using the CAS Policy Legacy Option</span></span>  
 <span data-ttu-id="2056b-146">O [o elemento de configuração < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) permite que você especifique que um processo ou biblioteca usa a política de CAS legada.</span><span class="sxs-lookup"><span data-stu-id="2056b-146">The [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="2056b-147">Quando você habilita esse elemento, as política e evidência sobrecargas funcionará como nas versões anteriores do framework.</span><span class="sxs-lookup"><span data-stu-id="2056b-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2056b-148">Comportamento da diretiva de autoridades de certificação é especificado em uma base de versão de tempo de execução, para que modificar a política de CAS para uma versão de tempo de execução não afeta a política de CAS de outra versão.</span><span class="sxs-lookup"><span data-stu-id="2056b-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2056b-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2056b-149">See Also</span></span>  
 [<span data-ttu-id="2056b-150">Como executar código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="2056b-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
