---
title: Código transparente de segurança, nível 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f15c3bc097bc034db41c95cd168104b8435aaf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394134"
---
# <a name="security-transparent-code-level-2"></a>Código transparente de segurança, nível 2
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Transparência de nível 2 foi introduzida no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Os três princípios desse modelo são código transparente, código de segurança crítica segura e código crítico de segurança.  
  
-   Código transparente, incluindo o código que está executando em confiança total, pode chamar outro código transparente ou somente código de segurança crítica segura. Ele só pode executar ações permitidas pela permissão de confiança parcial do domínio definido (se houver). Código transparente não pode fazer o seguinte:  
  
    -   Executar um <xref:System.Security.CodeAccessPermission.Assert%2A> ou elevação de privilégio.  
  
    -   Contém o código não confiável ou.  
  
    -   Chame diretamente o código crítico.  
  
    -   Chamar código nativo ou com o código de <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.  
  
    -   Chamar um membro que é protegido por um <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Herda de tipos críticos.  
  
     Além disso, os métodos transparentes não é possível substituir métodos virtuais críticos ou implementar métodos de interface crítico.  
  
-   Código crítico de segurança é totalmente confiável, mas pode ser chamado por código transparente. Ela expõe uma área da superfície limitada do código de confiança total; verificações de integridade e segurança acontecem no código crítico para segurança.  
  
-   Código crítico de segurança pode chamar qualquer código e é totalmente confiável, mas ele não pode ser chamado por código transparente.  
  
 Esse tópico contém as seguintes seções:  
  
-   [Comportamentos e exemplos de uso](#examples)  
  
-   [Padrões de substituição](#override)  
  
-   [Regras de herança](#inheritance)  
  
-   [Regras e informações adicionais](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a>Exemplos de Uso e Comportamentos  
 Para especificar [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] regras (transparência de nível 2), use a anotação a seguir para um assembly:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 Para bloquear nas regras do .NET Framework 2.0 (transparência de nível 1), use a anotação a seguir:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Se você não anotar um assembly, o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] regras são usadas por padrão. No entanto, a prática recomendada é usar o <xref:System.Security.SecurityRulesAttribute> de atributo, em vez de dependendo do padrão.  
  
### <a name="assembly-wide-annotation"></a>Anotação de todo o assembly  
 As seguintes regras se aplicam ao uso de atributos em nível de assembly:  
  
-   Nenhum atributo: se você não especificar os atributos, o tempo de execução interpreta todo o código como críticas de segurança, exceto onde sendo críticas de segurança viola uma regra de herança (por exemplo, ao substituir ou implementar um transparente virtual ou o método de interface ). Nesses casos, os métodos são crítico para segurança. Não especificar nenhum atributo faz com que o common language runtime determinar as regras de transparência para você.  
  
-   `SecurityTransparent`: Todo o código é transparente; o conjunto inteiro não fará nada privilegiada ou não seguro.  
  
-   `SecurityCritical`: Todo o código que é apresentado pelo tipos neste assembly é importante; todos os outros códigos é transparente. Este cenário é semelhante à especificação não todos os atributos; No entanto, o common language runtime não determinar automaticamente as regras de transparência. Por exemplo, se você substituir um método virtual ou abstrato ou implementa um método de interface, por padrão, esse método é transparente. Você deve explicitamente anotar o método como `SecurityCritical` ou `SecuritySafeCritical`; caso contrário, um <xref:System.TypeLoadException> será lançada em tempo de carregamento. Esta regra também se aplica quando a classe base e a classe derivada no mesmo assembly.  
  
-   `AllowPartiallyTrustedCallers` (nível 2 somente): todos os padrões para transparente de código. No entanto, membros e tipos individuais podem ter outros atributos.  
  
 A tabela a seguir compara o comportamento de nível de assembly para o nível 2 com o nível 1.  
  
|Atributo de assembly|Nível 2|Nível 1|  
|------------------------|-------------|-------------|  
|Nenhum atributo em um assembly parcialmente confiável|Tipos e membros são por padrão transparente, mas podem ser crítico de segurança ou segurança crítica safe.|Todos os tipos e membros são transparentes.|  
|Nenhum atributo|Não especificar nenhum atributo faz com que o common language runtime determinar as regras de transparência para você. Todos os tipos e membros são críticas de segurança, exceto onde sendo críticas de segurança viola uma regra de herança.|Em um assembly totalmente confiável (no cache de assembly global ou identificado como confiança total no `AppDomain`) todos os tipos são transparentes e todos os membros são safe-crítico de segurança.|  
|`SecurityTransparent`|Todos os tipos e membros são transparentes.|Todos os tipos e membros são transparentes.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Não aplicável.|Todos os tipos e membros são críticas de segurança.|  
|`SecurityCritical`|Todo o código que é apresentado pelo tipos neste assembly é importante; todos os outros códigos é transparente. Se você substituir um método virtual ou abstrato ou implementa um método de interface, você deve explicitamente anotar o método como `SecurityCritical` ou `SecuritySafeCritical`.|Todos os padrões para transparente de código. No entanto, membros e tipos individuais podem ter outros atributos.|  
  
### <a name="type-and-member-annotation"></a>Tipo e Anotação do Membro  
 Os atributos de segurança que são aplicados a um tipo também se aplicam aos membros que são introduzidos pelo tipo. No entanto, eles não se aplicam ao virtual ou abstrato substitui as implementações de interface ou classe base. As seguintes regras se aplicam ao uso de atributos em nível de tipo e membro:  
  
-   `SecurityCritical`: O tipo ou membro é fundamental e pode ser chamado apenas pelo código de confiança total. Os métodos que foram introduzidos em um tipo crítico de segurança são essenciais.  
  
    > [!IMPORTANT]
    >  Métodos abstratos e virtuais que são introduzidos no interfaces ou classes base e substituídos ou implementados em uma classe críticas de segurança são transparentes por padrão. Eles devem ser identificados como `SecuritySafeCritical` ou `SecurityCritical`.  
  
-   `SecuritySafeCritical`: O tipo ou membro é crítico para segurança. No entanto, o tipo ou membro pode ser chamado de código (parcialmente confiável) transparente e é capaz como qualquer outro código crítico. O código deve ser auditado para segurança.  
  
 [Voltar ao início](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a>Substituir Padrões  
 A tabela a seguir mostra as substituições de método permitidas para a transparência de nível 2.  
  
|Membro de base virtual/de interface|Substituição/de interface|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [Voltar ao início](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a>Regras de Herança  
 Nesta seção, a ordem a seguir é atribuída a `Transparent`, `Critical`, e `SafeCritical` código com base no acesso e recursos:  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   Regras para tipos: vai da esquerda para a direita, acesso se torna mais restritivo. Tipos derivados devem ser pelo menos tão restritivos quanto o tipo base.  
  
-   Regras para métodos: métodos derivados não é possível alterar a acessibilidade do método base. Para o comportamento padrão, todos os métodos derivados que são anotados não são `Transparent`. Derivados dos tipos críticos causam uma exceção seja lançada se o método substituído não é anotado explicitamente como `SecurityCritical`.  
  
 A tabela a seguir mostra o tipo permitido padrões de herança.  
  
|Classe base|Classe derivada pode ser|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 A tabela a seguir mostra o tipo não permitido padrões de herança.  
  
|Classe base|Classe derivada não pode ser|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 A tabela a seguir mostra o método permitido padrões de herança.  
  
|Método base|Método derivado pode ser|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 A tabela a seguir mostra o método não permitido padrões de herança.  
  
|Método base|Método derivado não pode ser|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  Essas regras de herança se aplicam a membros e tipos de nível 2. Tipos em assemblies de nível 1 podem herdar de membros e tipos de segurança crítica de nível 2. Portanto, os membros e tipos de nível 2 devem ter demandas de herança separados para os herdeiros de nível 1.  
  
 [Voltar ao início](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a>Informações Adicionais e Regras  
  
### <a name="linkdemand-support"></a>Suporte LinkDemand  
 O modelo de transparência de nível 2 substitui o <xref:System.Security.Permissions.SecurityAction.LinkDemand> com o <xref:System.Security.SecurityCriticalAttribute> atributo. No código herdado (nível 1), um <xref:System.Security.Permissions.SecurityAction.LinkDemand> automaticamente é tratado como um <xref:System.Security.Permissions.SecurityAction.Demand>.  
  
### <a name="reflection"></a>Reflexão  
 Invocando um método crítico ou a leitura de um campo crítico dispara uma solicitação de confiança total (como se você invocou um campo ou método particular). Portanto, o código de confiança total pode invocar um método crítico, enquanto que o código parcialmente confiável não pode.  
  
 As propriedades a seguir foram adicionadas para o <xref:System.Reflection> namespace para determinar se o tipo, método ou campo é `SecurityCritical`, `SecuritySafeCritical`, ou `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, e <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Use essas propriedades para determinar a transparência por meio de reflexão em vez de verificar a presença do atributo. As regras de transparência são complexas e verificando o atributo pode não ser suficiente.  
  
> [!NOTE]
>  Um `SafeCritical` método retorna `true` para ambos <xref:System.Type.IsSecurityCritical%2A> e <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, pois `SafeCritical` é realmente importante (ele tem as mesmas capacidades de código crítico, mas ele pode ser chamado de código de transparência).  
  
 Métodos dinâmicos herdam a transparência de módulos que estão conectados a; eles não herdam a transparência do tipo (se eles estão conectados a um tipo).  
  
### <a name="skip-verification-in-full-trust"></a>Ignorar Verificação em Confiança Total  
 Você pode ignorar a verificação para totalmente confiáveis assemblies transparentes, definindo o <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> propriedade `true` no <xref:System.Security.SecurityRulesAttribute> atributo:  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 O <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> é de propriedade `false` por padrão, então a propriedade deve ser definida como `true` para ignorar a verificação. Isso deve ser feito apenas a fins de otimização. Você deve garantir que o código de transparência no assembly é verificado usando o `transparent` opção o [ferramenta PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).  
  
## <a name="see-also"></a>Consulte também  
 [Código transparente de segurança, nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [Alterações de segurança](../../../docs/framework/security/security-changes.md)
