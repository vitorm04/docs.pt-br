---
title: Protegendo o acesso dos métodos
description: Saiba como tornar o método acesso seguro para métodos que não são destinados ao uso público, mas que ainda precisam ser públicos.
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
ms.openlocfilehash: 88868ab29fc37854959a044b9c0fed5bd8c82d77
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855758"
---
# <a name="securing-method-access"></a><span data-ttu-id="79bed-103">Protegendo o acesso dos métodos</span><span class="sxs-lookup"><span data-stu-id="79bed-103">Securing Method Access</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="79bed-104">Alguns métodos podem não ser adequados para permitir que um código não confiável arbitrário chame.</span><span class="sxs-lookup"><span data-stu-id="79bed-104">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="79bed-105">Esses métodos apresentam vários riscos: o método pode fornecer algumas informações restritas; pode acreditar que todas as informações sejam passadas para ele; Ele pode não fazer a verificação de erro nos parâmetros; ou com os parâmetros errados, ele pode não funcionar ou fazer algo prejudicial.</span><span class="sxs-lookup"><span data-stu-id="79bed-105">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="79bed-106">Você deve estar atento a esses casos e tomar medidas para ajudar a proteger o método.</span><span class="sxs-lookup"><span data-stu-id="79bed-106">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="79bed-107">Em alguns casos, talvez seja necessário restringir métodos que não são destinados ao uso público, mas que ainda devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="79bed-107">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="79bed-108">Por exemplo, você pode ter uma interface que precisa ser chamada em suas próprias DLLs e, portanto, deve ser pública, mas você não deseja expô-las publicamente para impedir que os clientes as usem ou para impedir que códigos mal-intencionados explorem o ponto de entrada em seu componente.</span><span class="sxs-lookup"><span data-stu-id="79bed-108">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="79bed-109">Outro motivo comum para restringir um método não destinado ao uso público (mas que deve ser público) é evitar ter que documentar e dar suporte ao que pode ser uma interface interna.</span><span class="sxs-lookup"><span data-stu-id="79bed-109">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be an internal interface.</span></span>  
  
 <span data-ttu-id="79bed-110">O código gerenciado oferece várias maneiras de restringir o acesso ao método:</span><span class="sxs-lookup"><span data-stu-id="79bed-110">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="79bed-111">Limite o escopo de acessibilidade à classe, ao assembly ou às classes derivadas, se eles puderem ser confiáveis.</span><span class="sxs-lookup"><span data-stu-id="79bed-111">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="79bed-112">Essa é a maneira mais simples de limitar o acesso do método.</span><span class="sxs-lookup"><span data-stu-id="79bed-112">This is the simplest way to limit method access.</span></span> <span data-ttu-id="79bed-113">Em geral, as classes derivadas podem ser menos confiáveis do que a classe da qual derivam, embora, em alguns casos, eles compartilhem a identidade da classe pai.</span><span class="sxs-lookup"><span data-stu-id="79bed-113">In general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="79bed-114">Em particular, não infere confiança da palavra-chave `protected` , que não é necessariamente usada no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="79bed-114">In particular, do not infer trust from the keyword `protected`, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="79bed-115">Limitar o acesso do método a chamadores de uma identidade especificada – essencialmente, qualquer [evidência](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) específica (nome forte, Publicador, zona e assim por diante) que você escolher.</span><span class="sxs-lookup"><span data-stu-id="79bed-115">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="79bed-116">Limite o método de acesso a chamadores que têm quaisquer permissões que você selecionar.</span><span class="sxs-lookup"><span data-stu-id="79bed-116">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="79bed-117">Da mesma forma, a segurança declarativa permite que você controle a herança de classes.</span><span class="sxs-lookup"><span data-stu-id="79bed-117">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="79bed-118">Você pode usar **InheritanceDemand** para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="79bed-118">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="79bed-119">Exigir que classes derivadas tenham uma identidade ou permissão especificada.</span><span class="sxs-lookup"><span data-stu-id="79bed-119">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="79bed-120">Exigir classes derivadas que substituam métodos específicos para ter uma identidade ou permissão especificada.</span><span class="sxs-lookup"><span data-stu-id="79bed-120">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="79bed-121">O exemplo a seguir mostra como ajudar a proteger uma classe pública para acesso limitado, exigindo que os chamadores sejam assinados com um nome forte específico.</span><span class="sxs-lookup"><span data-stu-id="79bed-121">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="79bed-122">Este exemplo usa o <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> com uma **demanda** para o nome forte.</span><span class="sxs-lookup"><span data-stu-id="79bed-122">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="79bed-123">Para obter informações baseadas em tarefas sobre como assinar um assembly com um nome forte, consulte [criando e usando assemblies de nome forte](../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="79bed-123">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="79bed-124">Excluindo classes e membros do uso por código não confiável</span><span class="sxs-lookup"><span data-stu-id="79bed-124">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="79bed-125">Use as declarações mostradas nesta seção para impedir que classes e métodos específicos, bem como propriedades e eventos, sejam usados pelo código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="79bed-125">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="79bed-126">Aplicando essas declarações a uma classe, você aplica a proteção a todos os seus métodos, propriedades e eventos.</span><span class="sxs-lookup"><span data-stu-id="79bed-126">By applying these declarations to a class, you apply the protection to all its methods, properties, and events.</span></span> <span data-ttu-id="79bed-127">No entanto, o acesso ao campo não é afetado pela segurança declarativa.</span><span class="sxs-lookup"><span data-stu-id="79bed-127">However, field access is not affected by declarative security.</span></span> <span data-ttu-id="79bed-128">Observe também que as demandas de link ajudam a proteger contra apenas os chamadores imediatos e podem ainda estar sujeitos a ataques chamariz.</span><span class="sxs-lookup"><span data-stu-id="79bed-128">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79bed-129">Um novo modelo de transparência foi introduzido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="79bed-129">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="79bed-130">O [código de segurança transparente, modelo de nível 2,](security-transparent-code-level-2.md) identifica o código seguro com o <xref:System.Security.SecurityCriticalAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="79bed-130">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="79bed-131">O código de segurança crítica exige que os chamadores e os herdeiros sejam totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="79bed-131">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="79bed-132">Os assemblies que estão em execução nas regras de segurança de acesso ao código de versões anteriores do .NET Framework podem chamar assemblies de nível 2.</span><span class="sxs-lookup"><span data-stu-id="79bed-132">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="79bed-133">Nesse caso, os atributos de segurança crítica serão tratados como demandas de link para confiança total.</span><span class="sxs-lookup"><span data-stu-id="79bed-133">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="79bed-134">Em assemblies de nome forte, um [LinkDemand](link-demands.md) é aplicado a todos os métodos, propriedades e eventos publicamente acessíveis para restringir seu uso a chamadores totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="79bed-134">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="79bed-135">Para desabilitar esse recurso, você deve aplicar o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="79bed-135">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="79bed-136">Portanto, marcar explicitamente as classes para excluir chamadores não confiáveis é necessário apenas para assemblies não assinados ou assemblies com esse atributo; Você pode usar essas declarações para marcar um subconjunto de tipos que não se destinam a chamadores não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="79bed-136">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="79bed-137">Os exemplos a seguir mostram como impedir que classes e membros sejam usados por código não confiável.</span><span class="sxs-lookup"><span data-stu-id="79bed-137">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="79bed-138">Para classes não seladas públicas:</span><span class="sxs-lookup"><span data-stu-id="79bed-138">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="79bed-139">Para classes lacradas públicas:</span><span class="sxs-lookup"><span data-stu-id="79bed-139">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="79bed-140">Para classes abstratas públicas:</span><span class="sxs-lookup"><span data-stu-id="79bed-140">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="79bed-141">Para funções virtuais públicas:</span><span class="sxs-lookup"><span data-stu-id="79bed-141">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="79bed-142">Para funções abstratas públicas:</span><span class="sxs-lookup"><span data-stu-id="79bed-142">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="79bed-143">Para funções de substituição pública em que a classe base não exige confiança total:</span><span class="sxs-lookup"><span data-stu-id="79bed-143">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="79bed-144">Para funções de substituição pública em que a classe base exige confiança total:</span><span class="sxs-lookup"><span data-stu-id="79bed-144">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="79bed-145">Para interfaces públicas:</span><span class="sxs-lookup"><span data-stu-id="79bed-145">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="79bed-146">Substituições com virtual internal ou Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="79bed-146">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79bed-147">Esta seção avisa sobre um problema de segurança ao declarar um método como `virtual` e `internal` ( `Overloads` `Overridable` `Friend` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="79bed-147">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="79bed-148">Esse aviso se aplica somente às versões 1,0 e 1,1 do .NET Framework e não se aplica a versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="79bed-148">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="79bed-149">No .NET Framework versões 1,0 e 1,1, você deve estar ciente de uma nuance do tipo acessibilidade do sistema ao confirmar que seu código não está disponível para outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="79bed-149">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="79bed-150">Um método declarado **virtual** e **interno** (**sobrecargas Friend presubstituíveis** em Visual Basic) pode substituir a entrada vtable da classe pai e pode ser usado somente de dentro do mesmo assembly porque ele é interno.</span><span class="sxs-lookup"><span data-stu-id="79bed-150">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="79bed-151">No entanto, a acessibilidade para substituição é determinada pela palavra-chave **virtual** , e isso pode ser substituído de outro assembly, desde que o código tenha acesso à própria classe.</span><span class="sxs-lookup"><span data-stu-id="79bed-151">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="79bed-152">Se a possibilidade de uma substituição apresentar um problema, use a segurança declarativa para corrigi-lo ou remova a palavra-chave **virtual** se ela não for estritamente necessária.</span><span class="sxs-lookup"><span data-stu-id="79bed-152">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="79bed-153">Mesmo que um compilador de linguagem impeça essas substituições com um erro de compilação, é possível que o código escrito com outros compiladores substitua.</span><span class="sxs-lookup"><span data-stu-id="79bed-153">Even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79bed-154">Veja também</span><span class="sxs-lookup"><span data-stu-id="79bed-154">See also</span></span>

- [<span data-ttu-id="79bed-155">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="79bed-155">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
