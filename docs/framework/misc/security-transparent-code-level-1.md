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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afec37a6510e445f1fe2c430684099af967be0ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868752"
---
# <a name="security-transparent-code-level-1"></a>Código transparente de segurança, nível 1
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Transparência ajuda os desenvolvedores a escrever bibliotecas do .NET Framework mais seguras que expõem a funcionalidade para código parcialmente confiável. Transparência de nível 1 foi introduzida no .NET Framework versão 2.0 e foi usada originalmente somente dentro da Microsoft. Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar [transparência de nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md). No entanto, transparência de nível 1 foi retida para que você possa identificar código herdado que deve ser executado com as regras de segurança anteriores.  
  
> [!IMPORTANT]
>  Você deve especificar a transparência de nível 1 somente para compatibilidade; ou seja, especificar o nível 1 somente para o código que foi desenvolvido com o .NET Framework 3.5 ou anterior que usa o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ou não usar o modelo de transparência. Por exemplo, use a transparência de nível 1 para assemblies do .NET Framework 2.0 que permitem chamadas de chamadores parcialmente confiáveis (APTCA). Para o código que é desenvolvido para o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], sempre use a transparência de nível 2.  
  
 Esse tópico contém as seguintes seções:  
  
- [O modelo de transparência de nível 1](#the_level_1_transparency_model)  
  
- [Atributos de transparência](#transparency_attributes)  
  
- [Exemplos de transparência de segurança](#security_transparency_examples)  
  
<a name="the_level_1_transparency_model"></a>   
## <a name="the-level-1-transparency-model"></a>O modelo de transparência de nível 1  
 Quando você usa a transparência de nível 1, você estiver usando um modelo de segurança que separa o código em métodos transparentes de segurança, segurança-seguro-crítica e crítico para segurança.  
  
 Você pode marcar um assembly inteiro, algumas classes em um assembly ou alguns métodos em uma classe como transparente de segurança. Código transparente de segurança não pode elevar os privilégios. Essa restrição tem três consequências:  
  
- Código transparente de segurança não é possível executar <xref:System.Security.Permissions.SecurityAction.Assert> ações.  
  
- Qualquer demanda de link que seria atendida pelo código transparente de segurança se torna uma demanda completa.  
  
- Qualquer código não seguro (não verificável) que deve ser executado no código transparente de segurança faz com que uma demanda completa para o <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> permissão de segurança.  
  
 Essas regras são impostas durante a execução pelo common language runtime (CLR). Código transparente de segurança passa todos os requisitos de segurança do código que ele chama de volta para os chamadores. As demandas que fluem através do código transparente de segurança não podem elevar os privilégios. Se um aplicativo de confiança baixa chama o código transparente de segurança e faz com que uma demanda de alto privilégio, a demanda de fluxo de volta para o código de baixa confiança e falhar. O código transparente de segurança não é possível parar a demanda porque ele não pode realizar ações de assert. O mesmo código transparente de segurança chamado de código de confiança total resulta em uma demanda com êxito.  
  
 Segurança crítica é o oposto da transparência de segurança. Código de segurança crítica é executado com confiança total e pode executar todas as operações privilegiadas. Código de segurança-seguro-crítica é privilegiada que tenha sido por meio de uma auditoria de segurança extensiva para confirmar que ele não permite chamadores parcialmente confiáveis usar os recursos que eles não têm permissão para acessar.  
  
 Você precisa aplicar transparência explicitamente. A maioria do código que manipula a lógica e manipulação de dados normalmente pode ser marcada como transparente de segurança, ao passo que a menor quantidade de código que executa as elevações de privilégios está marcada como crítico para segurança ou segurança-seguro-crítica.  
  
> [!IMPORTANT]
>  Transparência de nível 1 é limitada ao escopo do assembly. ele não é imposto entre assemblies. Transparência de nível 1 foi usada principalmente dentro da Microsoft para fins de auditoria de segurança. Tipos de segurança crítica e os membros dentro de um assembly de nível 1 podem ser acessados pelo código transparente de segurança em outros assemblies. É importante que você execute demandas de link para confiança total em todos os seus membros e tipos de segurança crítica de nível 1. Os membros e tipos de segurança-seguro-crítica também devem confirmar que os chamadores tenham permissões para recursos protegidos que são acessados por tipo ou membro.  
  
 Para fins de compatibilidade com versões anteriores do .NET Framework, todos os membros que não são anotados com atributos de transparência são considerados segurança-seguro-crítica. Todos os tipos que são anotados não são considerados para ser transparente. Não há nenhuma regra de análise estática para validar a transparência. Portanto, você talvez precise depurar erros de transparência em tempo de execução.  
  
<a name="transparency_attributes"></a>   
## <a name="transparency-attributes"></a>Atributos de transparência  
 A tabela a seguir descreve os três atributos que você pode usar para anotar o código para transparência.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute>|Permitido apenas no nível do assembly. Identifica todos os tipos e membros no assembly como transparente de segurança. O assembly não pode conter qualquer código de segurança crítica.|  
|<xref:System.Security.SecurityCriticalAttribute>|Quando usado no nível do assembly sem o <xref:System.Security.SecurityCriticalAttribute.Scope%2A> propriedade, identifica todo o código no assembly como transparente de segurança por padrão, mas indica que o assembly pode conter código crítico para segurança.<br /><br /> Quando usado no nível de classe, identifica a classe ou método, como críticas de segurança, mas não os membros da classe. Para fazer com que todos os membros críticos para segurança, defina as <xref:System.Security.SecurityCriticalAttribute.Scope%2A> propriedade para <xref:System.Security.SecurityCriticalScope.Everything>.<br /><br /> Quando usado no nível do membro, o atributo se aplica somente a esse membro.<br /><br /> A classe ou membro identificado como crítico de segurança pode executar elevações de privilégio. **Importante:**  Na transparência de nível 1, tipos e membros críticos de segurança são tratados como segurança-seguro-crítica quando eles são chamados de fora do assembly. Você deve proteger a segurança crítica tipos e membros com uma demanda de link para confiança total para evitar a elevação não autorizada de privilégios.|  
|<xref:System.Security.SecuritySafeCriticalAttribute>|Identifica o código de segurança crítica que pode ser acessado pelo código transparente de segurança no assembly. Caso contrário, o código transparente de segurança não pode acessar membros críticos para segurança privados ou internos no mesmo assembly. Isso seria influenciar o código de segurança crítica e possibilitam inesperadas elevações de privilégio. Código de segurança-seguro-crítica deve passar por uma auditoria de segurança rigorosos. **Observação:**  Os membros e tipos de segurança-seguro-crítica devem validar as permissões dos chamadores para determinar se o chamador tem autoridade para acessar recursos protegidos.|  
  
 O <xref:System.Security.SecuritySafeCriticalAttribute> atributo permite que o código transparente de segurança acessar membros críticos para segurança no mesmo assembly. Considere o código transparente de segurança e críticas de segurança em seu assembly conforme separados em dois assemblies. O código transparente de segurança não poderá ver os membros privados ou internos do código crítico para segurança. Além disso, o código crítico para segurança em geral é auditado para acesso à sua interface pública. Você não esperaria em um estado privado ou interno para estar acessível fora do assembly; Você pode querer manter o estado isolado. O <xref:System.Security.SecuritySafeCriticalAttribute> atributo mantém o isolamento de estado entre o código transparente de segurança e críticas de segurança, fornecendo a capacidade de substituir o isolamento quando for necessário. Código transparente de segurança não pode acessar o código de segurança crítica privado ou interno, a menos que esses membros foram marcados com <xref:System.Security.SecuritySafeCriticalAttribute>. Antes de aplicar o <xref:System.Security.SecuritySafeCriticalAttribute>, esse membro de auditoria, como se ele foi exposto publicamente.  
  
### <a name="assembly-wide-annotation"></a>Anotação de todo o assembly  
 A tabela a seguir descreve os efeitos do uso de atributos de segurança no nível do assembly.  
  
|Atributo de assembly|Estado do assembly|  
|------------------------|--------------------|  
|Nenhum atributo em um assembly parcialmente confiável|Todos os tipos e membros são transparentes.|  
|Nenhum atributo em um assembly totalmente confiável (no cache de assembly global ou identificado como confiança total no `AppDomain`)|Todos os tipos são transparentes e todos os membros são segurança-seguro-crítica.|  
|`SecurityTransparent`|Todos os tipos e membros são transparentes.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Todos os tipos e membros são críticos para segurança.|  
|`SecurityCritical`|Todo o código padrão é transparente. No entanto, os membros e tipos individuais podem ter outros atributos.|  
  
<a name="security_transparency_examples"></a>   
## <a name="security-transparency-examples"></a>Exemplos de transparência de segurança  
 Para usar as regras de transparência do .NET Framework 2.0 (transparência de nível 1), use a anotação de assembly a seguir:  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Se você quiser criar um assembly inteiro transparente para indicar que o assembly não contém qualquer código crítico e não eleva os privilégios de qualquer forma, você pode adicionar explicitamente transparência para o assembly com o seguinte atributo:  
  
```  
[assembly: SecurityTransparent]  
```  
  
 Se você desejar misturar código transparente e crítico no mesmo assembly, inicie marcando o assembly com o <xref:System.Security.SecurityCriticalAttribute> atributo para indicar que o assembly pode conter código crítico, da seguinte maneira:  
  
```  
[assembly: SecurityCritical]  
```  
  
 Se você quiser executar ações de segurança crítica, você deve marcar explicitamente o código que executará a ação crítica com outra <xref:System.Security.SecurityCriticalAttribute> de atributo, conforme mostrado no exemplo de código a seguir:  
  
```  
[assembly: SecurityCritical]  
Public class A  
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
  
 O código anterior é transparente, exceto para o `Critical` método, que seja explicitamente marcado como crítico de segurança. A transparência é a configuração padrão, mesmo com o nível de assembly <xref:System.Security.SecurityCriticalAttribute> atributo.  
  
## <a name="see-also"></a>Consulte também

- [Código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
- [Alterações de segurança](../../../docs/framework/security/security-changes.md)
