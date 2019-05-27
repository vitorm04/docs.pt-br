---
title: Construtores estáticos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 110d83caad0c588fa899a4129897784e9c74aab8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881909"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="539c3-102">Construtores estáticos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="539c3-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="539c3-103">Um construtor estático é usado para inicializar quaisquer dados [estáticos](../../../csharp/language-reference/keywords/static.md) ou para executar uma ação específica que precisa ser executada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="539c3-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="539c3-104">Ele é chamado automaticamente antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.</span><span class="sxs-lookup"><span data-stu-id="539c3-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
  
 <span data-ttu-id="539c3-105">Construtores estáticos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="539c3-105">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="539c3-106">Um construtor estático não usa modificadores de acesso nem tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="539c3-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
- <span data-ttu-id="539c3-107">Um construtor estático é chamado automaticamente para inicializar a [classe](../../../csharp/language-reference/keywords/class.md) antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.</span><span class="sxs-lookup"><span data-stu-id="539c3-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="539c3-108">Observe que um construtor de tipo estático é chamado quando um método estático atribuído a um evento ou um delegado é invocado, e não quando ele é atribuído.</span><span class="sxs-lookup"><span data-stu-id="539c3-108">Note that a type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span>
  
- <span data-ttu-id="539c3-109">Um construtor estático não pode ser chamado diretamente.</span><span class="sxs-lookup"><span data-stu-id="539c3-109">A static constructor cannot be called directly.</span></span>  
  
- <span data-ttu-id="539c3-110">O usuário não tem controle sobre quando o construtor estático é executado no programa.</span><span class="sxs-lookup"><span data-stu-id="539c3-110">The user has no control on when the static constructor is executed in the program.</span></span>  
  
- <span data-ttu-id="539c3-111">Um uso típico de construtores estáticos é quando a classe está usando um arquivo de log e o construtor é usado para gravar entradas nesse arquivo.</span><span class="sxs-lookup"><span data-stu-id="539c3-111">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
- <span data-ttu-id="539c3-112">Construtores estáticos também são úteis ao criar classes wrapper para código não gerenciado quando o construtor pode chamar o método `LoadLibrary`.</span><span class="sxs-lookup"><span data-stu-id="539c3-112">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
- <span data-ttu-id="539c3-113">Se um construtor estático gera uma exceção, o tempo de execução não o invocará uma segunda vez e o tipo permanecerá não inicializado durante o tempo de vida do domínio do aplicativo no qual o programa está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="539c3-113">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="539c3-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="539c3-114">Example</span></span>  
 <span data-ttu-id="539c3-115">Nesse exemplo, a classe `Bus` tem um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="539c3-115">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="539c3-116">Quando a primeira instância do `Bus` for criada (`bus1`), o construtor estático será invocado para inicializar a classe.</span><span class="sxs-lookup"><span data-stu-id="539c3-116">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="539c3-117">O exemplo de saída verifica se o construtor estático é executado somente uma vez, mesmo se duas instâncias de `Bus` forem criadas e se é executado antes que o construtor da instância seja executado.</span><span class="sxs-lookup"><span data-stu-id="539c3-117">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]  
  
## <a name="see-also"></a><span data-ttu-id="539c3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="539c3-118">See also</span></span>

- [<span data-ttu-id="539c3-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="539c3-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="539c3-120">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="539c3-120">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="539c3-121">Construtores</span><span class="sxs-lookup"><span data-stu-id="539c3-121">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="539c3-122">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="539c3-122">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="539c3-123">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="539c3-123">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
