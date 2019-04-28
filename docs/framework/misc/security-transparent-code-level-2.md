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
ms.openlocfilehash: 9c3970823557d1d1b24405fd4b390b81006533a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868895"
---
# <a name="security-transparent-code-level-2"></a>Código transparente de segurança, nível 2

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Transparência de nível 2 foi introduzida no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Os três tenets desse modelo são código transparente, código segurança-seguro-crítica e código de segurança crítica.

- Código transparente, incluindo o código que está em execução em confiança total, pode chamar outro código transparente ou somente código segurança-seguro-crítica. Ele só pode executar ações permitidas pela permissão de confiança parcial do domínio definido (se houver). O código transparente não pode fazer o seguinte:

  - Executar um <xref:System.Security.CodeAccessPermission.Assert%2A> ou elevação de privilégio.

  - Contém código não seguro ou não verificável.

  - Chame um código crítico diretamente.

  - Chamar código nativo ou código com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

  - Chamar um membro que é protegido por um <xref:System.Security.Permissions.SecurityAction.LinkDemand>.

  - Herda de tipos críticos.

  Além disso, os métodos transparentes não podem substituir métodos virtuais críticos ou implementar métodos críticos da interface.

- Código crítico de segurança é totalmente confiável, mas pode ser chamado pelo código transparent. Ele expõe uma área da superfície limitada de código de confiança total; verificações de exatidão e segurança ocorrem no código crítico.

- Código de segurança crítica pode chamar qualquer código e é totalmente confiável, mas ele não pode ser chamado pelo código transparent.

Esse tópico contém as seguintes seções:

- [Exemplos de uso e comportamentos](#examples)

- [Substituir padrões](#override)

- [Regras de herança](#inheritance)

- [Informações adicionais e regras](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a>Exemplos de Uso e Comportamentos

Para especificar [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] regras (transparência de nível 2), use a anotação a seguir para um assembly:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

Para bloquear nas regras do .NET Framework 2.0 (transparência de nível 1), use a anotação a seguir:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Se você não fazer anotações em um assembly, o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] regras são usadas por padrão. No entanto, a prática recomendada é usar o <xref:System.Security.SecurityRulesAttribute> de atributo, em vez de dependendo do padrão.

### <a name="assembly-wide-annotation"></a>Anotação de todo o assembly

As seguintes regras se aplicam ao uso de atributos no nível de assembly:

- Nenhum atributo: Se você não especificar todos os atributos, o tempo de execução interpreta todos os códigos como crítico de segurança, exceto onde sendo crítico para segurança viola uma regra de herança (por exemplo, quando a substituição ou implementando um transparente virtual ou o método de interface). Nesses casos, os métodos são seguro-crítica. Não especificar nenhum atributo faz com que o common language runtime determinar as regras de transparência para você.

- `SecurityTransparent`: Todo o código é transparente; todo o assembly não fará nada com privilégios ou que não é segura.

- `SecurityCritical`: Todo o código que é introduzido pelos tipos neste assembly é essencial; todos os outros códigos é transparente. Esse cenário é semelhante à especificação não todos os atributos; No entanto, o common language runtime não determina automaticamente as regras de transparência. Por exemplo, se você substituir um método virtual ou abstract ou implementa um método de interface, por padrão, esse método é transparente. Você deve anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical`; caso contrário, um <xref:System.TypeLoadException> será lançada no tempo de carregamento. Essa regra também se aplica quando a classe base e a classe derivada estão no mesmo assembly.

- `AllowPartiallyTrustedCallers` (nível 2 somente): Todo o código padrão é transparente. No entanto, os membros e tipos individuais podem ter outros atributos.

A tabela a seguir compara o comportamento de nível de assembly para o nível 2 com o nível 1.

|Atributo de assembly|Nível 2|Nível 1|
|------------------------|-------------|-------------|
|Nenhum atributo em um assembly parcialmente confiável|Tipos e membros são por padrão transparente, mas podem ser crítico para segurança ou segurança-seguro-crítica.|Todos os tipos e membros são transparentes.|
|Nenhum atributo|Não especificar nenhum atributo faz com que o common language runtime determinar as regras de transparência para você. Todos os tipos e membros são críticos para segurança, exceto onde sendo crítico para segurança viola uma regra de herança.|Em um assembly totalmente confiável (no cache de assembly global ou identificado como confiança total no `AppDomain`) todos os tipos são transparentes e todos os membros são segurança-seguro-crítica.|
|`SecurityTransparent`|Todos os tipos e membros são transparentes.|Todos os tipos e membros são transparentes.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Não aplicável.|Todos os tipos e membros são críticos para segurança.|
|`SecurityCritical`|Todo o código que é introduzido pelos tipos neste assembly é essencial; todos os outros códigos é transparente. Se você substituir um método virtual ou abstract ou implementa um método de interface, você deve anotar explicitamente o método como `SecurityCritical` ou `SecuritySafeCritical`.|Todo o código padrão é transparente. No entanto, os membros e tipos individuais podem ter outros atributos.|

### <a name="type-and-member-annotation"></a>Tipo e Anotação do Membro

Os atributos de segurança que são aplicados a um tipo também se aplicam aos membros que são introduzidos pelo tipo. No entanto, eles não se aplicam ao virtual ou abstract substitui das implementações de interface ou classe base. As seguintes regras se aplicam ao uso de atributos no nível do tipo e membro:

- `SecurityCritical`: O tipo ou membro é crítico e pode ser chamado somente pelo código de confiança total. Métodos que são introduzidos em um tipo crítico de segurança são essenciais.

    > [!IMPORTANT]
    > Métodos abstratos e virtuais que são introduzidos em interfaces ou classes base e substituídos ou implementados em uma classe de segurança críticas são transparentes por padrão. Eles devem ser identificados como `SecuritySafeCritical` ou `SecurityCritical`.

- `SecuritySafeCritical`: O tipo ou membro é crítico. No entanto, o tipo ou membro pode ser chamado no código transparent de (parcialmente confiável) e é tão potentes quanto qualquer outro código crítico. O código deve ser auditado para segurança.

[Voltar ao início](#top)

<a name="override"></a>

## <a name="override-patterns"></a>Substituir Padrões

A tabela a seguir mostra as substituições de método permitidas para a transparência de nível 2.

|Membro de base virtuais/interface|Substituição/interface|
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

- Regras para tipos: Saindo da esquerda para a direita, o acesso se torna mais restritivo. Tipos derivados devam ser, pelo menos, tão restritivos quanto o tipo base.

- Regras para métodos: Métodos derivados não podem alterar a acessibilidade do método base. Para o comportamento padrão, todos os métodos derivados que não são anotados são `Transparent`. Derivados de tipos critical causam uma exceção seja gerada se o método substituído não é anotado explicitamente como `SecurityCritical`.

A tabela a seguir mostra o tipo permitido padrões de herança.

|Classe base|Classe derivada pode ser|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

A tabela a seguir mostra o tipo não permitido em padrões de herança.

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

A tabela a seguir mostra o método não permitido em padrões de herança.

|Método base|Método derivado não pode ser|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Essas regras de herança se aplicam a membros e tipos de nível 2. Tipos em assemblies de nível 1 podem herdar de membros e tipos de segurança crítica de nível 2. Portanto, os membros e tipos de nível 2 devem ter demandas de herança separados para os herdeiros de nível 1.

[Voltar ao início](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a>Informações Adicionais e Regras

### <a name="linkdemand-support"></a>Suporte LinkDemand

O modelo de transparência de nível 2 substitui o <xref:System.Security.Permissions.SecurityAction.LinkDemand> com o <xref:System.Security.SecurityCriticalAttribute> atributo. No código herdado (nível 1), uma <xref:System.Security.Permissions.SecurityAction.LinkDemand> são tratados automaticamente como um <xref:System.Security.Permissions.SecurityAction.Demand>.

### <a name="reflection"></a>Reflexão

Invocar um método crítico ou a leitura de um campo crítica aciona uma demanda para confiança total (como se você invocou um método particular ou campo). Portanto, o código de confiança total pode invocar um método crítico, enquanto o código de confiança parcial não pode.

As propriedades a seguir foram adicionadas para o <xref:System.Reflection> namespace para determinar se o tipo, método ou campo é `SecurityCritical`, `SecuritySafeCritical`, ou `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, e <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Use essas propriedades para determinar a transparência por meio de reflexão em vez de verificar a presença do atributo. As regras de transparência são complexas e verificando o atributo pode não ser suficiente.

> [!NOTE]
> Um `SafeCritical` retorn `true` para ambos <xref:System.Type.IsSecurityCritical%2A> e <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, pois `SafeCritical` é realmente fundamental (ele tem os mesmos recursos que o código critical, mas ele pode ser chamado no código transparent).

Métodos dinâmicos herdam a transparência dos módulos que eles são anexados a; eles não herdam a transparência do tipo (se eles são anexados a um tipo).

### <a name="skip-verification-in-full-trust"></a>Ignorar Verificação em Confiança Total

Você pode ignorar a verificação de assemblies transparentes totalmente confiáveis, definindo o <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> propriedade para `true` no <xref:System.Security.SecurityRulesAttribute> atributo:

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

O <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> é de propriedade `false` por padrão, portanto, a propriedade deve ser definida como `true` para ignorar a verificação. Isso deve ser feito para apenas para fins de otimização. Você deve garantir que o código transparente no assembly é verificável usando o `transparent` opção de [ferramenta PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).

## <a name="see-also"></a>Consulte também

- [Código transparente de segurança, nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [Alterações de segurança](../../../docs/framework/security/security-changes.md)
