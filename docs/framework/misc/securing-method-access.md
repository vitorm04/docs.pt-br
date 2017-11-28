---
title: "Protegendo o acesso dos métodos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 40d073a2ae390a434f5bf4562da7a6226993cfcb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="securing-method-access"></a><span data-ttu-id="6b33a-102">Protegendo o acesso dos métodos</span><span class="sxs-lookup"><span data-stu-id="6b33a-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="6b33a-103">Alguns métodos podem não ser adequados para permitir a chamar código não confiável arbitrário.</span><span class="sxs-lookup"><span data-stu-id="6b33a-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="6b33a-104">Esses métodos apresentam vários riscos: O método pode fornecer algumas informações restritas; ele pode achar qualquer informação passada para ele; ele não pode fazer a verificação de erro em parâmetros. ou com parâmetros incorretos, talvez ele mau funcionamento ou fazer algo prejudiciais.</span><span class="sxs-lookup"><span data-stu-id="6b33a-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="6b33a-105">Você deve estar ciente desses casos e tomar medidas para ajudar a proteger o método.</span><span class="sxs-lookup"><span data-stu-id="6b33a-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="6b33a-106">Em alguns casos, convém restringir os métodos que não se destina para uso público, mas ainda devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="6b33a-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="6b33a-107">Por exemplo, você pode ter uma interface que precisa ser chamado em seus próprio DLLs e, portanto, deve ser públicos, mas você não deseja expor publicamente para impedir que os clientes usá-lo ou para impedir que um código mal-intencionado Explorando o ponto de entrada em seu componente.</span><span class="sxs-lookup"><span data-stu-id="6b33a-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="6b33a-108">Outro motivo comum para restringir um método não se destina para uso público (mas que devem ser públicos) é evitar ter de documento e suporte que pode haver uma interface muito interna.</span><span class="sxs-lookup"><span data-stu-id="6b33a-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="6b33a-109">Gerenciado código oferece várias maneiras para restringir o acesso do método:</span><span class="sxs-lookup"><span data-stu-id="6b33a-109">Managed code offers several ways to restrict method access:</span></span>  
  
-   <span data-ttu-id="6b33a-110">Limite o escopo de acessibilidade para a classe, assembly ou classes derivadas, se eles podem ser confiáveis.</span><span class="sxs-lookup"><span data-stu-id="6b33a-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="6b33a-111">Essa é a maneira mais simples para limitar o acesso do método.</span><span class="sxs-lookup"><span data-stu-id="6b33a-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="6b33a-112">Observe que, em geral, as classes derivadas podem ser menos confiáveis do que a classe que derivam, embora em alguns casos, eles compartilham identidade da classe pai.</span><span class="sxs-lookup"><span data-stu-id="6b33a-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="6b33a-113">Em particular, não deduzir a relação de confiança da palavra-chave **protegido**, que não é necessariamente usado no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="6b33a-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
-   <span data-ttu-id="6b33a-114">Limitar o acesso de método para chamadores de uma identidade especificada – essencialmente, qualquer [evidência](http://msdn.microsoft.com/en-us/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (nome forte, publisher, zona e assim por diante) que você escolher.</span><span class="sxs-lookup"><span data-stu-id="6b33a-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](http://msdn.microsoft.com/en-us/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
-   <span data-ttu-id="6b33a-115">Limite o acesso de método para chamadores com as permissões que você selecionar.</span><span class="sxs-lookup"><span data-stu-id="6b33a-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="6b33a-116">Da mesma forma, a segurança declarativa permite controlar a herança de classes.</span><span class="sxs-lookup"><span data-stu-id="6b33a-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="6b33a-117">Você pode usar **InheritanceDemand** para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6b33a-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
-   <span data-ttu-id="6b33a-118">Exigir classes derivadas para ter uma identidade especificada ou a permissão.</span><span class="sxs-lookup"><span data-stu-id="6b33a-118">Require derived classes to have a specified identity or permission.</span></span>  
  
-   <span data-ttu-id="6b33a-119">Exigir classes derivadas que substituem os métodos específicos para ter uma identidade especificada ou a permissão.</span><span class="sxs-lookup"><span data-stu-id="6b33a-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="6b33a-120">O exemplo a seguir mostra como proteger uma classe pública para acesso limitado, exigindo que os chamadores sejam assinados com um determinado nome forte.</span><span class="sxs-lookup"><span data-stu-id="6b33a-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="6b33a-121">Este exemplo usa o <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> com um **demanda** para o nome forte.</span><span class="sxs-lookup"><span data-stu-id="6b33a-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="6b33a-122">Para baseado em tarefa obter informações sobre como assinar um assembly com um nome forte, consulte [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6b33a-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="6b33a-123">Excluindo classes e membros do uso por código não confiável</span><span class="sxs-lookup"><span data-stu-id="6b33a-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="6b33a-124">Use as declarações mostradas nesta seção para impedir que classes específicas e métodos, bem como propriedades e eventos, que está sendo usado por código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="6b33a-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="6b33a-125">Aplicando essas declarações para uma classe, você deve aplicar a proteção para todos os seus métodos, propriedades e eventos; No entanto, observe que o acesso de campo não é afetado por segurança declarativa.</span><span class="sxs-lookup"><span data-stu-id="6b33a-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="6b33a-126">Observe também que as demandas de link ajudam a proteger contra somente os chamadores imediatos e ainda podem estar sujeita a ataques de atração.</span><span class="sxs-lookup"><span data-stu-id="6b33a-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b33a-127">Um novo modelo de transparência foi introduzido no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b33a-127">A new transparency model has been introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="6b33a-128">O [código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modelo identifica o código de segurança com o <xref:System.Security.SecurityCriticalAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="6b33a-128">The [Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="6b33a-129">Código crítico de segurança requer que os chamadores e herdeiros ser totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="6b33a-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="6b33a-130">Os assemblies que estão sendo executados sob as regras de segurança de acesso do código de versões anteriores do .NET Framework podem chamar assemblies de nível 2.</span><span class="sxs-lookup"><span data-stu-id="6b33a-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="6b33a-131">Nesse caso, os atributos de segurança crítica serão tratados como demandas de link de confiança total.</span><span class="sxs-lookup"><span data-stu-id="6b33a-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="6b33a-132">Em assemblies de nome forte, um [LinkDemand](../../../docs/framework/misc/link-demands.md) é aplicado a todos os eventos para restringir o uso para os chamadores totalmente confiáveis, propriedades e métodos publicamente acessíveis.</span><span class="sxs-lookup"><span data-stu-id="6b33a-132">In strong-named assemblies, a [LinkDemand](../../../docs/framework/misc/link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="6b33a-133">Para desabilitar esse recurso, você deve aplicar o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="6b33a-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="6b33a-134">Assim, é necessário somente para assemblies não assinados ou assemblies com esse atributo; marcar explicitamente classes para excluir os chamadores não confiáveis Você pode usar essas declarações para marcar um subconjunto de tipos contidos que não são destinadas para chamadores não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="6b33a-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="6b33a-135">Os exemplos a seguir mostram como evitar classes e membros que está sendo usado por código não confiável.</span><span class="sxs-lookup"><span data-stu-id="6b33a-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="6b33a-136">Para as classes públicas nonsealed:</span><span class="sxs-lookup"><span data-stu-id="6b33a-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="6b33a-137">Para public lacrado classes:</span><span class="sxs-lookup"><span data-stu-id="6b33a-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="6b33a-138">Para classes abstratas públicas:</span><span class="sxs-lookup"><span data-stu-id="6b33a-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="6b33a-139">Para funções virtuais públicas:</span><span class="sxs-lookup"><span data-stu-id="6b33a-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="6b33a-140">Para funções abstract públicas:</span><span class="sxs-lookup"><span data-stu-id="6b33a-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="6b33a-141">Para funções de substituição pública em que a classe base não exigem confiança total:</span><span class="sxs-lookup"><span data-stu-id="6b33a-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="6b33a-142">Para funções de substituição pública em que a classe base exige confiança total:</span><span class="sxs-lookup"><span data-stu-id="6b33a-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="6b33a-143">Para interfaces públicas:</span><span class="sxs-lookup"><span data-stu-id="6b33a-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="6b33a-144">Substituições com virtual internal ou Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="6b33a-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b33a-145">Esta seção avisa sobre um problema de segurança ao declarar um método como `virtual` e `internal` (`Overloads``Overridable``Friend` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6b33a-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads``Overridable``Friend` in Visual Basic).</span></span> <span data-ttu-id="6b33a-146">Este aviso se aplica somente às versões do .NET Framework 1.0 e 1.1, não se aplica a versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="6b33a-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="6b33a-147">Nas versões do .NET Framework 1.0 e 1.1, você deve estar atento um nuance de acessibilidade do sistema de tipo durante a confirmação de que seu código não está disponível para outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="6b33a-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="6b33a-148">Um método que é declarado **virtual** e **interno** (**sobrecargas substituível Friend** no Visual Basic) pode substituir a entrada de vtable da classe pai e pode ser usado somente em dentro do mesmo assembly porque é interno.</span><span class="sxs-lookup"><span data-stu-id="6b33a-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="6b33a-149">No entanto, a acessibilidade de substituição é determinada pelo **virtual** palavra-chave e isso pode ser substituído de outro assembly, desde que o código tenha acesso à própria classe.</span><span class="sxs-lookup"><span data-stu-id="6b33a-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="6b33a-150">Se a possibilidade de uma substituição apresenta um problema, use a segurança declarativa para corrigi-lo, ou remova o **virtual** palavra-chave se ela não é estritamente necessária.</span><span class="sxs-lookup"><span data-stu-id="6b33a-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="6b33a-151">Observe que, mesmo que um compilador de linguagem impede que essas substituições com um erro de compilação, é possível que código gravado com outros compiladores para substituir.</span><span class="sxs-lookup"><span data-stu-id="6b33a-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b33a-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b33a-152">See Also</span></span>  
 [<span data-ttu-id="6b33a-153">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="6b33a-153">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
