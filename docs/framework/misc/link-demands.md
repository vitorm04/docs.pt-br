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
ms.openlocfilehash: 31fbd938acb457a4ea803375d18cb1be11d8b287
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217166"
---
# <a name="link-demands"></a><span data-ttu-id="8df02-102">Demandas de link</span><span class="sxs-lookup"><span data-stu-id="8df02-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="8df02-103">Uma demanda de link causa uma verificação de segurança durante a compilação just-in-time e verifica apenas o assembly de chamada imediata do seu código.</span><span class="sxs-lookup"><span data-stu-id="8df02-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="8df02-104">A vinculação ocorre quando seu código está associado a uma referência de tipo, incluindo referências de ponteiro de função e chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="8df02-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="8df02-105">Se o assembly de chamada não tiver permissão suficiente para vincular ao seu código, o link não será permitido e uma exceção de tempo de execução será lançada quando o código for carregado e executado.</span><span class="sxs-lookup"><span data-stu-id="8df02-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="8df02-106">As demandas de link podem ser substituídas em classes que herdam do seu código.</span><span class="sxs-lookup"><span data-stu-id="8df02-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="8df02-107">Observe que uma movimentação de pilha completa não é executada com esse tipo de demanda e que seu código ainda está suscetível a ataques de chamariz.</span><span class="sxs-lookup"><span data-stu-id="8df02-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="8df02-108">Por exemplo, se um método no assembly A for protegido por uma demanda de link, um chamador direto no assembly B será avaliado com base nas permissões do assembly B.  No entanto, a demanda de link não avaliará um método no assembly C se ele chamar indiretamente o método no assembly A usando o método no assembly B. A demanda de link especifica somente as permissões que os chamadores diretos no assembly de chamada imediata devem ter que vincular ao seu código.</span><span class="sxs-lookup"><span data-stu-id="8df02-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="8df02-109">Ele não especifica as permissões que todos os chamadores devem ter para executar seu código.</span><span class="sxs-lookup"><span data-stu-id="8df02-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="8df02-110">Os modificadores <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>e <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk não afetam a avaliação das demandas de link.</span><span class="sxs-lookup"><span data-stu-id="8df02-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="8df02-111">Como as demandas de link não executam uma movimentação de pilha, os modificadores de movimentação de pilha não têm nenhum efeito nas demandas de link.</span><span class="sxs-lookup"><span data-stu-id="8df02-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="8df02-112">Se um método protegido por uma demanda de link for acessado por meio de [reflexão](../reflection-and-codedom/reflection.md), uma demanda de link verificará o chamador imediato do código acessado por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="8df02-112">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="8df02-113">Isso é verdadeiro para a descoberta de método e para invocação de método executada usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="8df02-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="8df02-114">Por exemplo, suponha que o código use a reflexão para retornar um objeto de <xref:System.Reflection.MethodInfo> que representa um método protegido por uma demanda de link e, em seguida, passa esse objeto **MethodInfo** para algum outro código que usa o objeto para invocar o método original.</span><span class="sxs-lookup"><span data-stu-id="8df02-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="8df02-115">Nesse caso, a verificação de demanda de link ocorre duas vezes: uma vez para o código que retorna o objeto **MethodInfo** e uma vez para o código que o invoca.</span><span class="sxs-lookup"><span data-stu-id="8df02-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8df02-116">Uma demanda de link executada em um construtor de classe estática não protege o construtor porque construtores estáticos são chamados pelo sistema, fora do caminho de execução de código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8df02-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="8df02-117">Como resultado, quando uma demanda de link é aplicada a uma classe inteira, ela não pode proteger o acesso a um construtor estático, embora proteja o restante da classe.</span><span class="sxs-lookup"><span data-stu-id="8df02-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="8df02-118">O fragmento de código a seguir especifica declarativamente que qualquer vinculação de código com o método `ReadData` deve ter a permissão `CustomPermission`.</span><span class="sxs-lookup"><span data-stu-id="8df02-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="8df02-119">Essa permissão é uma permissão personalizada hipotética e não existe no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8df02-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="8df02-120">A demanda é feita passando um sinalizador **SecurityAction. LinkDemand** para a `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8df02-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8df02-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="8df02-121">See also</span></span>

- [<span data-ttu-id="8df02-122">Atributos</span><span class="sxs-lookup"><span data-stu-id="8df02-122">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="8df02-123">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="8df02-123">Code Access Security</span></span>](code-access-security.md)
