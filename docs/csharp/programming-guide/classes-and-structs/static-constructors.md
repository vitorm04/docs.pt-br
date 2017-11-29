---
title: "Construtores estáticos (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee5448095cf06c2473c94bae542c02557918271a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="60cde-102">Construtores estáticos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="60cde-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="60cde-103">Um construtor estático é usado para inicializar quaisquer dados [estáticos](../../../csharp/language-reference/keywords/static.md) ou para executar uma ação específica que precisa ser executada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="60cde-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="60cde-104">Ele é chamado automaticamente antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.</span><span class="sxs-lookup"><span data-stu-id="60cde-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 <span data-ttu-id="60cde-105">Construtores estáticos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="60cde-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="60cde-106">Um construtor estático não usa modificadores de acesso nem tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="60cde-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="60cde-107">Um construtor estático é chamado automaticamente para inicializar a [classe](../../../csharp/language-reference/keywords/class.md) antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.</span><span class="sxs-lookup"><span data-stu-id="60cde-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="60cde-108">Um construtor estático não pode ser chamado diretamente.</span><span class="sxs-lookup"><span data-stu-id="60cde-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="60cde-109">O usuário não tem controle sobre quando o construtor estático é executado no programa.</span><span class="sxs-lookup"><span data-stu-id="60cde-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="60cde-110">Um uso típico de construtores estáticos é quando a classe está usando um arquivo de log e o construtor é usado para gravar entradas nesse arquivo.</span><span class="sxs-lookup"><span data-stu-id="60cde-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="60cde-111">Construtores estáticos também são úteis ao criar classes wrapper para código não gerenciado quando o construtor pode chamar o método `LoadLibrary`.</span><span class="sxs-lookup"><span data-stu-id="60cde-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="60cde-112">Se um construtor estático gera uma exceção, o tempo de execução não o invocará uma segunda vez e o tipo permanecerá não inicializado durante o tempo de vida do domínio do aplicativo no qual o programa está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="60cde-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60cde-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60cde-113">Example</span></span>  
 <span data-ttu-id="60cde-114">Nesse exemplo, a classe `Bus` tem um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="60cde-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="60cde-115">Quando a primeira instância do `Bus` for criada (`bus1`), o construtor estático será invocado para inicializar a classe.</span><span class="sxs-lookup"><span data-stu-id="60cde-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="60cde-116">O exemplo de saída verifica se o construtor estático é executado somente uma vez, mesmo se duas instâncias de `Bus` forem criadas e se é executado antes que o construtor da instância seja executado.</span><span class="sxs-lookup"><span data-stu-id="60cde-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="60cde-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60cde-117">See Also</span></span>  
 [<span data-ttu-id="60cde-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="60cde-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="60cde-119">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="60cde-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="60cde-120">Construtores</span><span class="sxs-lookup"><span data-stu-id="60cde-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="60cde-121">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="60cde-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="60cde-122">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="60cde-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
