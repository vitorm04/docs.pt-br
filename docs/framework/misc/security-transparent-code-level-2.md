---
title: Código transparente de segurança, nível 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 12e991e4977b0866343158c05681ddf4bd0c869b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645726"
---
# <a name="security-transparent-code-level-2"></a>Código transparente de segurança, nível 2

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

A transparência nível 2 foi introduzida no Quadro .NET 4. Os três princípios deste modelo são código transparente, código crítico de segurança e código crítico de segurança.

- O código transparente, incluindo o código que está sendo executado como confiança total, pode chamar outro código transparente ou código crítico de segurança apenas. Ele só pode executar ações permitidas pelo conjunto de permissão de confiança parcial do domínio (se existir). O código transparente não pode fazer o seguinte:

  - Realizar <xref:System.Security.CodeAccessPermission.Assert%2A> uma ou elevação de privilégios.

  - Contenha código inseguro ou inverificável.

  - Chame diretamente código crítico.

  - Ligue para código ou <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> código nativo com o atributo.

  - Ligue para um membro <xref:System.Security.Permissions.SecurityAction.LinkDemand>que é protegido por um .

  - Herdar de tipos críticos.

  Além disso, métodos transparentes não podem substituir métodos virtuais críticos ou implementar métodos críticos de interface.

- O código de segurança é totalmente confiável, mas pode ser callable por código transparente. Expõe uma área de superfície limitada de código de confiança total; correção e verificações de segurança acontecem em código de segurança-crítica.

- O código crítico de segurança pode chamar qualquer código e é totalmente confiável, mas não pode ser chamado por código transparente.

## <a name="usage-examples-and-behaviors"></a>Exemplos de Uso e Comportamentos

Para especificar as regras do Quadro .NET 4 (transparência nível 2), use a seguinte anotação para uma montagem:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

Para bloquear as regras do Quadro .NET 2.0 (transparência nível 1), use a seguinte anotação:

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

Se você não anotar um conjunto, as regras do .NET Framework 4 serão usadas por padrão. No entanto, a melhor prática <xref:System.Security.SecurityRulesAttribute> recomendada é usar o atributo em vez de depender do padrão.

### <a name="assembly-wide-annotation"></a>Anotação em toda a montagem

As seguintes regras aplicam-se ao uso de atributos no nível de montagem:

- Sem atributos: Se você não especificar nenhum atributo, o tempo de execução interpretará todo o código como crítico de segurança, exceto quando ser crítico de segurança viola uma regra de herança (por exemplo, ao sobrepor ou implementar um método virtual ou de interface transparente). Nesses casos, os métodos são seguros e críticos. Especificar nenhum atributo faz com que o tempo de execução do idioma comum determine as regras de transparência para você.

- `SecurityTransparent`: Todos os códigos são transparentes; toda a assembléia não fará nada privilegiado ou inseguro.

- `SecurityCritical`: Todo o código introduzido por tipos nesta montagem é crítico; todos os outros códigos são transparentes. Este cenário é semelhante ao não especificar nenhum atributo; no entanto, o tempo de execução do idioma comum não determina automaticamente as regras de transparência. Por exemplo, se você substituir um método virtual ou abstrato ou implementar um método de interface, por padrão, esse método é transparente. Você deve anotar explicitamente o `SecurityCritical` método `SecuritySafeCritical`como ou; caso contrário, <xref:System.TypeLoadException> um será jogado na hora da carga. Esta regra também se aplica quando tanto a classe base quanto a classe derivada estão na mesma montagem.

- `AllowPartiallyTrustedCallers`(somente nível 2): Todos os padrões de código são transparentes. No entanto, tipos individuais e membros podem ter outros atributos.

A tabela a seguir compara o comportamento do nível de montagem para o Nível 2 com o Nível 1.

|Atributo de assembly|Nível 2|Nível 1|
|------------------------|-------------|-------------|
|Nenhum atributo em uma assembléia parcialmente confiável|Os tipos e membros são transparentes por padrão, mas podem ser críticos à segurança ou críticos à segurança.|Todos os tipos e membros são transparentes.|
|Nenhum atributo|Especificar nenhum atributo faz com que o tempo de execução do idioma comum determine as regras de transparência para você. Todos os tipos e membros são críticos à segurança, exceto quando ser crítico de segurança viola uma regra de herança.|Em uma montagem totalmente confiável (no cache de montagem `AppDomain`global ou identificada como total confiança no ) todos os tipos são transparentes e todos os membros são críticos à segurança.|
|`SecurityTransparent`|Todos os tipos e membros são transparentes.|Todos os tipos e membros são transparentes.|
|`SecurityCritical(SecurityCriticalScope.Everything)`|Não aplicável.|Todos os tipos e membros são críticos à segurança.|
|`SecurityCritical`|Todo o código introduzido por tipos neste conjunto é crítico; todos os outros códigos são transparentes. Se você substituir um método virtual ou abstrato ou implementar um método `SecurityCritical` de `SecuritySafeCritical`interface, você deve anotar explicitamente o método como ou .|Todos os códigos são padrão transparentes. No entanto, tipos individuais e membros podem ter outros atributos.|

### <a name="type-and-member-annotation"></a>Tipo e Anotação do Membro

Os atributos de segurança aplicados a um tipo também se aplicam aos membros que são introduzidos pelo tipo. No entanto, eles não se aplicam a substituições virtuais ou abstratas da classe base ou implementações de interface. As seguintes regras aplicam-se ao uso de atributos no tipo e no nível do membro:

- `SecurityCritical`: O tipo ou membro é crítico e só pode ser chamado por código de confiança total. Os métodos introduzidos em um tipo crítico de segurança são críticos.

    > [!IMPORTANT]
    > Os métodos virtuais e abstratos que são introduzidos em classes ou interfaces básicas e substituídos ou implementados em uma classe crítica de segurança são transparentes por padrão. Eles devem ser `SecuritySafeCritical` identificados como `SecurityCritical`ou.

- `SecuritySafeCritical`: O tipo ou membro é seguro-crítico. No entanto, o tipo ou membro pode ser chamado de código transparente (parcialmente confiável) e é tão capaz quanto qualquer outro código crítico. O código deve ser auditado por segurança.

## <a name="override-patterns"></a>Substituir Padrões

A tabela a seguir mostra que o método substitui permitido a transparência nível 2.

|Membro de interface/virtual base|Substituição/interface|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a>Regras de Herança

Nesta seção, a seguinte ordem `Transparent` `Critical`é `SafeCritical` atribuída a , e código com base no acesso e recursos:

`Transparent` < `SafeCritical` < `Critical`

- Regras para tipos: Indo da esquerda para a direita, o acesso se torna mais restritivo. Os tipos derivados devem ser pelo menos tão restritivos quanto o tipo de base.

- Regras para métodos: Os métodos derivados não podem alterar a acessibilidade do método base. Para o comportamento padrão, todos os métodos derivados que não são anotados são `Transparent`. Derivativos de tipos críticos fazem com que uma exceção seja lançada `SecurityCritical`se o método substituído não for explicitamente anotado como .

A tabela a seguir mostra os padrões de herança do tipo permitidos.

|Classe base|Classe derivada pode ser|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

A tabela a seguir mostra os padrões de herança do tipo proibidos.

|Classe base|Classe derivada não pode ser|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

A tabela a seguir mostra os padrões de herança do método permitido.

|Método base|Método derivado pode ser|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

A tabela a seguir mostra os padrões de herança do método proibido.

|Método base|Método derivado não pode ser|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> Essas regras de herança se aplicam aos tipos e membros do nível 2. Os tipos em conjuntos de nível 1 podem herdar de tipos e membros críticos de segurança nível 2. Portanto, os tipos de nível 2 e os membros devem ter demandas de herança separadas para os herdeiros do nível 1.

## <a name="additional-information-and-rules"></a>Informações Adicionais e Regras

### <a name="linkdemand-support"></a>Suporte LinkDemand

O modelo de transparência <xref:System.Security.Permissions.SecurityAction.LinkDemand> nível <xref:System.Security.SecurityCriticalAttribute> 2 substitui o atributo. No código legado (nível <xref:System.Security.Permissions.SecurityAction.LinkDemand> 1), a é <xref:System.Security.Permissions.SecurityAction.Demand>automaticamente tratada como a .

### <a name="reflection"></a>Reflexão

Invocar um método crítico ou ler um campo crítico desencadeia uma demanda por confiança total (como se você estivesse invocando um método ou campo privado). Portanto, o código de confiança total pode invocar um método crítico, enquanto o código de confiança parcial não pode.

As seguintes propriedades foram <xref:System.Reflection> adicionadas ao namespace para determinar `SecurityCritical`se `SecuritySafeCritical`o `SecurityTransparent` <xref:System.Type.IsSecurityCritical%2A>tipo, método ou campo é, ou : , <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>e <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Use essas propriedades para determinar a transparência usando a reflexão em vez de verificar a presença do atributo. As regras de transparência são complexas, e a verificação do atributo pode não ser suficiente.

> [!NOTE]
> Um `SafeCritical` método `true` retorna <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>para `SafeCritical` ambos e, porque é realmente crítico (ele tem as mesmas capacidades que o código crítico, mas pode ser chamado de código transparente).

Os métodos dinâmicos herdam a transparência dos módulos a que estão conectados; eles não herdam a transparência do tipo (se estiverem ligados a um tipo).

### <a name="skip-verification-in-full-trust"></a>Ignorar Verificação em Confiança Total

Você pode pular a verificação para <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> conjuntos `true` transparentes totalmente confiáveis definindo a propriedade no atributo: <xref:System.Security.SecurityRulesAttribute>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

A <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> propriedade `false` é por padrão, então a `true` propriedade deve ser definida para pular a verificação. Isso deve ser feito apenas para fins de otimização. Você deve garantir que o código transparente no conjunto `transparent` seja verificável usando a opção na [ferramenta PEVerify](../tools/peverify-exe-peverify-tool.md).

## <a name="see-also"></a>Confira também

- [Código transparente de segurança, nível 1](security-transparent-code-level-1.md)
- [Alterações de segurança](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
