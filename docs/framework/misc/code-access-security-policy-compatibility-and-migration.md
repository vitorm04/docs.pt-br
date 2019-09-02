---
title: Compatibilidade de políticas de segurança de acesso de código e migração
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9563dae9ba5d144300549e7f33f5f5a9feb1d410
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205643"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="66acd-102">Compatibilidade de políticas de segurança de acesso de código e migração</span><span class="sxs-lookup"><span data-stu-id="66acd-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="66acd-103">A parte da política da CAS (segurança de acesso do código) tornou-se obsoleta no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="66acd-103">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="66acd-104">Como resultado, você poderá encontrar avisos de compilação e exceções de tempo de execução se chamar os tipos de política e os membros obsoletos [explicitamente](#explicit_use) ou [implicitamente](#implicit_use) (por meio de outros tipos e membros).</span><span class="sxs-lookup"><span data-stu-id="66acd-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="66acd-105">Você pode evitar os avisos e erros de uma das opções:</span><span class="sxs-lookup"><span data-stu-id="66acd-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="66acd-106">[Migrar](#migration) para as .NET Framework 4 substituições para as chamadas obsoletas.</span><span class="sxs-lookup"><span data-stu-id="66acd-106">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="66acd-107">\- ou -</span><span class="sxs-lookup"><span data-stu-id="66acd-107">\- or -</span></span>

- <span data-ttu-id="66acd-108">Usando o [ \<elemento de configuração NetFx40_LegacySecurityPolicy >](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) para aceitar o comportamento da política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="66acd-108">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="66acd-109">Esse tópico contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="66acd-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="66acd-110">Uso explícito</span><span class="sxs-lookup"><span data-stu-id="66acd-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="66acd-111">Uso implícito</span><span class="sxs-lookup"><span data-stu-id="66acd-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="66acd-112">Erros e avisos</span><span class="sxs-lookup"><span data-stu-id="66acd-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="66acd-113">As Substituição de chamadas obsoletas</span><span class="sxs-lookup"><span data-stu-id="66acd-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="66acd-114">Compatibilidade Usando a opção herdada da política CAS</span><span class="sxs-lookup"><span data-stu-id="66acd-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="66acd-115">Uso explícito</span><span class="sxs-lookup"><span data-stu-id="66acd-115">Explicit Use</span></span>

<span data-ttu-id="66acd-116">Os membros que manipulam diretamente a política de segurança ou exigem que a política de CAS para a área restrita sejam obsoletos e produzirão erros por padrão.</span><span class="sxs-lookup"><span data-stu-id="66acd-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="66acd-117">Os exemplos são:</span><span class="sxs-lookup"><span data-stu-id="66acd-117">Examples of these are:</span></span>

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a><span data-ttu-id="66acd-118">Uso implícito</span><span class="sxs-lookup"><span data-stu-id="66acd-118">Implicit Use</span></span>

<span data-ttu-id="66acd-119">Várias sobrecargas de carregamento de assembly geram erros devido ao uso implícito da política de CAS.</span><span class="sxs-lookup"><span data-stu-id="66acd-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="66acd-120">Essas sobrecargas usam um <xref:System.Security.Policy.Evidence> parâmetro que é usado para resolver a política de CAS e fornecem um conjunto de concessão de permissão para um assembly.</span><span class="sxs-lookup"><span data-stu-id="66acd-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="66acd-121">Aqui estão alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="66acd-121">Here are some examples.</span></span> <span data-ttu-id="66acd-122">As sobrecargas obsoletas são as que <xref:System.Security.Policy.Evidence> usam como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="66acd-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a><span data-ttu-id="66acd-123">Erros e Avisos</span><span class="sxs-lookup"><span data-stu-id="66acd-123">Errors and Warnings</span></span>

<span data-ttu-id="66acd-124">Os tipos e membros obsoletos produzem as seguintes mensagens de erro quando são usadas.</span><span class="sxs-lookup"><span data-stu-id="66acd-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="66acd-125">Observe que o <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> tipo em si não é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="66acd-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="66acd-126">Aviso de tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="66acd-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="66acd-127">Exceção de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="66acd-127">Run-time exception:</span></span>

<span data-ttu-id="66acd-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="66acd-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="66acd-129">As Substituição de chamadas obsoletas</span><span class="sxs-lookup"><span data-stu-id="66acd-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="66acd-130">Determinando o nível de confiança de um assembly</span><span class="sxs-lookup"><span data-stu-id="66acd-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="66acd-131">A política de CAS é geralmente usada para determinar o nível de confiança ou o conjunto de concessão de permissão de um domínio do aplicativo ou do assembly.</span><span class="sxs-lookup"><span data-stu-id="66acd-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="66acd-132">O .NET Framework 4 expõe as seguintes propriedades úteis que não precisam resolver a política de segurança:</span><span class="sxs-lookup"><span data-stu-id="66acd-132">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="66acd-133">Área restrita do domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="66acd-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="66acd-134">Normalmente <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> , o método é usado para proteger os assemblies em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="66acd-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="66acd-135">O .NET Framework 4 expõe Membros que não precisam ser usados <xref:System.Security.Policy.PolicyLevel> para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="66acd-135">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="66acd-136">Para obter mais informações, confira [Como: Executar o código parcialmente confiável em uma área restrita](how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="66acd-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="66acd-137">Determinando um conjunto de permissões seguro ou razoável para código parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="66acd-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="66acd-138">Geralmente, os hosts precisam determinar as permissões apropriadas para o código hospedado de área restrita.</span><span class="sxs-lookup"><span data-stu-id="66acd-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="66acd-139">Antes da .NET Framework 4, a política de CAS forneceu uma maneira de fazer <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> isso com o método.</span><span class="sxs-lookup"><span data-stu-id="66acd-139">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="66acd-140">Como uma substituição, o .NET Framework 4 fornece <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> o método, que retorna um conjunto de permissões seguro e padrão para a evidência fornecida.</span><span class="sxs-lookup"><span data-stu-id="66acd-140">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="66acd-141">Cenários que não são de área restrita: Sobrecargas para cargas de assembly</span><span class="sxs-lookup"><span data-stu-id="66acd-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="66acd-142">O motivo para usar uma sobrecarga de carga de assembly pode ser usar parâmetros que não estão disponíveis de outra forma, em vez de colocar o assembly em área restrita.</span><span class="sxs-lookup"><span data-stu-id="66acd-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="66acd-143">Começando com o .NET Framework 4, as sobrecargas de carregamento de assembly que não <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> exigem um objeto como parâmetro, por <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>exemplo, habilitam esse cenário.</span><span class="sxs-lookup"><span data-stu-id="66acd-143">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="66acd-144">Se você quiser colocar um assembly em área restrita, <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> use a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="66acd-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="66acd-145">Compatibilidade Usando a opção herdada da política CAS</span><span class="sxs-lookup"><span data-stu-id="66acd-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="66acd-146">O [ \<elemento de configuração de > NetFx40_LegacySecurityPolicy](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) permite especificar que um processo ou uma biblioteca usa uma política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="66acd-146">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="66acd-147">Quando você habilitar esse elemento, as sobrecargas de política e evidência funcionarão como faziam em versões anteriores do Framework.</span><span class="sxs-lookup"><span data-stu-id="66acd-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="66acd-148">O comportamento da política de CAS é especificado em uma base de versão de tempo de execução, portanto, a modificação da política de CAS para uma versão de tempo de execução não afeta a política CAS de outra versão.</span><span class="sxs-lookup"><span data-stu-id="66acd-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="66acd-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66acd-149">See also</span></span>

- [<span data-ttu-id="66acd-150">Como: Executar o código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="66acd-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="66acd-151">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="66acd-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
