---
title: Compatibilidade de políticas de segurança de acesso de código e migração
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 219b511662a2e59fb6e0e55b6630bd54015fcc79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620091"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Compatibilidade de políticas de segurança de acesso de código e migração
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 A parte da política de segurança de acesso do código (CAS) se tornou obsoleta o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Como resultado, você pode encontrar avisos de compilação e exceções de tempo de execução se você chamar os tipos de política obsoleto e membros [explicitamente](#explicit_use) ou [implicitamente](#implicit_use) (por meio de outros tipos e membros).  
  
 Você pode evitar os avisos e erros por qualquer um:  
  
-   [Migrando](#migration) para o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] substituições para as chamadas obsoletas.  
  
     \- ou -  
  
-   Usando o [o elemento de configuração < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) aceitar o comportamento herdado de política de CAS.  
  
 Esse tópico contém as seguintes seções:  
  
-   [Uso explícito](#explicit_use)  
  
-   [Uso implícito](#implicit_use)  
  
-   [Erros e avisos](#errors_and_warnings)  
  
-   [Migração: Substituição para chamadas obsoletas](#migration)  
  
-   [Compatibilidade: Usando a opção de política CAS herdada](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a>Uso explícito  
 Membros que manipulam a política de segurança diretamente ou exigem a política de CAS para a área restrita são obsoletos e gerarão erros por padrão.  
  
 Exemplos disso são:  
  
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
## <a name="implicit-use"></a>Uso implícito  
 Carregamento de assembly várias sobrecargas produzir erros devido ao seu uso implícito de política de CAS. Essas sobrecargas usam uma <xref:System.Security.Policy.Evidence> parâmetro que é usado para resolver a política de CAS e fornecer uma permissão de conceder o conjunto para um assembly.  
  
 Aqui estão alguns exemplos. As sobrecargas obsoletas são aquelas que levam <xref:System.Security.Policy.Evidence> como um parâmetro:  
  
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
## <a name="errors-and-warnings"></a>Erros e Avisos  
 Os tipos e membros obsoletos geram as seguintes mensagens de erro quando eles são usados. Observe que o <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> tipo em si não está obsoleto.  
  
 Aviso de tempo de compilação:  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 Exceção de tempo de execução:  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a>Migração: Substituição para chamadas obsoletas  
  
### <a name="determining-an-assemblys-trust-level"></a>Determinar o nível de confiança do Assembly  
 Política de CAS geralmente é usada para determinar um assembly ou conceder o conjunto de permissão do domínio de aplicativo ou nível de confiança. O [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expõe as seguintes propriedades úteis que não é necessário para resolver a política de segurança:  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a>Área restrita de domínio de aplicativo  
 O <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> método normalmente é usado para a área restrita os assemblies em um domínio do aplicativo. O [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expõe membros que não precisa usar <xref:System.Security.Policy.PolicyLevel> para essa finalidade. Para obter mais informações, confira [Como: Executar código parcialmente confiável em uma área restrita](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Determinar uma permissão de segurança ou razoável parcialmente definidos para um código confiável  
 Hosts geralmente precisam determinar as permissões apropriadas para o código de modo seguro hospedado. Antes do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], a política de CAS fornecida uma maneira de fazer isso com o <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> método. Como um substituto [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] fornece o <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> método, que retorna uma permissão de segurança, standard definida para a evidência fornecida.  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Cenários de não-Sandboxing: Sobrecargas para carregamentos de Assembly  
 O motivo para usar uma sobrecarga de carregamento de assembly pode ser usar parâmetros que não estão disponíveis, em vez de áreas de segurança do assembly. Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], sobrecargas de carregamento de assembly que não exigem uma <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objeto como um parâmetro, por exemplo, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, habilitar esse cenário.  
  
 Se você quiser para a área restrita um assembly, use o <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> de sobrecarga.  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Compatibilidade: Usando a opção de política CAS herdada  
 O [o elemento de configuração < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) permite que você especifique que um processo ou a biblioteca usa a política CAS herdada. Quando você habilita esse elemento, as sobrecargas de diretiva e evidência funcionará como ocorria nas versões anteriores do framework.  
  
> [!NOTE]
>  Comportamento da política de CAS é especificado em uma base de versão de tempo de execução, portanto, a modificação de política de CAS para uma versão de tempo de execução não afeta a política de CAS de outra versão.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também
- [Como: Executar código parcialmente confiável em uma área restrita](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
