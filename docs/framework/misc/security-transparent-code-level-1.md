---
title: Segurança-código Transparent, nível 1
ms.date: 03/30/2017
helpviewer_keywords:
- transparent
- SecurityTreatAsSafeAttribute
- SecurityTransparentAttribute
- SecurityCriticalAttribute
- security-transparent code
- security [.NET Framework], security-transparent code
ms.assetid: 5fd8f46d-3961-46a7-84af-2eb1f48e75cf
ms.openlocfilehash: 8f232a7724ad831818627cbfc2845ea808a3fcfd
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215799"
---
# <a name="security-transparent-code-level-1"></a>Segurança-código Transparent, nível 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 A transparência ajuda os desenvolvedores a escreverem bibliotecas de .NET Framework mais seguras que expõem a funcionalidade a código parcialmente confiável. A transparência de nível 1 foi introduzida na versão .NET Framework 2,0 e foi usada principalmente apenas dentro da Microsoft. Começando com o .NET Framework 4, você pode usar a [transparência de nível 2](security-transparent-code-level-2.md). No entanto, a transparência de nível 1 foi mantida para que você possa identificar o código herdado que deve ser executado com as regras de segurança anteriores.  
  
> [!IMPORTANT]
> Você deve especificar a transparência de nível 1 somente para fins de compatibilidade; ou seja, especifique o nível 1 somente para o código que foi desenvolvido com o .NET Framework 3,5 ou anterior que usa o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ou não usa o modelo de transparência. Por exemplo, use a transparência de nível 1 para assemblies .NET Framework 2,0 que permitem chamadas de chamadores parcialmente confiáveis (APTCA). Para o código que é desenvolvido para o .NET Framework 4, sempre use a transparência nível 2.  
  
 Este tópico contém as seguintes seções:  
  
- [O modelo de transparência nível 1](#the_level_1_transparency_model)  
  
- [Atributos de transparência](#transparency_attributes)  
  
- [Exemplos de transparência de segurança](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>O modelo de transparência nível 1  
 Ao usar a transparência de nível 1, você está usando um modelo de segurança que separa o código em métodos de segurança transparente, de segurança crítica e de segurança crítica.  
  
 Você pode marcar um assembly inteiro, algumas classes em um assembly ou alguns métodos em uma classe como segurança transparente. O código de segurança transparente não pode elevar privilégios. Essa restrição tem três consequências:  
  
- O código de segurança transparente não pode executar <xref:System.Security.Permissions.SecurityAction.Assert> ações.  
  
- Qualquer demanda de link que seria satisfeita pelo código de segurança transparente se torna uma demanda completa.  
  
- Qualquer código não seguro (não verificável) que deve ser executado em código de segurança transparente causa uma demanda total para a permissão de segurança de <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>.  
  
 Essas regras são impostas durante a execução pelo Common Language Runtime (CLR). O código de segurança transparente passa todos os requisitos de segurança do código que ele chama de volta para seus chamadores. As demandas que fluem pelo código de segurança transparente não podem elevar privilégios. Se um aplicativo de baixa confiança chamar o código de segurança transparente e causar uma demanda por alto privilégio, a demanda fluirá de volta para o código de baixa confiança e falhará. O código de segurança transparente não pode interromper a demanda porque não pode executar ações Assert. O mesmo código transparente de segurança chamado do código de confiança total resulta em uma demanda bem-sucedida.  
  
 A segurança-crítica é o oposto da segurança transparente. O código de segurança crítica é executado com confiança total e pode executar todas as operações privilegiadas. Segurança-o código crítico é o código privilegiado que passou por uma ampla auditoria de segurança para confirmar que ele não permite que chamadores parcialmente confiáveis usem recursos que eles não têm permissão para acessar.  
  
 Você precisa aplicar transparência explicitamente. A maior parte do seu código que lida com a manipulação e a lógica de dados normalmente pode ser marcada como de segurança transparente, enquanto que a menor quantidade de código que executa elevações de privilégios é marcada como segurança crítica ou segura para segurança.  
  
> [!IMPORTANT]
> A transparência de nível 1 é limitada ao escopo do assembly; Ele não é imposto entre assemblies. A transparência de nível 1 foi usada principalmente na Microsoft para fins de auditoria de segurança. Os tipos de segurança crítica e os membros em um assembly de nível 1 podem ser acessados pelo código de segurança transparente em outros assemblies. É importante que você execute demandas de link para confiança total em todos os seus tipos e membros de segurança de nível 1. Os membros e os tipos de segurança segura-críticos também devem confirmar se os chamadores têm permissões para recursos protegidos que são acessados pelo tipo ou membro.  
  
 Para compatibilidade com versões anteriores do .NET Framework, todos os membros que não estão anotados com atributos de transparência são considerados críticos para segurança. Todos os tipos que não são anotados são considerados transparentes. Não há regras de análise estática para validar a transparência. Portanto, talvez seja necessário depurar erros de transparência em tempo de execução.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Atributos de transparência  
 A tabela a seguir descreve os três atributos que você usa para anotar seu código em busca de transparência.  
  
|Atributo|DESCRIÇÃO|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Permitido somente no nível do assembly. Identifica todos os tipos e membros no assembly como segurança transparente. O assembly não pode conter nenhum código crítico de segurança.|  
|<xref:System.Security.SecurityCriticalAttribute>|Quando usado no nível de assembly sem a propriedade <xref:System.Security.SecurityCriticalAttribute.Scope%2A>, identifica todo o código no assembly como segurança transparente por padrão, mas indica que o assembly pode conter código de segurança crítica.<br /><br /> Quando usado no nível de classe, identifica a classe ou o método como segurança crítica, mas não os membros da classe. Para tornar todos os membros de segurança crítica, defina a propriedade <xref:System.Security.SecurityCriticalAttribute.Scope%2A> como <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> Quando usado no nível de membro, o atributo aplica-se somente a esse membro.<br /><br /> A classe ou o membro identificado como segurança crítica pode executar elevações de privilégio. **Importante:**  Na transparência de nível 1, os tipos de segurança crítica e os membros são tratados como de segurança crítica quando são chamados de fora do assembly. Você deve proteger tipos e membros com segurança crítica com uma demanda de link para confiança total para evitar elevação de privilégio não autorizada.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identifica o código de segurança crítica que pode ser acessado pelo código de segurança transparente no assembly. Caso contrário, o código de segurança transparente não poderá acessar membros críticos de segurança privada ou interna no mesmo assembly. Isso influenciaria o código de segurança crítica e tornaria as elevações inesperadas de privilégio possível. Segurança-o código crítico deve passar por uma auditoria de segurança rigorosa. **Observação:**  Os membros e tipos com segurança crítica devem validar as permissões de chamadores para determinar se o chamador tem autoridade para acessar recursos protegidos.|  
  
 O atributo <xref:System.Security.SecuritySafeCriticalAttribute> permite que o código de segurança transparente acesse os membros de segurança crítica no mesmo assembly. Considere o código de segurança transparente e com segurança crítica em seu assembly, como separado em dois assemblies. O código de segurança transparente não seria capaz de ver os membros privados ou internos do código de segurança crítica. Além disso, o código de segurança crítica geralmente é auditado para acesso à sua interface pública. Você não esperaria que um estado privado ou interno fosse acessível fora do assembly; Você desejaria manter o estado isolado. O atributo <xref:System.Security.SecuritySafeCriticalAttribute> mantém o isolamento do estado entre o código de segurança transparente e de segurança crítica, fornecendo a capacidade de substituir o isolamento quando necessário. O código de segurança transparente não pode acessar código crítico de segurança particular ou interno, a menos que esses membros tenham sido marcados com <xref:System.Security.SecuritySafeCriticalAttribute>. Antes de aplicar o <xref:System.Security.SecuritySafeCriticalAttribute>, faça auditoria desse membro como se ele estivesse publicamente exposto.  
  
### <a name="assembly-wide-annotation"></a>Anotação em todo o assembly  
 A tabela a seguir descreve os efeitos do uso de atributos de segurança no nível do assembly.  
  
|Atributo de assembly|Estado do assembly|  
|------------------------|--------------------|  
|Nenhum atributo em um assembly parcialmente confiável|Todos os tipos e membros são transparentes.|  
|Nenhum atributo em um assembly totalmente confiável (no cache de assembly global ou identificado como confiança total no `AppDomain`)|Todos os tipos são transparentes e todos os membros são críticos à segurança.|  
|`SecurityTransparent`|Todos os tipos e membros são transparentes.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Todos os tipos e membros são críticos para a segurança.|  
|`SecurityCritical`|Todos os padrões de código são transparentes. No entanto, tipos individuais e membros podem ter outros atributos.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Exemplos de transparência de segurança  
 Para usar as regras de transparência do .NET Framework 2,0 (transparência de nível 1), use a seguinte anotação de assembly:  
  
```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Se você quiser tornar um assembly inteiro transparente para indicar que o assembly não contém nenhum código crítico e não eleva privilégios de forma alguma, você pode adicionar a transparência explicitamente ao assembly com o seguinte atributo:  
  
```csharp  
[assembly: SecurityTransparent]  
```  
  
 Se você quiser misturar código crítico e transparente no mesmo assembly, comece marcando o assembly com o atributo <xref:System.Security.SecurityCriticalAttribute> para indicar que o assembly pode conter código crítico, da seguinte maneira:  
  
```csharp  
[assembly: SecurityCritical]  
```  
  
 Se você quiser executar ações de segurança crítica, deverá marcar explicitamente o código que executará a ação crítica com outro atributo <xref:System.Security.SecurityCriticalAttribute>, conforme mostrado no exemplo de código a seguir:  
  
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
  
 O código anterior é transparente, exceto pelo método `Critical`, que é explicitamente marcado como Security-Critical. Transparência é a configuração padrão, mesmo com o atributo de <xref:System.Security.SecurityCriticalAttribute> no nível do assembly.  
  
## <a name="see-also"></a>Confira também

- [Segurança-código Transparent, nível 2](security-transparent-code-level-2.md)
- [Alterações de segurança](../security/security-changes.md)
