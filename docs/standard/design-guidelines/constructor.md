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
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: KrzysztofCwalina
ms.openlocfilehash: 68192e3b75a120c73b82c34005d4dee650540bf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722160"
---
# <a name="constructor-design"></a><span data-ttu-id="c92f9-102">Design do construtor</span><span class="sxs-lookup"><span data-stu-id="c92f9-102">Constructor Design</span></span>
<span data-ttu-id="c92f9-103">Há dois tipos dos construtores: construtores e construtores de instância de tipo.</span><span class="sxs-lookup"><span data-stu-id="c92f9-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="c92f9-104">Construtores de tipo são estáticos e são executados pelo CLR, antes do tipo é usado.</span><span class="sxs-lookup"><span data-stu-id="c92f9-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="c92f9-105">Construtores de instância executados quando uma instância de um tipo é criada.</span><span class="sxs-lookup"><span data-stu-id="c92f9-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="c92f9-106">Construtores de tipo não podem receber quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c92f9-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="c92f9-107">Construtores de instância podem.</span><span class="sxs-lookup"><span data-stu-id="c92f9-107">Instance constructors can.</span></span> <span data-ttu-id="c92f9-108">Construtores de instância que não usam todos os parâmetros são chamados de construtores padrão.</span><span class="sxs-lookup"><span data-stu-id="c92f9-108">Instance constructors that don’t take any parameters are often called default constructors.</span></span>  
  
 <span data-ttu-id="c92f9-109">Construtores são a maneira mais natural para criar instâncias de um tipo.</span><span class="sxs-lookup"><span data-stu-id="c92f9-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="c92f9-110">A maioria dos desenvolvedores pesquisará e tentar usar um construtor antes que eles considerarem maneiras alternativas de criação de instâncias (como métodos de fábrica).</span><span class="sxs-lookup"><span data-stu-id="c92f9-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="c92f9-111">**✓ CONSIDER** fornecendo simples, idealmente padrão, construtores.</span><span class="sxs-lookup"><span data-stu-id="c92f9-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="c92f9-112">Um construtor simple tem um número muito pequeno de parâmetros e todos os parâmetros são primitivos ou enumerações.</span><span class="sxs-lookup"><span data-stu-id="c92f9-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="c92f9-113">Esses construtores simples aumentam a usabilidade do framework.</span><span class="sxs-lookup"><span data-stu-id="c92f9-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="c92f9-114">**✓ CONSIDER** usando um método de fábrica estáticos em vez de um construtor, se a semântica da operação desejada não é mapeados diretamente para a construção de uma nova instância, ou se seguir as diretrizes de design do construtor parece não natural.</span><span class="sxs-lookup"><span data-stu-id="c92f9-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="c92f9-115">**✓ DO** usar os parâmetros do construtor como atalhos para definir as propriedades principais.</span><span class="sxs-lookup"><span data-stu-id="c92f9-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="c92f9-116">Não deve haver nenhuma diferença semântica entre usando o construtor vazio seguido por alguns conjuntos de propriedade e um construtor com vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="c92f9-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="c92f9-117">**✓ DO** usar o mesmo nome para os parâmetros do construtor e uma propriedade se os parâmetros do construtor são usados simplesmente definir a propriedade.</span><span class="sxs-lookup"><span data-stu-id="c92f9-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="c92f9-118">A única diferença entre esses parâmetros e as propriedades deve ser maiusculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="c92f9-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="c92f9-119">**✓ DO** mínimo de trabalho no construtor.</span><span class="sxs-lookup"><span data-stu-id="c92f9-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="c92f9-120">Construtores não devem fazer muito trabalho que não seja captura os parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="c92f9-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="c92f9-121">O custo de qualquer outro processamento deve ser atrasado até que o necessário.</span><span class="sxs-lookup"><span data-stu-id="c92f9-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="c92f9-122">**✓ DO** lançar exceções a partir de construtores de instância, se apropriado.</span><span class="sxs-lookup"><span data-stu-id="c92f9-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="c92f9-123">**✓ DO** declarar explicitamente o construtor padrão público em classes, se tal construtor for necessária.</span><span class="sxs-lookup"><span data-stu-id="c92f9-123">**✓ DO** explicitly declare the public default constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="c92f9-124">Se você não declarar construtores explicitamente em um tipo, muitas linguagens (como c#) adiciona automaticamente um construtor padrão público.</span><span class="sxs-lookup"><span data-stu-id="c92f9-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public default constructor.</span></span> <span data-ttu-id="c92f9-125">(As classes abstratas obterá um construtor protegido.)</span><span class="sxs-lookup"><span data-stu-id="c92f9-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="c92f9-126">Adicionando um construtor parametrizado a uma classe impede que o compilador adicione o construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="c92f9-126">Adding a parameterized constructor to a class prevents the compiler from adding the default constructor.</span></span> <span data-ttu-id="c92f9-127">Com frequência isso causa alterações significativas acidental.</span><span class="sxs-lookup"><span data-stu-id="c92f9-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="c92f9-128">**X AVOID** explicitamente definir construtores padrão em estruturas.</span><span class="sxs-lookup"><span data-stu-id="c92f9-128">**X AVOID** explicitly defining default constructors on structs.</span></span>  
  
 <span data-ttu-id="c92f9-129">Isso torna a criação de matriz rápida, porque se o construtor padrão não for definido, ele não tem que ser executado em cada slot na matriz.</span><span class="sxs-lookup"><span data-stu-id="c92f9-129">This makes array creation faster, because if the default constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="c92f9-130">Observe que muitos compiladores, incluindo c#, não permitem structs ter construtores sem parâmetros por esse motivo.</span><span class="sxs-lookup"><span data-stu-id="c92f9-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="c92f9-131">**X AVOID** chamando membros virtuais em um objeto dentro de seu construtor.</span><span class="sxs-lookup"><span data-stu-id="c92f9-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="c92f9-132">Chamar um membro virtual fará com que a substituição mais derivada a ser chamado, mesmo se o construtor do tipo mais derivado não foi totalmente executado ainda.</span><span class="sxs-lookup"><span data-stu-id="c92f9-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="c92f9-133">Diretrizes do construtor de tipo</span><span class="sxs-lookup"><span data-stu-id="c92f9-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="c92f9-134">**✓ DO** tornar construtores estáticos em particular.</span><span class="sxs-lookup"><span data-stu-id="c92f9-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="c92f9-135">Um construtor estático, também chamado construtor de classe, é usado para inicializar um tipo.</span><span class="sxs-lookup"><span data-stu-id="c92f9-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="c92f9-136">O CLR chama o construtor estático antes da primeira instância do tipo é criada ou quaisquer membros estáticos no tipo são chamados.</span><span class="sxs-lookup"><span data-stu-id="c92f9-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="c92f9-137">O usuário não tem controle sobre quando o construtor estático é chamado.</span><span class="sxs-lookup"><span data-stu-id="c92f9-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="c92f9-138">Se um construtor estático não for privado, ele pode ser chamado pelo código que não seja o CLR.</span><span class="sxs-lookup"><span data-stu-id="c92f9-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="c92f9-139">Dependendo das operações realizadas no construtor, isso pode causar um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="c92f9-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="c92f9-140">O compilador c# força construtores estáticos a ser privadas.</span><span class="sxs-lookup"><span data-stu-id="c92f9-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="c92f9-141">**X DO NOT** lançar exceções a partir de construtores estáticos.</span><span class="sxs-lookup"><span data-stu-id="c92f9-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="c92f9-142">Se uma exceção for gerada de um construtor de tipo, o tipo não é utilizável no domínio do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="c92f9-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="c92f9-143">**✓ CONSIDER** inicializar campos estáticos embutido em vez de usar explicitamente construtores estáticos, porque o tempo de execução é capaz de otimizar o desempenho de tipos que não tem um construtor estático definido explicitamente.</span><span class="sxs-lookup"><span data-stu-id="c92f9-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="c92f9-144">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="c92f9-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c92f9-145">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c92f9-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92f9-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c92f9-146">See also</span></span>

- [<span data-ttu-id="c92f9-147">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="c92f9-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="c92f9-148">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="c92f9-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
