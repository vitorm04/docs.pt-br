---
title: Demandas de link
description: Leia sobre as demandas de link, que causam uma verificação de segurança durante a compilação JIT (just-in-time) e examina apenas o assembly de chamada imediata do seu código.
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
ms.openlocfilehash: eaf9ee1bb5cd10c724240bacac014503685a0c8c
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309086"
---
# <a name="link-demands"></a><span data-ttu-id="2e974-103">Demandas de link</span><span class="sxs-lookup"><span data-stu-id="2e974-103">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="2e974-104">Uma demanda de link causa uma verificação de segurança durante a compilação just-in-time e verifica apenas o assembly de chamada imediata do seu código.</span><span class="sxs-lookup"><span data-stu-id="2e974-104">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="2e974-105">A vinculação ocorre quando seu código está associado a uma referência de tipo, incluindo referências de ponteiro de função e chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="2e974-105">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="2e974-106">Se o assembly de chamada não tiver permissão suficiente para vincular ao seu código, o link não será permitido e uma exceção de tempo de execução será lançada quando o código for carregado e executado.</span><span class="sxs-lookup"><span data-stu-id="2e974-106">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="2e974-107">As demandas de link podem ser substituídas em classes que herdam do seu código.</span><span class="sxs-lookup"><span data-stu-id="2e974-107">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="2e974-108">Uma movimentação de pilha completa não é executada com esse tipo de demanda e o código ainda é suscetível a ataques chamariz.</span><span class="sxs-lookup"><span data-stu-id="2e974-108">A full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="2e974-109">Por exemplo, se um método no assembly A for protegido por uma demanda de link, um chamador direto no assembly B será avaliado com base nas permissões do assembly B.  No entanto, a demanda de link não avaliará um método no assembly C se ele chamar indiretamente o método no assembly A usando o método no assembly B. A demanda de link especifica somente as permissões que os chamadores diretos no assembly de chamada imediata devem ter que vincular ao seu código.</span><span class="sxs-lookup"><span data-stu-id="2e974-109">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="2e974-110">Ele não especifica as permissões que todos os chamadores devem ter para executar seu código.</span><span class="sxs-lookup"><span data-stu-id="2e974-110">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="2e974-111">Os <xref:System.Security.CodeAccessPermission.Assert%2A> <xref:System.Security.CodeAccessPermission.Deny%2A> <xref:System.Security.CodeAccessPermission.PermitOnly%2A> modificadores de movimentação de pilha, e não afetam a avaliação de demandas de link.</span><span class="sxs-lookup"><span data-stu-id="2e974-111">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="2e974-112">Como as demandas de link não executam uma movimentação de pilha, os modificadores de movimentação de pilha não têm nenhum efeito nas demandas de link.</span><span class="sxs-lookup"><span data-stu-id="2e974-112">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="2e974-113">Se um método protegido por uma demanda de link for acessado por meio de [reflexão](../reflection-and-codedom/reflection.md), uma demanda de link verificará o chamador imediato do código acessado por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="2e974-113">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="2e974-114">Isso é verdadeiro para a descoberta de método e para invocação de método executada usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="2e974-114">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="2e974-115">Por exemplo, suponha que o código use a reflexão para retornar um <xref:System.Reflection.MethodInfo> objeto que representa um método protegido por uma demanda de link e, em seguida, passe esse objeto **MethodInfo** para algum outro código que usa o objeto para invocar o método original.</span><span class="sxs-lookup"><span data-stu-id="2e974-115">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="2e974-116">Nesse caso, a verificação de demanda de link ocorre duas vezes: uma vez para o código que retorna o objeto **MethodInfo** e uma vez para o código que o invoca.</span><span class="sxs-lookup"><span data-stu-id="2e974-116">In this case, the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e974-117">Uma demanda de link executada em um construtor de classe estática não protege o construtor porque construtores estáticos são chamados pelo sistema, fora do caminho de execução de código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2e974-117">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="2e974-118">Como resultado, quando uma demanda de link é aplicada a uma classe inteira, ela não pode proteger o acesso a um construtor estático, embora proteja o restante da classe.</span><span class="sxs-lookup"><span data-stu-id="2e974-118">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="2e974-119">O fragmento de código a seguir especifica declarativamente que qualquer vinculação de código para o `ReadData` método deve ter a `CustomPermission` permissão.</span><span class="sxs-lookup"><span data-stu-id="2e974-119">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="2e974-120">Essa permissão é uma permissão personalizada hipotética e não existe no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2e974-120">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="2e974-121">A demanda é feita passando um sinalizador **SecurityAction. LinkDemand** para o `CustomPermissionAttribute` .</span><span class="sxs-lookup"><span data-stu-id="2e974-121">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2e974-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e974-122">See also</span></span>

- [<span data-ttu-id="2e974-123">Atributos</span><span class="sxs-lookup"><span data-stu-id="2e974-123">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="2e974-124">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="2e974-124">Code Access Security</span></span>](code-access-security.md)
