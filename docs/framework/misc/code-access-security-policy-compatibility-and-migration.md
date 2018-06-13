---
title: Compatibilidade de políticas de segurança de acesso de código e migração
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5007e07340621fa76dc37a48eaf8c17bc048339
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393241"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Compatibilidade de políticas de segurança de acesso de código e migração
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 A parte da política de segurança de acesso ao código (CAS) se tornou obsoleta no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Como resultado, você pode encontrar avisos de compilação e exceções de tempo de execução se você chamar os tipos de política obsoleto e membros [explicitamente](#explicit_use) ou [implicitamente](#implicit_use) (por meio de outros tipos e membros).  
  
 Você pode evitar os erros e avisos ao:  
  
-   [Migrando](#migration) para o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] substituições para as chamadas obsoletas.  
  
     \- ou -  
  
-   Usando o [o elemento de configuração < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) para aceitar o comportamento de política de CAS herdado.  
  
 Esse tópico contém as seguintes seções:  
  
-   [Uso explícito](#explicit_use)  
  
-   [Uso implícito](#implicit_use)  
  
-   [Erros e avisos](#errors_and_warnings)  
  
-   [Migração: Substituição para chamadas obsoletas](#migration)  
  
-   [Compatibilidade: Usando a opção de política de CAS herdado](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a>Uso explícito  
 Membros que diretamente manipulam a política de segurança ou exigem a política de CAS para a área restrita estão obsoletos e gerarão erros por padrão.  
  
 Exemplos são:  
  
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
 Carregamento do assembly várias sobrecargas produzir erros devido a seu uso implícito de política de CAS. Essas sobrecargas usam uma <xref:System.Security.Policy.Evidence> parâmetro que é usado para resolver a política de CAS e fornecer uma permissão de conceder o conjunto para um assembly.  
  
 Aqui estão alguns exemplos. As sobrecargas obsoletas são aqueles que usam <xref:System.Security.Policy.Evidence> como um parâmetro:  
  
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
 Os tipos obsoletos e membros geram as seguintes mensagens de erro quando eles são usados. Observe que o <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> próprio tipo não é obsoleto.  
  
 Aviso de tempo de compilação:  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 Exceção de tempo de execução:  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a>Migração: Substituição para chamadas obsoletas  
  
### <a name="determining-an-assemblys-trust-level"></a>Determinando o nível de confiança de um Assembly  
 Política de CAS geralmente é usada para determinar um assembly ou conceder o conjunto de permissão do domínio de aplicativo ou nível de confiança. O [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expõe as seguintes propriedades úteis que não é necessário para resolver a política de segurança:  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a>Área de segurança de domínio de aplicativo  
 O <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> método normalmente é usado para configurar de modo seguro os assemblies em um domínio de aplicativo. O [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] expõe membros que não precisam usar <xref:System.Security.Policy.PolicyLevel> para essa finalidade. Para obter mais informações, consulte [como: executar código parcialmente confiável em uma área restrita](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Determinar uma permissão de segurança ou razoável parcialmente definida para o código confiável  
 Hosts muitas vezes precisam determinar as permissões que são apropriadas para o código de área restrita hospedado. Antes do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], política de CAS fornece uma forma de fazer isso com o <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> método. Como uma substituição, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] fornece o <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> método, que retorna uma permissão de segurança, o padrão definido para a evidência fornecida.  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Cenários de não-Sandboxing: Sobrecargas para cargas de Assembly  
 O motivo para usar uma sobrecarga de carregamento do assembly pode ser usar parâmetros que não estão disponíveis, em vez de modo seguro do assembly. Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], sobrecargas de carregamento do assembly que não exigem um <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objeto como um parâmetro, por exemplo, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, habilitar esse cenário.  
  
 Se você quiser sandbox um assembly, use o <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> de sobrecarga.  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Compatibilidade: Usando a opção de política de CAS herdado  
 O [o elemento de configuração < NetFx40_LegacySecurityPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) permite que você especifique que um processo ou biblioteca usa a política de CAS legada. Quando você habilita esse elemento, as política e evidência sobrecargas funcionará como nas versões anteriores do framework.  
  
> [!NOTE]
>  Comportamento da diretiva de autoridades de certificação é especificado em uma base de versão de tempo de execução, para que modificar a política de CAS para uma versão de tempo de execução não afeta a política de CAS de outra versão.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como executar código parcialmente confiável em uma área restrita](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
