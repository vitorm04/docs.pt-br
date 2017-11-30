---
title: "O que há de novo no c# 7.2"
description: "Uma visão geral dos novos recursos no c# 7.2."
keywords: Design de linguagem c#, 7.2, Visual Studio de 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: a580a4a3a0a49e97ea8fb96699d1d978a9bc0a64
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="920d6-104">O que há de novo no c# 7.2</span><span class="sxs-lookup"><span data-stu-id="920d6-104">What's new in C# 7.2</span></span>

<span data-ttu-id="920d6-105">7.2 c# é outra versão do ponto que adiciona um número de recursos úteis.</span><span class="sxs-lookup"><span data-stu-id="920d6-105">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="920d6-106">Um tema para esta versão está trabalhando com mais eficiência com tipos de valor, evitando cópias desnecessárias ou alocações.</span><span class="sxs-lookup"><span data-stu-id="920d6-106">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="920d6-107">Os recursos restantes são pequenos, ótimo ter recursos.</span><span class="sxs-lookup"><span data-stu-id="920d6-107">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="920d6-108">7.2 c# usa o [seleção de versão de idioma](csharp-7-1.md#language-version-selection) elemento de configuração para selecionar a versão de idioma do compilador.</span><span class="sxs-lookup"><span data-stu-id="920d6-108">C# 7.2 uses the [language version selection](csharp-7-1.md#language-version-selection) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="920d6-109">Os novos recursos de idioma nesta versão são:</span><span class="sxs-lookup"><span data-stu-id="920d6-109">The new language features in this release are:</span></span>

* [<span data-ttu-id="920d6-110">Semântica de referência com tipos de valor</span><span class="sxs-lookup"><span data-stu-id="920d6-110">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="920d6-111">Uma combinação de aprimoramentos de sintaxe que permitem trabalhar com tipos de valor usando a semântica de referência.</span><span class="sxs-lookup"><span data-stu-id="920d6-111">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="920d6-112">Argumentos nomeada à direita não</span><span class="sxs-lookup"><span data-stu-id="920d6-112">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="920d6-113">Argumentos nomeados podem ser seguidos por argumentos posicionais.</span><span class="sxs-lookup"><span data-stu-id="920d6-113">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="920d6-114">Sublinhados em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="920d6-114">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="920d6-115">Literais numéricos agora podem ter sublinhados antes dos dígitos impressos.</span><span class="sxs-lookup"><span data-stu-id="920d6-115">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="920d6-116">`private protected`modificador de acesso</span><span class="sxs-lookup"><span data-stu-id="920d6-116">`private protected` access modifier</span></span>](#private-protected)
  - <span data-ttu-id="920d6-117">O `private protected` modificador de acesso permite o acesso para classes derivadas no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="920d6-117">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="920d6-118">Semântica de referência com tipos de valor</span><span class="sxs-lookup"><span data-stu-id="920d6-118">Reference semantics with value types</span></span>

<span data-ttu-id="920d6-119">Recursos de idioma introduzidos no 7.2 permitem trabalhar com tipos de valor ao usar semântica de referência.</span><span class="sxs-lookup"><span data-stu-id="920d6-119">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="920d6-120">Eles são projetados para melhorar o desempenho, minimizando a cópia de tipos de valor sem incorrer as alocações de memória associadas ao uso de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="920d6-120">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="920d6-121">Os recursos incluem:</span><span class="sxs-lookup"><span data-stu-id="920d6-121">The features include:</span></span>

 - <span data-ttu-id="920d6-122">O `in` modificador em parâmetros para especificar que um argumento é passado por referência, mas não modificado pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="920d6-122">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="920d6-123">O `ref readonly` modificador no método retorna, para indicar que um método retorna seu valor por referência, mas não permite gravações para o objeto.</span><span class="sxs-lookup"><span data-stu-id="920d6-123">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="920d6-124">O `readonly struct` declaração, para indicar que uma struct é imutável e deve ser passada como um `in` parâmetro para seus métodos de membro.</span><span class="sxs-lookup"><span data-stu-id="920d6-124">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="920d6-125">O `ref struct` declaração, para indicar que um tipo struct acessa memória gerenciada diretamente e deve sempre ser pilha alocada.</span><span class="sxs-lookup"><span data-stu-id="920d6-125">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="920d6-126">Você pode ler mais sobre todas essas alterações em [com a semântica de referência de tipos de valor](../reference-semantics-with-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="920d6-126">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="920d6-127">Argumentos nomeada à direita não</span><span class="sxs-lookup"><span data-stu-id="920d6-127">Non-trailing named arguments</span></span>

<span data-ttu-id="920d6-128">Chamadas de método agora podem usar argumentos nomeados que precedem argumentos posicionais quando esses argumentos nomeados são nas posições corretas.</span><span class="sxs-lookup"><span data-stu-id="920d6-128">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="920d6-129">Para obter mais informações, consulte [nomeadas e argumentos opcionais](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="920d6-129">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="920d6-130">Sublinhados em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="920d6-130">Leading underscores in numeric literals</span></span>

<span data-ttu-id="920d6-131">A implementação de suporte para os separadores de dígitos no c# 7.0 não permite a `_` para ser o primeiro caractere do valor literal.</span><span class="sxs-lookup"><span data-stu-id="920d6-131">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="920d6-132">Literais numéricos binários e hex agora podem começar com um `_`.</span><span class="sxs-lookup"><span data-stu-id="920d6-132">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="920d6-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="920d6-133">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

<span data-ttu-id="920d6-134">Por fim, um novo modificador de acesso composta: `private protected` indica que um membro pode ser acessado por classes derivadas que são declaradas no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="920d6-134">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="920d6-135">Enquanto `protected internal` permite o acesso por classes derivadas ou classes que estão no mesmo assembly, `private protected` limita o acesso a tipos derivados declarado no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="920d6-135">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="920d6-136">Para obter mais informações, consulte [modificadores de acesso](../language-reference/keywords/access-modifiers.md) na referência de linguagem.</span><span class="sxs-lookup"><span data-stu-id="920d6-136">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>
