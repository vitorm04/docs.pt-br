---
title: Protegendo o acesso dos métodos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
ms.openlocfilehash: a9e1226483eaa02dc8dc3dfb741e3df6b2985fbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181153"
---
# <a name="securing-method-access"></a>Protegendo o acesso dos métodos
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Alguns métodos podem não ser adequados para permitir que códigos arbitrários não confiáveis chamem. Tais métodos representam vários riscos: O método pode fornecer algumas informações restritas; ele pode acreditar que qualquer informação passou para ele, mas ele não pode pode não fazer verificação de erros nos parâmetros; ou com os parâmetros errados, pode funcionar mal ou fazer algo prejudicial. Você deve estar ciente desses casos e tomar medidas para ajudar a proteger o método.  
  
 Em alguns casos, você pode precisar restringir métodos que não são destinados ao uso público, mas ainda devem ser públicos. Por exemplo, você pode ter uma interface que precisa ser chamada através de seus próprios DLLs e, portanto, deve ser pública, mas você não quer expô-la publicamente para impedir que os clientes o usem ou para impedir que o código malicioso explore o ponto de entrada em seu componente. Outra razão comum para restringir um método não destinado ao uso público (mas que deve ser público) é evitar ter que documentar e apoiar o que pode ser uma interface muito interna.  
  
 O código gerenciado oferece várias maneiras de restringir o acesso ao método:  
  
- Limite o escopo de acessibilidade às classes de classe, montagem ou derivada, se elas forem confiáveis. Esta é a maneira mais simples de limitar o acesso ao método. Note que, em geral, as classes derivadas podem ser menos confiáveis do que a classe de que derivam, embora em alguns casos compartilhem a identidade da classe pai. Em particular, não inferir confiança da palavra-chave **protegida,** que não é necessariamente usada no contexto de segurança.  
  
- Limite o acesso do método aos chamadores de uma identidade especificada — essencialmente, qualquer [evidência](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) específica (nome forte, editor, zona e assim por diante) você escolhe.  
  
- Limite o acesso do método aos chamadores que tenham as permissões selecionadas.  
  
 Da mesma forma, a segurança declarativa permite controlar a herança das classes. Você pode usar **A HerançaDemanda** para fazer o seguinte:  
  
- Exija que as classes derivadas tenham uma identidade ou permissão especificadas.  
  
- Requerem classes derivadas que sobrepõem métodos específicos para ter uma identidade ou permissão especificadas.  
  
 O exemplo a seguir mostra como ajudar a proteger uma classe pública para acesso limitado, exigindo que os chamadores sejam assinados com um nome específico. Este exemplo <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> usa o com uma **Demanda** para o nome forte. Para obter informações baseadas em tarefas sobre como assinar um conjunto com um nome forte, consulte [Criando e Usando Conjuntos com Nomes Fortes](../../standard/assembly/create-use-strong-named.md).  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a>Excluindo classes e membros do uso por código não confiável  
 Use as declarações mostradas nesta seção para evitar que classes e métodos específicos, bem como propriedades e eventos, sejam usados por código parcialmente confiável. Ao aplicar essas declarações a uma classe, você aplica a proteção a todos os seus métodos, propriedades e eventos; no entanto, observe que o acesso ao campo não é afetado pela segurança declarativa. Observe também que as demandas de links ajudam a proteger apenas contra os chamadores imediatos e ainda podem estar sujeitas a ataques de atração.  
  
> [!NOTE]
> Um novo modelo de transparência foi introduzido no Quadro .NET 4. O modelo [Security-Transparent Code, Nível 2,](security-transparent-code-level-2.md) identifica código seguro com o atributo. <xref:System.Security.SecurityCriticalAttribute> O código crítico de segurança exige que tanto os chamadores quanto os herdeiros sejam totalmente confiáveis. Os conjuntos que estão sendo executados sob as regras de segurança de acesso ao código de versões anteriores do .NET Framework podem chamar conjuntos de nível 2. Neste caso, os atributos críticos à segurança serão tratados como demandas de link para a confiança total.  
  
 Em conjuntos com nomes fortes, um [LinkDemand](link-demands.md) é aplicado a todos os métodos, propriedades e eventos acessíveis publicamente para restringir seu uso a chamadores totalmente confiáveis. Para desativar esse recurso, você <xref:System.Security.AllowPartiallyTrustedCallersAttribute> deve aplicar o atributo. Assim, marcar explicitamente classes para excluir chamadores não confiáveis é necessário apenas para assembléias ou assembléias não assinadas com este atributo; você pode usar essas declarações para marcar um subconjunto de tipos nelas que não são destinados a chamadores não confiáveis.  
  
 Os exemplos a seguir mostram como evitar que classes e membros sejam usados por código não confiável.  
  
 Para classes públicas não seladas:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 Para aulas públicas lacradas:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 Para aulas abstratas públicas:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe {}  
```  
  
 Para funções virtuais públicas:  
  
```vb  
Class Base1
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 Para funções abstratas públicas:  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2 {  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 Para funções de substituição pública onde a classe base não exige confiança total:  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 Para funções de substituição pública onde a classe base exige total confiança:  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 Para interfaces públicas:  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a>Substituições com virtual internal ou Overloads Overridable Friend  
  
> [!NOTE]
> Esta seção adverte sobre um problema de `virtual` segurança `internal` `Overloads` `Overridable` ao declarar um método como ambos e (no `Friend` Visual Basic). Este aviso se aplica apenas às versões .NET Framework 1.0 e 1.1, não se aplica às versões posteriores.  
  
 Nas versões .NET Framework 1.0 e 1.1, você deve estar ciente de uma nuance da acessibilidade do sistema do tipo ao confirmar que seu código não está disponível para outros conjuntos. Um método declarado **virtual** e **interno** **(Overloads Overridable Friend** in Visual Basic) pode substituir a entrada vtable da classe pai e só pode ser usado dentro do mesmo conjunto porque é interno. No entanto, a acessibilidade para substituição é determinada pela palavra-chave **virtual,** e isso pode ser substituído de outra montagem, desde que esse código tenha acesso à própria classe. Se a possibilidade de uma substituição apresentar um problema, use segurança declarativa para corrigi-lo ou remova a palavra-chave **virtual** se não for estritamente necessária.  
  
 Observe que, mesmo que um compilador de idiomas impeça essas substituições com um erro de compilação, é possível que o código escrito com outros compiladores seja substituído.  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
