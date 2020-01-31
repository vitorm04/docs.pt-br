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
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741743"
---
# <a name="constructor-design"></a><span data-ttu-id="7ab3e-102">Design do construtor</span><span class="sxs-lookup"><span data-stu-id="7ab3e-102">Constructor Design</span></span>

<span data-ttu-id="7ab3e-103">Há dois tipos de construtores: construtores de tipo e construtores de instância.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="7ab3e-104">Construtores de tipo são estáticos e são executados pelo CLR antes de o tipo ser usado.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="7ab3e-105">Os construtores de instância são executados quando uma instância de um tipo é criada.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="7ab3e-106">Construtores de tipo não podem usar parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="7ab3e-107">Construtores de instância podem.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-107">Instance constructors can.</span></span> <span data-ttu-id="7ab3e-108">Os construtores de instância que não usam parâmetros geralmente são chamados de construtores sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="7ab3e-109">Os construtores são a maneira mais natural de criar instâncias de um tipo.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="7ab3e-110">A maioria dos desenvolvedores pesquisará e tentará usar um Construtor antes que eles considerem maneiras alternativas de criar instâncias (como métodos de fábrica).</span><span class="sxs-lookup"><span data-stu-id="7ab3e-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="7ab3e-111">✔️ Considere fornecer construtores simples, ideais, padrão.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="7ab3e-112">Um Construtor simples tem um número muito pequeno de parâmetros e todos os parâmetros são primitivos ou enums.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="7ab3e-113">Esses construtores simples aumentam a usabilidade da estrutura.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="7ab3e-114">✔️ Considere o uso de um método de fábrica estático em vez de um construtor se a semântica da operação desejada não for mapeada diretamente para a construção de uma nova instância ou se as diretrizes de design de Construtor a seguir não se sentirem naturais.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="7ab3e-115">✔️ Use parâmetros de construtor como atalhos para definir propriedades principais.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="7ab3e-116">Não deve haver nenhuma diferença na semântica entre o uso do construtor vazio seguido por alguns conjuntos de propriedades e o uso de um construtor com vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="7ab3e-117">✔️ usar o mesmo nome para parâmetros de construtor e uma propriedade se os parâmetros do Construtor forem usados para simplesmente definir a propriedade.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="7ab3e-118">A única diferença entre esses parâmetros e as propriedades deve estar entre maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="7ab3e-119">✔️ EXECUTAR o mínimo de trabalho no construtor.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="7ab3e-120">Os construtores não devem fazer muito trabalho além de capturar os parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="7ab3e-121">O custo de qualquer outro processamento deve ser atrasado até que seja necessário.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="7ab3e-122">✔️ gerar exceções de construtores de instância, se apropriado.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="7ab3e-123">✔️ declarar explicitamente o construtor público sem parâmetros em classes, se esse construtor for necessário.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="7ab3e-124">Se você não declarar explicitamente nenhum construtor em um tipo, muitas linguagens (como C#) adicionarão automaticamente um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="7ab3e-125">(Classes abstratas obtêm um construtor protegido.)</span><span class="sxs-lookup"><span data-stu-id="7ab3e-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="7ab3e-126">Adicionar um construtor com parâmetros a uma classe impede que o compilador adicione o construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="7ab3e-127">Isso geralmente causa alterações de interrupção acidentais.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="7ab3e-128">❌ evitar definir explicitamente construtores sem parâmetros em structs.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="7ab3e-129">Isso torna a criação de matriz mais rápida, porque se o construtor sem parâmetros não estiver definido, ele não precisará ser executado em todos os slots na matriz.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="7ab3e-130">Observe que muitos compiladores, incluindo C#, não permitem que structs tenham construtores sem parâmetros por esse motivo.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="7ab3e-131">❌ evitar chamar Membros virtuais em um objeto dentro de seu construtor.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="7ab3e-132">Chamar um membro virtual fará com que a substituição mais derivada seja chamada, mesmo que o construtor do tipo mais derivado ainda não tenha sido totalmente executado.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="7ab3e-133">Diretrizes de construtor de tipo</span><span class="sxs-lookup"><span data-stu-id="7ab3e-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="7ab3e-134">✔️ tornar os construtores estáticos privados.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="7ab3e-135">Um construtor estático, também chamado de construtor de classe, é usado para inicializar um tipo.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="7ab3e-136">O CLR chama o construtor estático antes que a primeira instância do tipo seja criada ou quaisquer membros estáticos nesse tipo sejam chamados.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="7ab3e-137">O usuário não tem controle sobre quando o construtor estático é chamado.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="7ab3e-138">Se um construtor estático não for privado, ele poderá ser chamado por um código diferente do CLR.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="7ab3e-139">Dependendo das operações executadas no construtor, isso pode causar um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="7ab3e-140">O C# compilador força os construtores estáticos a serem privados.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="7ab3e-141">❌ não lançam exceções de construtores estáticos.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="7ab3e-142">Se uma exceção for gerada de um construtor de tipo, o tipo não poderá ser usado no domínio do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="7ab3e-143">✔️ Considere a inicialização de campos estáticos embutidos em vez de usar construtores estáticos explicitamente, pois o tempo de execução é capaz de otimizar o desempenho dos tipos que não têm um construtor estático explicitamente definido.</span><span class="sxs-lookup"><span data-stu-id="7ab3e-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="7ab3e-144">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="7ab3e-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="7ab3e-145">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="7ab3e-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7ab3e-146">Veja também</span><span class="sxs-lookup"><span data-stu-id="7ab3e-146">See also</span></span>

- [<span data-ttu-id="7ab3e-147">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="7ab3e-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="7ab3e-148">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="7ab3e-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
