---
title: Código transparente de segurança, nível 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
ms.openlocfilehash: 980c684bced685a61ad82ff5713ccff2b974028f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181122"
---
# <a name="security-transparent-code-level-1"></a>Código transparente de segurança, nível 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 A transparência ajuda os desenvolvedores a escrever bibliotecas .NET Framework mais seguras que expõem a funcionalidade a códigos parcialmente confiáveis. A transparência nível 1 foi introduzida na versão 2.0 do .NET Framework e foi usada principalmente apenas dentro da Microsoft. Começando com o Quadro .NET 4, você pode usar [a transparência nível 2](security-transparent-code-level-2.md). No entanto, a transparência nível 1 foi mantida para que você possa identificar código legado que deve ser executado com as regras de segurança anteriores.  
  
> [!IMPORTANT]
> Você deve especificar a transparência nível 1 apenas para compatibilidade; ou seja, especifique o nível 1 apenas para o código que <xref:System.Security.AllowPartiallyTrustedCallersAttribute> foi desenvolvido com o .NET Framework 3.5 ou anterior que usa o modelo de transparência ou não use o modelo de transparência. Por exemplo, use a transparência nível 1 para conjuntos .NET Framework 2.0 que permitem chamadas de chamadores parcialmente confiáveis (APTCA). Para o código desenvolvido para o .NET Framework 4, use sempre a transparência nível 2.  
  
 Este tópico contém as seguintes seções:  
  
- [O modelo de transparência nível 1](#the_level_1_transparency_model)  
  
- [Atributos de transparência](#transparency_attributes)  
  
- [Exemplos de transparência de segurança](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>
## <a name="the-level-1-transparency-model"></a>O modelo de transparência nível 1  
 Quando você usa a transparência nível 1, você está usando um modelo de segurança que separa o código em métodos transparentes de segurança, críticos à segurança e críticos à segurança.  
  
 Você pode marcar uma assembléia inteira, algumas classes em uma assembléia, ou alguns métodos em uma classe como transparentes de segurança. O código transparente de segurança não pode elevar privilégios. Esta restrição tem três consequências:  
  
- O código transparente <xref:System.Security.Permissions.SecurityAction.Assert> de segurança não pode executar ações.  
  
- Qualquer demanda de link que seja satisfeita pelo código transparente de segurança torna-se uma demanda completa.  
  
- Qualquer código inseguro (inverificável) que deve ser executado em <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> código transparente de segurança causa uma demanda total pela permissão de segurança.  
  
 Essas regras são aplicadas durante a execução pelo tempo de execução da linguagem comum (CLR). O código transparente de segurança passa todos os requisitos de segurança do código que ele chama de volta para seus chamadores. Demandas que fluem através do código transparente de segurança não podem elevar privilégios. Se um aplicativo de baixa confiança chamar código transparente de segurança e causar uma demanda por alto privilégio, a demanda voltará para o código de baixa confiança e falhará. O código transparente de segurança não pode parar a demanda porque não pode executar ações de afirmação. O mesmo código transparente de segurança chamado do código de confiança total resulta em uma demanda bem sucedida.  
  
 A segurança crítica é o oposto de transparente de segurança. O código crítico de segurança é executado com total confiança e pode executar todas as operações privilegiadas. Código crítico de segurança é um código privilegiado que passou por uma extensa auditoria de segurança para confirmar que não permite que os chamadores parcialmente confiáveis usem recursos que não têm permissão para acessar.  
  
 Você tem que aplicar transparência explicitamente. A maioria do seu código que lida com manipulação de dados e lógica pode normalmente ser marcada como transparente para a segurança, enquanto a menor quantidade de código que executa elevações de privilégios é marcada como crítica de segurança ou crítica de segurança.  
  
> [!IMPORTANT]
> A transparência nível 1 está limitada ao escopo de montagem; não é imposta entre assembléias. A transparência nível 1 foi usada principalmente dentro da Microsoft para fins de auditoria de segurança. Os tipos críticos de segurança e os membros dentro de um conjunto de nível 1 podem ser acessados por código transparente de segurança em outras assembléias. É importante que você execute demandas de link para total confiança em todos os seus tipos e membros críticos de segurança nível 1. Os tipos e membros críticos de segurança também devem confirmar que os chamadores têm permissões para recursos protegidos que são acessados pelo tipo ou membro.  
  
 Para compatibilidade retrógrada com versões anteriores do .NET Framework, todos os membros que não são anotados com atributos de transparência são considerados críticos à segurança. Todos os tipos que não são anotados são considerados transparentes. Não há regras de análise estática para validar a transparência. Portanto, você pode precisar depurar erros de transparência no tempo de execução.  
  
<a name="transparency_attributes"></a>
## <a name="transparency-attributes"></a>Atributos de transparência  
 A tabela a seguir descreve os três atributos que você usa para anotar seu código para transparência.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Permitido apenas no nível de montagem. Identifica todos os tipos e membros na montagem como transparentes à segurança. A montagem não pode conter nenhum código crítico de segurança.|  
|<xref:System.Security.SecurityCriticalAttribute>|Quando usado no nível <xref:System.Security.SecurityCriticalAttribute.Scope%2A> de montagem sem a propriedade, identifica todo o código no conjunto como transparente de segurança por padrão, mas indica que o conjunto pode conter código crítico de segurança.<br /><br /> Quando usado no nível de classe, identifica a classe ou o método como críticos de segurança, mas não os membros da classe. Para tornar todos os membros críticos à segurança, defina a <xref:System.Security.SecurityCriticalAttribute.Scope%2A> propriedade para <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> Quando usado no nível de membro, o atributo se aplica apenas a esse membro.<br /><br /> A classe ou membro identificado como crítico de segurança pode realizar elevações de privilégios. **Importante:**  Na transparência nível 1, os tipos críticos de segurança e os membros são tratados como críticos de segurança quando são chamados de fora da assembléia. Você deve proteger os tipos críticos de segurança e os membros com uma demanda de link de confiança total para evitar a elevação não autorizada do privilégio.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identifica código crítico de segurança que pode ser acessado por código transparente de segurança no conjunto. Caso contrário, o código transparente de segurança não pode acessar membros privados ou internos críticos à segurança na mesma assembléia. Isso influenciaria o código crítico de segurança e tornaria possível elevações inesperadas de privilégios. O código crítico de segurança deve passar por uma rigorosa auditoria de segurança. **Nota:**  Os tipos e membros críticos de segurança devem validar as permissões dos chamadores para determinar se o chamador tem autoridade para acessar recursos protegidos.|  
  
 O <xref:System.Security.SecuritySafeCriticalAttribute> atributo permite que o código transparente de segurança acesse membros críticos de segurança no mesmo conjunto. Considere o código transparente de segurança e crítico de segurança em sua montagem como separado em dois conjuntos. O código transparente de segurança não seria capaz de ver os membros privados ou internos do código crítico de segurança. Além disso, o código crítico de segurança é geralmente auditado para acesso à sua interface pública. Você não esperaria que um estado privado ou interno fosse acessível fora da assembléia; você gostaria de manter o estado isolado. O <xref:System.Security.SecuritySafeCriticalAttribute> atributo mantém o isolamento do estado entre o código transparente de segurança e o código crítico de segurança, ao mesmo tempo em que fornece a capacidade de anular o isolamento quando necessário. O código transparente de segurança não pode acessar códigos críticos de segurança privadas ou internas, a menos que esses membros tenham sido marcados com <xref:System.Security.SecuritySafeCriticalAttribute>. Antes de <xref:System.Security.SecuritySafeCriticalAttribute>aplicar a auditoria, esse membro como se estivesse exposto publicamente.  
  
### <a name="assembly-wide-annotation"></a>Anotação em toda a montagem  
 A tabela a seguir descreve os efeitos do uso de atributos de segurança no nível de montagem.  
  
|Atributo de assembly|Estado da Assembléia|  
|------------------------|--------------------|  
|Nenhum atributo em uma assembléia parcialmente confiável|Todos os tipos e membros são transparentes.|  
|Nenhum atributo em uma montagem totalmente confiável (no cache `AppDomain`de montagem global ou identificado como total confiança no )|Todos os tipos são transparentes e todos os membros são críticos à segurança.|  
|`SecurityTransparent`|Todos os tipos e membros são transparentes.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Todos os tipos e membros são críticos à segurança.|  
|`SecurityCritical`|Todos os códigos são padrão transparentes. No entanto, tipos individuais e membros podem ter outros atributos.|  
  
<a name="security_transparency_examples"></a>
## <a name="security-transparency-examples"></a>Exemplos de transparência de segurança  
 Para usar as regras de transparência do Quadro .NET 2.0 (transparência nível 1), use a seguinte anotação de montagem:  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Se você quiser tornar um conjunto inteiro transparente para indicar que a montagem não contém nenhum código crítico e não eleva privilégios de forma alguma, você pode explicitamente adicionar transparência à montagem com o seguinte atributo:  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 Se você quiser misturar código crítico e transparente no mesmo conjunto, comece marcando o conjunto com o atributo <xref:System.Security.SecurityCriticalAttribute> para indicar que o conjunto pode conter código crítico, da seguinte forma:  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 Se você quiser executar ações críticas à segurança, você deve marcar explicitamente <xref:System.Security.SecurityCriticalAttribute> o código que executará a ação crítica com outro atributo, como mostrado no exemplo de código a seguir:  
  
```csharp  
[assembly: SecurityCritical]  
public class A  
{  
    [SecurityCritical]  
    private void Critical()  
    {  
        // critical  
    }  
  
    public int SomeProperty  
    {  
        get {/* transparent */ }  
        set {/* transparent */ }  
    }  
}  
public class B  
{
    internal string SomeOtherProperty  
    {  
        get { /* transparent */ }  
        set { /* transparent */ }  
    }  
}  
```  
  
 O código anterior é `Critical` transparente, exceto para o método, que é explicitamente marcado como crítico de segurança. Transparência é a configuração padrão, <xref:System.Security.SecurityCriticalAttribute> mesmo com o atributo de nível de montagem.  
  
## <a name="see-also"></a>Confira também

- [Código transparente de segurança, nível 2](security-transparent-code-level-2.md)
- [Alterações de segurança](../security/security-changes.md)
