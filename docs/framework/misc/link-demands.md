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
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181167"
---
# <a name="link-demands"></a><span data-ttu-id="d4d56-102">Demandas de link</span><span class="sxs-lookup"><span data-stu-id="d4d56-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="d4d56-103">Uma demanda de link causa uma verificação de segurança durante a compilação just-in-time e verifica apenas a montagem imediata de chamada do seu código.</span><span class="sxs-lookup"><span data-stu-id="d4d56-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="d4d56-104">A vinculação ocorre quando seu código está vinculado a uma referência de tipo, incluindo referências de ponteiro de função e chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="d4d56-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="d4d56-105">Se a assembléia de chamada não tiver permissão suficiente para vincular ao seu código, o link não é permitido e uma exceção em tempo de execução é lançada quando o código é carregado e executado.</span><span class="sxs-lookup"><span data-stu-id="d4d56-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="d4d56-106">As demandas de link podem ser substituídas em classes que herdam do seu código.</span><span class="sxs-lookup"><span data-stu-id="d4d56-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="d4d56-107">Observe que uma caminhada de pilha completa não é realizada com esse tipo de demanda e que seu código ainda é suscetível a atrair ataques.</span><span class="sxs-lookup"><span data-stu-id="d4d56-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="d4d56-108">Por exemplo, se um método na montagem A for protegido por uma demanda de link, um chamador direto no conjunto B será avaliado com base nas permissões da Assembléia B.  No entanto, a demanda de link não avaliará um método na montagem C se ele chamar indiretamente o método na montagem A usando o método na montagem B. A demanda de link especifica apenas as permissões que os chamadores diretos na assembléia de chamada imediata devem ter que vincular ao seu código.</span><span class="sxs-lookup"><span data-stu-id="d4d56-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="d4d56-109">Ele não especifica as permissões que todos os chamadores devem ter para executar seu código.</span><span class="sxs-lookup"><span data-stu-id="d4d56-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="d4d56-110">Os <xref:System.Security.CodeAccessPermission.Assert%2A> <xref:System.Security.CodeAccessPermission.Deny%2A>modificadores <xref:System.Security.CodeAccessPermission.PermitOnly%2A> de caminhada e pilha não afetam a avaliação das demandas de link.</span><span class="sxs-lookup"><span data-stu-id="d4d56-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="d4d56-111">Como as demandas de link não realizam uma caminhada de pilha, os modificadores de caminhada de pilha não têm efeito sobre as demandas de link.</span><span class="sxs-lookup"><span data-stu-id="d4d56-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="d4d56-112">Se um método protegido por uma demanda de link for acessado através do [Reflection,](../reflection-and-codedom/reflection.md)então uma demanda de link verifica o chamador imediato do código acessado através da reflexão.</span><span class="sxs-lookup"><span data-stu-id="d4d56-112">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="d4d56-113">Isso é verdade tanto para a descoberta do método quanto para a invocação do método realizada com reflexão.</span><span class="sxs-lookup"><span data-stu-id="d4d56-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="d4d56-114">Por exemplo, suponha que <xref:System.Reflection.MethodInfo> o código use reflexão para retornar um objeto representando um método protegido por uma demanda de link e, em seguida, passa esse objeto **MethodInfo** para algum outro código que usa o objeto para invocar o método original.</span><span class="sxs-lookup"><span data-stu-id="d4d56-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="d4d56-115">Neste caso, a verificação de demanda de link ocorre duas vezes: uma para o código que retorna o objeto **MethodInfo** e outra para o código que o invoca.</span><span class="sxs-lookup"><span data-stu-id="d4d56-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4d56-116">Uma demanda de link realizada em um construtor de classe estática não protege o construtor porque os construtores estáticos são chamados pelo sistema, fora do caminho de execução de código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d4d56-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="d4d56-117">Como resultado, quando uma demanda de link é aplicada a uma classe inteira, ela não pode proteger o acesso a um construtor estático, embora proteja o resto da classe.</span><span class="sxs-lookup"><span data-stu-id="d4d56-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="d4d56-118">O fragmento de código a seguir especifica declarativamente que qualquer código vinculado ao `ReadData` método deve ter a `CustomPermission` permissão.</span><span class="sxs-lookup"><span data-stu-id="d4d56-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="d4d56-119">Essa permissão é uma permissão personalizada hipotética e não existe no Quadro .NET.</span><span class="sxs-lookup"><span data-stu-id="d4d56-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="d4d56-120">A demanda é feita passando uma bandeira **SecurityAction.LinkDemand** para o `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="d4d56-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4d56-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="d4d56-121">See also</span></span>

- [<span data-ttu-id="d4d56-122">Atributos</span><span class="sxs-lookup"><span data-stu-id="d4d56-122">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="d4d56-123">Segurança de acesso a código</span><span class="sxs-lookup"><span data-stu-id="d4d56-123">Code Access Security</span></span>](code-access-security.md)
