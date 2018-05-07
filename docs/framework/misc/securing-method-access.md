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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b0d9ddbd6c7b027a7c342f4c14192a7571beb592
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="securing-method-access"></a>Protegendo o acesso dos métodos
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Alguns métodos podem não ser adequados para permitir a chamar código não confiável arbitrário. Esses métodos apresentam vários riscos: O método pode fornecer algumas informações restritas; ele pode achar qualquer informação passada para ele; ele não pode fazer a verificação de erro em parâmetros. ou com parâmetros incorretos, talvez ele mau funcionamento ou fazer algo prejudiciais. Você deve estar ciente desses casos e tomar medidas para ajudar a proteger o método.  
  
 Em alguns casos, convém restringir os métodos que não se destina para uso público, mas ainda devem ser públicos. Por exemplo, você pode ter uma interface que precisa ser chamado em seus próprio DLLs e, portanto, deve ser públicos, mas você não deseja expor publicamente para impedir que os clientes usá-lo ou para impedir que um código mal-intencionado Explorando o ponto de entrada em seu componente. Outro motivo comum para restringir um método não se destina para uso público (mas que devem ser públicos) é evitar ter de documento e suporte que pode haver uma interface muito interna.  
  
 Gerenciado código oferece várias maneiras para restringir o acesso do método:  
  
-   Limite o escopo de acessibilidade para a classe, assembly ou classes derivadas, se eles podem ser confiáveis. Essa é a maneira mais simples para limitar o acesso do método. Observe que, em geral, as classes derivadas podem ser menos confiáveis do que a classe que derivam, embora em alguns casos, eles compartilham identidade da classe pai. Em particular, não deduzir a relação de confiança da palavra-chave **protegido**, que não é necessariamente usado no contexto de segurança.  
  
-   Limitar o acesso de método para chamadores de uma identidade especificada – essencialmente, qualquer [evidência](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (nome forte, publisher, zona e assim por diante) que você escolher.  
  
-   Limite o acesso de método para chamadores com as permissões que você selecionar.  
  
 Da mesma forma, a segurança declarativa permite controlar a herança de classes. Você pode usar **InheritanceDemand** para fazer o seguinte:  
  
-   Exigir classes derivadas para ter uma identidade especificada ou a permissão.  
  
-   Exigir classes derivadas que substituem os métodos específicos para ter uma identidade especificada ou a permissão.  
  
 O exemplo a seguir mostra como proteger uma classe pública para acesso limitado, exigindo que os chamadores sejam assinados com um determinado nome forte. Este exemplo usa o <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> com um **demanda** para o nome forte. Para baseado em tarefa obter informações sobre como assinar um assembly com um nome forte, consulte [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
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
 Use as declarações mostradas nesta seção para impedir que classes específicas e métodos, bem como propriedades e eventos, que está sendo usado por código parcialmente confiável. Aplicando essas declarações para uma classe, você deve aplicar a proteção para todos os seus métodos, propriedades e eventos; No entanto, observe que o acesso de campo não é afetado por segurança declarativa. Observe também que as demandas de link ajudam a proteger contra somente os chamadores imediatos e ainda podem estar sujeita a ataques de atração.  
  
> [!NOTE]
>  Um novo modelo de transparência foi introduzido no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. O [código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modelo identifica o código de segurança com o <xref:System.Security.SecurityCriticalAttribute> atributo. Código crítico de segurança requer que os chamadores e herdeiros ser totalmente confiável. Os assemblies que estão sendo executados sob as regras de segurança de acesso do código de versões anteriores do .NET Framework podem chamar assemblies de nível 2. Nesse caso, os atributos de segurança crítica serão tratados como demandas de link de confiança total.  
  
 Em assemblies de nome forte, um [LinkDemand](../../../docs/framework/misc/link-demands.md) é aplicado a todos os eventos para restringir o uso para os chamadores totalmente confiáveis, propriedades e métodos publicamente acessíveis. Para desabilitar esse recurso, você deve aplicar o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo. Assim, é necessário somente para assemblies não assinados ou assemblies com esse atributo; marcar explicitamente classes para excluir os chamadores não confiáveis Você pode usar essas declarações para marcar um subconjunto de tipos contidos que não são destinadas para chamadores não confiáveis.  
  
 Os exemplos a seguir mostram como evitar classes e membros que está sendo usado por código não confiável.  
  
 Para as classes públicas nonsealed:  
  
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
  
 Para public lacrado classes:  
  
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
  
 Para classes abstratas públicas:  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe{}  
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
  
 Para funções abstract públicas:  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 Para funções de substituição pública em que a classe base não exigem confiança total:  
  
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
  
 Para funções de substituição pública em que a classe base exige confiança total:  
  
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
>  Esta seção avisa sobre um problema de segurança ao declarar um método como `virtual` e `internal` (`Overloads``Overridable``Friend` no Visual Basic). Este aviso se aplica somente às versões do .NET Framework 1.0 e 1.1, não se aplica a versões posteriores.  
  
 Nas versões do .NET Framework 1.0 e 1.1, você deve estar atento um nuance de acessibilidade do sistema de tipo durante a confirmação de que seu código não está disponível para outros assemblies. Um método que é declarado **virtual** e **interno** (**sobrecargas substituível Friend** no Visual Basic) pode substituir a entrada de vtable da classe pai e pode ser usado somente em dentro do mesmo assembly porque é interno. No entanto, a acessibilidade de substituição é determinada pelo **virtual** palavra-chave e isso pode ser substituído de outro assembly, desde que o código tenha acesso à própria classe. Se a possibilidade de uma substituição apresenta um problema, use a segurança declarativa para corrigi-lo, ou remova o **virtual** palavra-chave se ela não é estritamente necessária.  
  
 Observe que, mesmo que um compilador de linguagem impede que essas substituições com um erro de compilação, é possível que código gravado com outros compiladores para substituir.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
