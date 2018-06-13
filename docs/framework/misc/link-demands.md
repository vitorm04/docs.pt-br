---
title: Demandas de link
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29a3254bb5ccfe422a1c2d7d156975c0887d9273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390657"
---
# <a name="link-demands"></a><span data-ttu-id="e5c90-102">Demandas de link</span><span class="sxs-lookup"><span data-stu-id="e5c90-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="e5c90-103">Uma demanda de link faz com que uma verificação de segurança durante a compilação just-in-time e verifica somente o assembly de chamada imediato do seu código.</span><span class="sxs-lookup"><span data-stu-id="e5c90-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="e5c90-104">Vinculando ocorre quando seu código é associado a uma referência de tipo, incluindo referências de ponteiro de função e chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="e5c90-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="e5c90-105">Se o assembly de chamada não tem permissão suficiente para vincular ao seu código, o link não é permitido e uma exceção de tempo de execução é gerada quando o código é carregado e executado.</span><span class="sxs-lookup"><span data-stu-id="e5c90-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="e5c90-106">Demandas de link podem ser substituídas nas classes que herdam de seu código.</span><span class="sxs-lookup"><span data-stu-id="e5c90-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="e5c90-107">Observe que um exame da pilha completa não será executado com esse tipo de demanda e que seu código ainda é suscetível a ataques de atração.</span><span class="sxs-lookup"><span data-stu-id="e5c90-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="e5c90-108">Por exemplo, se um método no assembly A é protegido por uma demanda de link, um chamador direto no assembly B é avaliado com base nas permissões do Assembly B.  No entanto, a demanda de link não avaliará um método no assembly C se indiretamente chama o método no assembly usando o método no assembly B. A demanda de link Especifica que apenas as permissões de direcionam os chamadores no assembly de chamada imediato devem ter que vincular ao seu código.</span><span class="sxs-lookup"><span data-stu-id="e5c90-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="e5c90-109">Ele não especifica as permissões de todos os chamadores devem ter para executar seu código.</span><span class="sxs-lookup"><span data-stu-id="e5c90-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="e5c90-110">O <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, e <xref:System.Security.CodeAccessPermission.PermitOnly%2A> modificadores de movimentação de pilha não afetam a avaliação de demandas de link.</span><span class="sxs-lookup"><span data-stu-id="e5c90-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="e5c90-111">Como as demandas de link não executam um exame da pilha, os modificadores de movimentação de pilha não têm efeito nas demandas de link.</span><span class="sxs-lookup"><span data-stu-id="e5c90-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="e5c90-112">Se um método protegido por uma demanda de link é acessado por meio de [reflexão](../../../docs/framework/reflection-and-codedom/reflection.md), em seguida, uma demanda de link verifica o chamador imediato do código acessado por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="e5c90-112">If a method protected by a link demand is accessed through [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="e5c90-113">Isso é verdadeiro para descoberta de método e executada usando a reflexão de invocação de método.</span><span class="sxs-lookup"><span data-stu-id="e5c90-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="e5c90-114">Por exemplo, suponha que o código usa reflexão para retornar um <xref:System.Reflection.MethodInfo> do objeto que representa um método protegido por uma demanda de link e, em seguida, passa que **MethodInfo** objeto para algum outro código que usa o objeto para invocar o método original.</span><span class="sxs-lookup"><span data-stu-id="e5c90-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="e5c90-115">Nesse caso a verificação de demanda de link ocorre duas vezes: uma vez para o código que retorna o **MethodInfo** objeto e uma vez para o código que o chama.</span><span class="sxs-lookup"><span data-stu-id="e5c90-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5c90-116">Uma demanda de link executada em um construtor de classe estática não protege o construtor porque construtores estáticos são chamados pelo sistema, fora do caminho de execução de código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5c90-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="e5c90-117">Como resultado, quando uma demanda de link é aplicada a uma classe inteira, ele não pode proteger o acesso a um construtor estático, embora ele protege o restante da classe.</span><span class="sxs-lookup"><span data-stu-id="e5c90-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="e5c90-118">O fragmento de código a seguir declarativamente Especifica que qualquer código de vinculação para o `ReadData` método deve ter o `CustomPermission` permissão.</span><span class="sxs-lookup"><span data-stu-id="e5c90-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="e5c90-119">Essa permissão é uma permissão personalizada hipotética e não existe no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5c90-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="e5c90-120">A solicitação é feita, passando um **SecurityAction.LinkDemand** sinalizador como o `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="e5c90-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function    
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5c90-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5c90-121">See Also</span></span>  
 [<span data-ttu-id="e5c90-122">Atributos</span><span class="sxs-lookup"><span data-stu-id="e5c90-122">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="e5c90-123">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="e5c90-123">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
