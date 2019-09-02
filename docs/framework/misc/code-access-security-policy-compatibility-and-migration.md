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
# <a name="code-access-security-policy-compatibility-and-migration"></a>Compatibilidade de políticas de segurança de acesso de código e migração

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

A parte da política da CAS (segurança de acesso do código) tornou-se obsoleta no .NET Framework 4. Como resultado, você poderá encontrar avisos de compilação e exceções de tempo de execução se chamar os tipos de política e os membros obsoletos [explicitamente](#explicit_use) ou [implicitamente](#implicit_use) (por meio de outros tipos e membros).

Você pode evitar os avisos e erros de uma das opções:

- [Migrar](#migration) para as .NET Framework 4 substituições para as chamadas obsoletas.

   \- ou -

- Usando o [ \<elemento de configuração NetFx40_LegacySecurityPolicy >](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) para aceitar o comportamento da política CAS herdada.

Esse tópico contém as seguintes seções:

- [Uso explícito](#explicit_use)

- [Uso implícito](#implicit_use)

- [Erros e avisos](#errors_and_warnings)

- [As Substituição de chamadas obsoletas](#migration)

- [Compatibilidade Usando a opção herdada da política CAS](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a>Uso explícito

Os membros que manipulam diretamente a política de segurança ou exigem que a política de CAS para a área restrita sejam obsoletos e produzirão erros por padrão.

Os exemplos são:

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

## <a name="implicit-use"></a>Uso implícito

Várias sobrecargas de carregamento de assembly geram erros devido ao uso implícito da política de CAS. Essas sobrecargas usam um <xref:System.Security.Policy.Evidence> parâmetro que é usado para resolver a política de CAS e fornecem um conjunto de concessão de permissão para um assembly.

Aqui estão alguns exemplos. As sobrecargas obsoletas são as que <xref:System.Security.Policy.Evidence> usam como um parâmetro:

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

## <a name="errors-and-warnings"></a>Erros e Avisos

Os tipos e membros obsoletos produzem as seguintes mensagens de erro quando são usadas. Observe que o <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> tipo em si não é obsoleto.

Aviso de tempo de compilação:

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

Exceção de tempo de execução:

<xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a>As Substituição de chamadas obsoletas

### <a name="determining-an-assemblys-trust-level"></a>Determinando o nível de confiança de um assembly

A política de CAS é geralmente usada para determinar o nível de confiança ou o conjunto de concessão de permissão de um domínio do aplicativo ou do assembly. O .NET Framework 4 expõe as seguintes propriedades úteis que não precisam resolver a política de segurança:

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a>Área restrita do domínio do aplicativo

Normalmente <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> , o método é usado para proteger os assemblies em um domínio de aplicativo. O .NET Framework 4 expõe Membros que não precisam ser usados <xref:System.Security.Policy.PolicyLevel> para essa finalidade. Para obter mais informações, confira [Como: Executar o código parcialmente confiável em uma área restrita](how-to-run-partially-trusted-code-in-a-sandbox.md).

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Determinando um conjunto de permissões seguro ou razoável para código parcialmente confiável

Geralmente, os hosts precisam determinar as permissões apropriadas para o código hospedado de área restrita. Antes da .NET Framework 4, a política de CAS forneceu uma maneira de fazer <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> isso com o método. Como uma substituição, o .NET Framework 4 fornece <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> o método, que retorna um conjunto de permissões seguro e padrão para a evidência fornecida.

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Cenários que não são de área restrita: Sobrecargas para cargas de assembly

O motivo para usar uma sobrecarga de carga de assembly pode ser usar parâmetros que não estão disponíveis de outra forma, em vez de colocar o assembly em área restrita. Começando com o .NET Framework 4, as sobrecargas de carregamento de assembly que não <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> exigem um objeto como parâmetro, por <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>exemplo, habilitam esse cenário.

Se você quiser colocar um assembly em área restrita, <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> use a sobrecarga.

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Compatibilidade Usando a opção herdada da política CAS

O [ \<elemento de configuração de > NetFx40_LegacySecurityPolicy](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) permite especificar que um processo ou uma biblioteca usa uma política CAS herdada. Quando você habilitar esse elemento, as sobrecargas de política e evidência funcionarão como faziam em versões anteriores do Framework.

> [!NOTE]
> O comportamento da política de CAS é especificado em uma base de versão de tempo de execução, portanto, a modificação da política de CAS para uma versão de tempo de execução não afeta a política CAS de outra versão.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Consulte também

- [Como: Executar o código parcialmente confiável em uma área restrita](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
