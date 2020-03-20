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
# <a name="securing-method-access"></a><span data-ttu-id="43c13-102">Protegendo o acesso dos métodos</span><span class="sxs-lookup"><span data-stu-id="43c13-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="43c13-103">Alguns métodos podem não ser adequados para permitir que códigos arbitrários não confiáveis chamem.</span><span class="sxs-lookup"><span data-stu-id="43c13-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="43c13-104">Tais métodos representam vários riscos: O método pode fornecer algumas informações restritas; ele pode acreditar que qualquer informação passou para ele, mas ele não pode pode não fazer verificação de erros nos parâmetros; ou com os parâmetros errados, pode funcionar mal ou fazer algo prejudicial.</span><span class="sxs-lookup"><span data-stu-id="43c13-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="43c13-105">Você deve estar ciente desses casos e tomar medidas para ajudar a proteger o método.</span><span class="sxs-lookup"><span data-stu-id="43c13-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="43c13-106">Em alguns casos, você pode precisar restringir métodos que não são destinados ao uso público, mas ainda devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="43c13-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="43c13-107">Por exemplo, você pode ter uma interface que precisa ser chamada através de seus próprios DLLs e, portanto, deve ser pública, mas você não quer expô-la publicamente para impedir que os clientes o usem ou para impedir que o código malicioso explore o ponto de entrada em seu componente.</span><span class="sxs-lookup"><span data-stu-id="43c13-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="43c13-108">Outra razão comum para restringir um método não destinado ao uso público (mas que deve ser público) é evitar ter que documentar e apoiar o que pode ser uma interface muito interna.</span><span class="sxs-lookup"><span data-stu-id="43c13-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="43c13-109">O código gerenciado oferece várias maneiras de restringir o acesso ao método:</span><span class="sxs-lookup"><span data-stu-id="43c13-109">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="43c13-110">Limite o escopo de acessibilidade às classes de classe, montagem ou derivada, se elas forem confiáveis.</span><span class="sxs-lookup"><span data-stu-id="43c13-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="43c13-111">Esta é a maneira mais simples de limitar o acesso ao método.</span><span class="sxs-lookup"><span data-stu-id="43c13-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="43c13-112">Note que, em geral, as classes derivadas podem ser menos confiáveis do que a classe de que derivam, embora em alguns casos compartilhem a identidade da classe pai.</span><span class="sxs-lookup"><span data-stu-id="43c13-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="43c13-113">Em particular, não inferir confiança da palavra-chave **protegida,** que não é necessariamente usada no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="43c13-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="43c13-114">Limite o acesso do método aos chamadores de uma identidade especificada — essencialmente, qualquer [evidência](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) específica (nome forte, editor, zona e assim por diante) você escolhe.</span><span class="sxs-lookup"><span data-stu-id="43c13-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="43c13-115">Limite o acesso do método aos chamadores que tenham as permissões selecionadas.</span><span class="sxs-lookup"><span data-stu-id="43c13-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="43c13-116">Da mesma forma, a segurança declarativa permite controlar a herança das classes.</span><span class="sxs-lookup"><span data-stu-id="43c13-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="43c13-117">Você pode usar **A HerançaDemanda** para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="43c13-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="43c13-118">Exija que as classes derivadas tenham uma identidade ou permissão especificadas.</span><span class="sxs-lookup"><span data-stu-id="43c13-118">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="43c13-119">Requerem classes derivadas que sobrepõem métodos específicos para ter uma identidade ou permissão especificadas.</span><span class="sxs-lookup"><span data-stu-id="43c13-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="43c13-120">O exemplo a seguir mostra como ajudar a proteger uma classe pública para acesso limitado, exigindo que os chamadores sejam assinados com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="43c13-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="43c13-121">Este exemplo <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> usa o com uma **Demanda** para o nome forte.</span><span class="sxs-lookup"><span data-stu-id="43c13-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="43c13-122">Para obter informações baseadas em tarefas sobre como assinar um conjunto com um nome forte, consulte [Criando e Usando Conjuntos com Nomes Fortes](../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="43c13-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="43c13-123">Excluindo classes e membros do uso por código não confiável</span><span class="sxs-lookup"><span data-stu-id="43c13-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="43c13-124">Use as declarações mostradas nesta seção para evitar que classes e métodos específicos, bem como propriedades e eventos, sejam usados por código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="43c13-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="43c13-125">Ao aplicar essas declarações a uma classe, você aplica a proteção a todos os seus métodos, propriedades e eventos; no entanto, observe que o acesso ao campo não é afetado pela segurança declarativa.</span><span class="sxs-lookup"><span data-stu-id="43c13-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="43c13-126">Observe também que as demandas de links ajudam a proteger apenas contra os chamadores imediatos e ainda podem estar sujeitas a ataques de atração.</span><span class="sxs-lookup"><span data-stu-id="43c13-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43c13-127">Um novo modelo de transparência foi introduzido no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="43c13-127">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="43c13-128">O modelo [Security-Transparent Code, Nível 2,](security-transparent-code-level-2.md) identifica código seguro com o atributo. <xref:System.Security.SecurityCriticalAttribute></span><span class="sxs-lookup"><span data-stu-id="43c13-128">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="43c13-129">O código crítico de segurança exige que tanto os chamadores quanto os herdeiros sejam totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="43c13-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="43c13-130">Os conjuntos que estão sendo executados sob as regras de segurança de acesso ao código de versões anteriores do .NET Framework podem chamar conjuntos de nível 2.</span><span class="sxs-lookup"><span data-stu-id="43c13-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="43c13-131">Neste caso, os atributos críticos à segurança serão tratados como demandas de link para a confiança total.</span><span class="sxs-lookup"><span data-stu-id="43c13-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="43c13-132">Em conjuntos com nomes fortes, um [LinkDemand](link-demands.md) é aplicado a todos os métodos, propriedades e eventos acessíveis publicamente para restringir seu uso a chamadores totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="43c13-132">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="43c13-133">Para desativar esse recurso, você <xref:System.Security.AllowPartiallyTrustedCallersAttribute> deve aplicar o atributo.</span><span class="sxs-lookup"><span data-stu-id="43c13-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="43c13-134">Assim, marcar explicitamente classes para excluir chamadores não confiáveis é necessário apenas para assembléias ou assembléias não assinadas com este atributo; você pode usar essas declarações para marcar um subconjunto de tipos nelas que não são destinados a chamadores não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="43c13-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="43c13-135">Os exemplos a seguir mostram como evitar que classes e membros sejam usados por código não confiável.</span><span class="sxs-lookup"><span data-stu-id="43c13-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="43c13-136">Para classes públicas não seladas:</span><span class="sxs-lookup"><span data-stu-id="43c13-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="43c13-137">Para aulas públicas lacradas:</span><span class="sxs-lookup"><span data-stu-id="43c13-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="43c13-138">Para aulas abstratas públicas:</span><span class="sxs-lookup"><span data-stu-id="43c13-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="43c13-139">Para funções virtuais públicas:</span><span class="sxs-lookup"><span data-stu-id="43c13-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="43c13-140">Para funções abstratas públicas:</span><span class="sxs-lookup"><span data-stu-id="43c13-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="43c13-141">Para funções de substituição pública onde a classe base não exige confiança total:</span><span class="sxs-lookup"><span data-stu-id="43c13-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="43c13-142">Para funções de substituição pública onde a classe base exige total confiança:</span><span class="sxs-lookup"><span data-stu-id="43c13-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="43c13-143">Para interfaces públicas:</span><span class="sxs-lookup"><span data-stu-id="43c13-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="43c13-144">Substituições com virtual internal ou Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="43c13-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43c13-145">Esta seção adverte sobre um problema de `virtual` segurança `internal` `Overloads` `Overridable` ao declarar um método como ambos e (no `Friend` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="43c13-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="43c13-146">Este aviso se aplica apenas às versões .NET Framework 1.0 e 1.1, não se aplica às versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="43c13-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="43c13-147">Nas versões .NET Framework 1.0 e 1.1, você deve estar ciente de uma nuance da acessibilidade do sistema do tipo ao confirmar que seu código não está disponível para outros conjuntos.</span><span class="sxs-lookup"><span data-stu-id="43c13-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="43c13-148">Um método declarado **virtual** e **interno** **(Overloads Overridable Friend** in Visual Basic) pode substituir a entrada vtable da classe pai e só pode ser usado dentro do mesmo conjunto porque é interno.</span><span class="sxs-lookup"><span data-stu-id="43c13-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="43c13-149">No entanto, a acessibilidade para substituição é determinada pela palavra-chave **virtual,** e isso pode ser substituído de outra montagem, desde que esse código tenha acesso à própria classe.</span><span class="sxs-lookup"><span data-stu-id="43c13-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="43c13-150">Se a possibilidade de uma substituição apresentar um problema, use segurança declarativa para corrigi-lo ou remova a palavra-chave **virtual** se não for estritamente necessária.</span><span class="sxs-lookup"><span data-stu-id="43c13-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="43c13-151">Observe que, mesmo que um compilador de idiomas impeça essas substituições com um erro de compilação, é possível que o código escrito com outros compiladores seja substituído.</span><span class="sxs-lookup"><span data-stu-id="43c13-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c13-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="43c13-152">See also</span></span>

- [<span data-ttu-id="43c13-153">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="43c13-153">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
