---
title: Construtores estáticos – Guia de Programação em C#
description: Um construtor estático em C# inicializa dados estáticos ou executa uma ação feita apenas uma vez antes que a primeira instância seja criada ou membros estáticos sejam referenciados.
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 07b3e54c9ffeb1abacaf5ddd04d2058697e653e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203963"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="18800-103">Construtores estáticos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="18800-103">Static Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="18800-104">Um construtor estático é usado para inicializar quaisquer dados [estáticos](../../language-reference/keywords/static.md) ou para executar uma ação específica que precisa ser executada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="18800-104">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="18800-105">Ele é chamado automaticamente antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.</span><span class="sxs-lookup"><span data-stu-id="18800-105">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a><span data-ttu-id="18800-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="18800-106">Remarks</span></span>

<span data-ttu-id="18800-107">Construtores estáticos têm as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="18800-107">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="18800-108">Um construtor estático não usa modificadores de acesso nem tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="18800-108">A static constructor does not take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="18800-109">Uma classe ou struct só pode ter um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="18800-109">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="18800-110">Os construtores estáticos não podem ser herdados ou sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="18800-110">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="18800-111">Um construtor estático não pode ser chamado diretamente e destina-se apenas a ser chamado pela Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="18800-111">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="18800-112">Ele é invocado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="18800-112">It is invoked automatically.</span></span>

- <span data-ttu-id="18800-113">O usuário não tem controle sobre quando o construtor estático é executado no programa.</span><span class="sxs-lookup"><span data-stu-id="18800-113">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="18800-114">Um construtor estático é chamado automaticamente para inicializar a [classe](../../language-reference/keywords/class.md) antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.</span><span class="sxs-lookup"><span data-stu-id="18800-114">A static constructor is called automatically to initialize the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="18800-115">Um construtor estático será executado antes de um construtor de instância.</span><span class="sxs-lookup"><span data-stu-id="18800-115">A static constructor will run before an instance constructor.</span></span> <span data-ttu-id="18800-116">O construtor estático de um tipo é chamado quando um método estático atribuído a um evento ou um delegado é invocado e não quando é atribuído.</span><span class="sxs-lookup"><span data-stu-id="18800-116">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="18800-117">Se os inicializadores de variável de campo estático estiverem presentes na classe do construtor estático, eles serão executados na ordem textual na qual eles aparecem na declaração de classe imediatamente antes da execução do construtor estático.</span><span class="sxs-lookup"><span data-stu-id="18800-117">If static field variable initializers are present in the class of the static constructor, they will be executed in the textual order in which they appear in the class declaration immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="18800-118">Se você não fornecer um construtor estático para inicializar campos estáticos, todos os campos estáticos serão inicializados para seu valor padrão, conforme listado em [valores padrão de tipos C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="18800-118">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="18800-119">Se um construtor estático gera uma exceção, o runtime não o invocará uma segunda vez e o tipo permanecerá não inicializado durante o tempo de vida do domínio do aplicativo no qual o programa está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="18800-119">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span> <span data-ttu-id="18800-120">Normalmente, uma exceção <xref:System.TypeInitializationException> é lançada quando um construtor estático não consegue instanciar um tipo ou uma exceção sem tratamento que ocorre em um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="18800-120">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="18800-121">Para construtores estáticos implícitos que não são definidos explicitamente no código-fonte, a solução de problemas pode exigir inspeção do código de linguagem intermediária (IL).</span><span class="sxs-lookup"><span data-stu-id="18800-121">For implicit static constructors that are not explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="18800-122">A presença de um construtor estático impede a adição do atributo do tipo <xref:System.Reflection.TypeAttributes.BeforeFieldInit>.</span><span class="sxs-lookup"><span data-stu-id="18800-122">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="18800-123">Isso limita a otimização do runtime.</span><span class="sxs-lookup"><span data-stu-id="18800-123">This limits runtime optimization.</span></span>

- <span data-ttu-id="18800-124">Um campo declarado como `static readonly` só pode ser atribuído como parte de sua declaração ou em um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="18800-124">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="18800-125">Quando um construtor estático explícito não for necessário, inicialize os campos estáticos na declaração, em vez de usar um construtor estático para melhorar a otimização do runtime.</span><span class="sxs-lookup"><span data-stu-id="18800-125">When an explicit static constructor is not required, initialize static fields at declaration, rather than through a static constructor for better runtime optimization.</span></span>

> [!Note]
> <span data-ttu-id="18800-126">Embora não seja diretamente acessível, a presença de um construtor estático explícito deve ser documentada para auxiliar na solução de problemas de exceções de inicialização.</span><span class="sxs-lookup"><span data-stu-id="18800-126">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="18800-127">Uso</span><span class="sxs-lookup"><span data-stu-id="18800-127">Usage</span></span>

- <span data-ttu-id="18800-128">Um uso típico de construtores estáticos é quando a classe está usando um arquivo de log e o construtor é usado para gravar entradas nesse arquivo.</span><span class="sxs-lookup"><span data-stu-id="18800-128">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="18800-129">Construtores estáticos também são úteis ao criar classes wrapper para código não gerenciado quando o construtor pode chamar o método `LoadLibrary`.</span><span class="sxs-lookup"><span data-stu-id="18800-129">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="18800-130">Construtores estáticos também são um local conveniente para impor verificações em tempo de execução no parâmetro de tipo que não pode ser verificado no tempo de compilação por meio de restrições (restrições de parâmetro de tipo).</span><span class="sxs-lookup"><span data-stu-id="18800-130">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via constraints (Type parameter constraints).</span></span>

## <a name="example"></a><span data-ttu-id="18800-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18800-131">Example</span></span>

 <span data-ttu-id="18800-132">Nesse exemplo, a classe `Bus` tem um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="18800-132">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="18800-133">Quando a primeira instância do `Bus` for criada (`bus1`), o construtor estático será invocado para inicializar a classe.</span><span class="sxs-lookup"><span data-stu-id="18800-133">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="18800-134">O exemplo de saída verifica se o construtor estático é executado somente uma vez, mesmo se duas instâncias de `Bus` forem criadas e se é executado antes que o construtor da instância seja executado.</span><span class="sxs-lookup"><span data-stu-id="18800-134">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="18800-135">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="18800-135">C# language specification</span></span>

<span data-ttu-id="18800-136">Para saber mais, confira a seção [Construtores estáticos](~/_csharplang/spec/classes.md#static-constructors) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="18800-136">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="18800-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="18800-137">See also</span></span>

- [<span data-ttu-id="18800-138">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="18800-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="18800-139">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="18800-139">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="18800-140">Construtores</span><span class="sxs-lookup"><span data-stu-id="18800-140">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="18800-141">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="18800-141">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="18800-142">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="18800-142">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="18800-143">Diretrizes de design de construtor</span><span class="sxs-lookup"><span data-stu-id="18800-143">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="18800-144">Aviso de segurança-CA2121: construtores estáticos devem ser privados</span><span class="sxs-lookup"><span data-stu-id="18800-144">Security Warning - CA2121: Static constructors should be private</span></span>](/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
