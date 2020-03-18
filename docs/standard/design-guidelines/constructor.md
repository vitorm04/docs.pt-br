---
title: Design do construtor
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400599"
---
# <a name="constructor-design"></a><span data-ttu-id="2fcee-102">Design do construtor</span><span class="sxs-lookup"><span data-stu-id="2fcee-102">Constructor Design</span></span>

<span data-ttu-id="2fcee-103">Existem dois tipos de construtores: construtores de tipos e construtores de instâncias.</span><span class="sxs-lookup"><span data-stu-id="2fcee-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="2fcee-104">Os construtores de tipo são estáticos e são executados pela CLR antes do tipo ser usado.</span><span class="sxs-lookup"><span data-stu-id="2fcee-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="2fcee-105">Construtores de instâncias são executados quando uma instância de um tipo é criada.</span><span class="sxs-lookup"><span data-stu-id="2fcee-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="2fcee-106">Os construtores de tipo não podem tomar parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2fcee-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="2fcee-107">Construtores de instâncias podem.</span><span class="sxs-lookup"><span data-stu-id="2fcee-107">Instance constructors can.</span></span> <span data-ttu-id="2fcee-108">Construtores de instâncias que não tomam parâmetros são frequentemente chamados de construtores sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2fcee-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="2fcee-109">Os construtores são a maneira mais natural de criar instâncias de um tipo.</span><span class="sxs-lookup"><span data-stu-id="2fcee-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="2fcee-110">A maioria dos desenvolvedores procurará e tentará usar um construtor antes de considerar formas alternativas de criar instâncias (como métodos de fábrica).</span><span class="sxs-lookup"><span data-stu-id="2fcee-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="2fcee-111">✔️ CONSIDEREm fornecer construtores simples, idealmente padrão.</span><span class="sxs-lookup"><span data-stu-id="2fcee-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="2fcee-112">Um simples construtor tem um número muito pequeno de parâmetros, e todos os parâmetros são primitivos ou enums.</span><span class="sxs-lookup"><span data-stu-id="2fcee-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="2fcee-113">Tais construtores simples aumentam a usabilidade do quadro.</span><span class="sxs-lookup"><span data-stu-id="2fcee-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="2fcee-114">✔️ considerem usar um método de fábrica estática em vez de um construtor se a semântica da operação desejada não mapear diretamente para a construção de uma nova instância, ou se seguir as diretrizes de projeto do construtor não parecer natural.</span><span class="sxs-lookup"><span data-stu-id="2fcee-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="2fcee-115">✔️ DO use parâmetros de construção como atalhos para definir as propriedades principais.</span><span class="sxs-lookup"><span data-stu-id="2fcee-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="2fcee-116">Não deve haver diferença na semântica entre usar o construtor vazio seguido de alguns conjuntos de propriedades e usar um construtor com múltiplos argumentos.</span><span class="sxs-lookup"><span data-stu-id="2fcee-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="2fcee-117">✔️ DO use o mesmo nome para parâmetros de construção e uma propriedade se os parâmetros do construtor forem usados para simplesmente definir a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2fcee-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="2fcee-118">A única diferença entre tais parâmetros e as propriedades deve ser o invólucro.</span><span class="sxs-lookup"><span data-stu-id="2fcee-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="2fcee-119">✔️ fazer o mínimo de trabalho na construtora.</span><span class="sxs-lookup"><span data-stu-id="2fcee-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="2fcee-120">Os construtores não devem fazer muito trabalho além de capturar os parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="2fcee-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="2fcee-121">O custo de qualquer outro processamento deve ser adiado até que seja necessário.</span><span class="sxs-lookup"><span data-stu-id="2fcee-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="2fcee-122">✔️ DO lançar exceções de construtores de instâncias, se apropriado.</span><span class="sxs-lookup"><span data-stu-id="2fcee-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="2fcee-123">✔️ DO declarar explicitamente o construtor público sem parâmetros nas classes, se tal construtor for necessário.</span><span class="sxs-lookup"><span data-stu-id="2fcee-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="2fcee-124">Se você não declarar explicitamente nenhum construtor em um tipo, muitas línguas (como C#) adicionarão automaticamente um construtor sem parâmetros públicos.</span><span class="sxs-lookup"><span data-stu-id="2fcee-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="2fcee-125">(Classes abstratas recebem um construtor protegido.)</span><span class="sxs-lookup"><span data-stu-id="2fcee-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="2fcee-126">Adicionar um construtor parametrizado a uma classe impede que o compilador adicione o construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2fcee-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="2fcee-127">Isso muitas vezes causa mudanças acidentais.</span><span class="sxs-lookup"><span data-stu-id="2fcee-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="2fcee-128">❌EVITE definir explicitamente construtores sem parâmetros em estruturas.</span><span class="sxs-lookup"><span data-stu-id="2fcee-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="2fcee-129">Isso torna a criação de array mais rápida, porque se o construtor sem parâmetros não for definido, ele não precisa ser executado em todos os slots da matriz.</span><span class="sxs-lookup"><span data-stu-id="2fcee-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="2fcee-130">Note que muitos compiladores, incluindo C#, não permitem que estruturas tenham construtores sem parâmetros por essa razão.</span><span class="sxs-lookup"><span data-stu-id="2fcee-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="2fcee-131">❌EVITE chamar membros virtuais em um objeto dentro de seu construtor.</span><span class="sxs-lookup"><span data-stu-id="2fcee-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="2fcee-132">Chamar um membro virtual fará com que a substituição mais derivada seja chamada, mesmo que o construtor do tipo mais derivado ainda não tenha sido totalmente executado.</span><span class="sxs-lookup"><span data-stu-id="2fcee-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="2fcee-133">Diretrizes de Construção de Tipo</span><span class="sxs-lookup"><span data-stu-id="2fcee-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="2fcee-134">✔️ FAZEM construções estáticas privadas.</span><span class="sxs-lookup"><span data-stu-id="2fcee-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="2fcee-135">Um construtor estático, também chamado de construtor de classe, é usado para inicializar um tipo.</span><span class="sxs-lookup"><span data-stu-id="2fcee-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="2fcee-136">O CLR chama o construtor estático antes que a primeira instância do tipo seja criada ou quaisquer membros estáticos desse tipo sejam chamados.</span><span class="sxs-lookup"><span data-stu-id="2fcee-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="2fcee-137">O usuário não tem controle sobre quando o construtor estático é chamado.</span><span class="sxs-lookup"><span data-stu-id="2fcee-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="2fcee-138">Se um construtor estático não for privado, ele pode ser chamado por código diferente do CLR.</span><span class="sxs-lookup"><span data-stu-id="2fcee-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="2fcee-139">Dependendo das operações realizadas na construtora, isso pode causar comportamentos inesperados.</span><span class="sxs-lookup"><span data-stu-id="2fcee-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="2fcee-140">O compilador C# força os construtores estáticos a serem privados.</span><span class="sxs-lookup"><span data-stu-id="2fcee-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="2fcee-141">❌NÃO jogue exceções de construtores estáticos.</span><span class="sxs-lookup"><span data-stu-id="2fcee-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="2fcee-142">Se uma exceção for lançada de um construtor de tipo, o tipo não poderá ser utilizável no domínio atual do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2fcee-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="2fcee-143">✔️ CONSIDEREMinicializar campos estáticos em linha em vez de usar explicitamente construtores estáticos, porque o tempo de execução é capaz de otimizar o desempenho de tipos que não possuem um construtor estático explicitamente definido.</span><span class="sxs-lookup"><span data-stu-id="2fcee-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="2fcee-144">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="2fcee-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="2fcee-145">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2fcee-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2fcee-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="2fcee-146">See also</span></span>

- [<span data-ttu-id="2fcee-147">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="2fcee-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="2fcee-148">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="2fcee-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
