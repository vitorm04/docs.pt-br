---
title: Novidades no C# 7.2
description: "Uma visão geral dos novos recursos no C# 7.2."
keywords: Design de linguagem do C#, 7.2, Visual Studio 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: cc861f186bea681bb32a2f8041a7155026679987
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2017
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="4f05c-104">Novidades no C# 7.2</span><span class="sxs-lookup"><span data-stu-id="4f05c-104">What's new in C# 7.2</span></span>

<span data-ttu-id="4f05c-105">O C# 7.2 é outra versão de ponto que adiciona vários recursos úteis.</span><span class="sxs-lookup"><span data-stu-id="4f05c-105">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="4f05c-106">Um tema desta versão é o trabalho com maior eficiência com tipos de valor, evitando cópias ou alocações desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="4f05c-106">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="4f05c-107">Os recursos restantes são pequenos e agradáveis.</span><span class="sxs-lookup"><span data-stu-id="4f05c-107">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="4f05c-108">O C# 7.2 usa o elemento de configuração de [seleção de versão de linguagem](csharp-7-1.md#language-version-selection) para selecionar a versão de linguagem do compilador.</span><span class="sxs-lookup"><span data-stu-id="4f05c-108">C# 7.2 uses the [language version selection](csharp-7-1.md#language-version-selection) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="4f05c-109">Os novos recursos de linguagem nesta versão são:</span><span class="sxs-lookup"><span data-stu-id="4f05c-109">The new language features in this release are:</span></span>

* [<span data-ttu-id="4f05c-110">Semântica de referência com tipos de valor</span><span class="sxs-lookup"><span data-stu-id="4f05c-110">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="4f05c-111">Uma combinação de aprimoramentos de sintaxe que permitem trabalhar com tipos de valor usando a semântica de referência.</span><span class="sxs-lookup"><span data-stu-id="4f05c-111">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="4f05c-112">Argumentos nomeados que não estejam à direita</span><span class="sxs-lookup"><span data-stu-id="4f05c-112">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="4f05c-113">Os argumentos nomeados podem ser seguidos por argumentos posicionais.</span><span class="sxs-lookup"><span data-stu-id="4f05c-113">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="4f05c-114">Sublinhados à esquerda em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="4f05c-114">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="4f05c-115">Agora os literais numéricos podem ter sublinhados à esquerda, antes dos dígitos impressos.</span><span class="sxs-lookup"><span data-stu-id="4f05c-115">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="4f05c-116">Modificador de acesso `private protected`</span><span class="sxs-lookup"><span data-stu-id="4f05c-116">`private protected` access modifier</span></span>](#private-protected)
  - <span data-ttu-id="4f05c-117">O modificador de acesso `private protected` permite o acesso a classes derivadas no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="4f05c-117">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="4f05c-118">Semântica de referência com tipos de valores</span><span class="sxs-lookup"><span data-stu-id="4f05c-118">Reference semantics with value types</span></span>

<span data-ttu-id="4f05c-119">Os recursos de linguagem introduzidos na 7.2 permitem trabalhar com tipos de valor ao usar semântica de referência.</span><span class="sxs-lookup"><span data-stu-id="4f05c-119">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="4f05c-120">Eles são projetados para melhorar o desempenho, minimizando a cópia de tipos de valor sem incorrer nas alocações de memória associadas ao uso de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="4f05c-120">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="4f05c-121">Os recursos incluem:</span><span class="sxs-lookup"><span data-stu-id="4f05c-121">The features include:</span></span>

 - <span data-ttu-id="4f05c-122">O modificador `in` em parâmetros, para especificar que um argumento é passado por referência, mas não modificado pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="4f05c-122">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="4f05c-123">O modificador `ref readonly` nos retornos de método, para indicar que um método retorna seu valor por referência, mas não permite gravações nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="4f05c-123">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="4f05c-124">A declaração `readonly struct`, para indicar que uma struct é imutável e deve ser passado como um parâmetro `in` para seus métodos de membro.</span><span class="sxs-lookup"><span data-stu-id="4f05c-124">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="4f05c-125">A declaração `ref struct`, para indicar que um tipo de struct acessa a memória gerenciada diretamente e deve sempre ser alocado por pilha.</span><span class="sxs-lookup"><span data-stu-id="4f05c-125">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="4f05c-126">Você pode ler mais sobre todas essas alterações em [Uso de tipos de valor com a semântica de referência](../reference-semantics-with-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="4f05c-126">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="4f05c-127">Argumentos nomeados que não estejam à direita</span><span class="sxs-lookup"><span data-stu-id="4f05c-127">Non-trailing named arguments</span></span>

<span data-ttu-id="4f05c-128">Agora as chamadas de método podem usar argumentos nomeados que precedem argumentos posicionais quando esses argumentos nomeados estão nas posições corretas.</span><span class="sxs-lookup"><span data-stu-id="4f05c-128">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="4f05c-129">Para obter mais informações, consulte [Argumentos nomeados e opcionais](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="4f05c-129">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="4f05c-130">Sublinhados à esquerda em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="4f05c-130">Leading underscores in numeric literals</span></span>

<span data-ttu-id="4f05c-131">A implementação de suporte para separadores de dígitos no C# 7.0 não permite que o `_` esteja no primeiro caractere do valor literal.</span><span class="sxs-lookup"><span data-stu-id="4f05c-131">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="4f05c-132">Agora os literais numéricos binários e hexadecimais podem começar com um `_`.</span><span class="sxs-lookup"><span data-stu-id="4f05c-132">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="4f05c-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4f05c-133">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

<span data-ttu-id="4f05c-134">Por fim, um novo modificador de acesso composto: `private protected` indica que um membro pode ser acessado pela classe que o contém ou por classes derivadas que são declaradas no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="4f05c-134">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="4f05c-135">Enquanto que `protected internal` permite o acesso por classes derivadas ou classes que estejam no mesmo assembly, o `private protected` limita o acesso a tipos derivados declarados no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="4f05c-135">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="4f05c-136">Para obter mais informações, consulte [modificadores de acesso](../language-reference/keywords/access-modifiers.md) na referência de linguagem.</span><span class="sxs-lookup"><span data-stu-id="4f05c-136">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>
