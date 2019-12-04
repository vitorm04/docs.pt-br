---
title: Reflexão (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711669"
---
# <a name="reflection-c"></a><span data-ttu-id="a10d2-102">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="a10d2-102">Reflection (C#)</span></span>

<span data-ttu-id="a10d2-103">A reflexão fornece objetos (do tipo <xref:System.Type>) que descrevem assemblies, módulos e tipos.</span><span class="sxs-lookup"><span data-stu-id="a10d2-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules, and types.</span></span> <span data-ttu-id="a10d2-104">É possível usar a reflexão para criar dinamicamente uma instância de um tipo, associar o tipo a um objeto existente ou obter o tipo de um objeto existente e invocar seus métodos ou acessar suas propriedades e campos.</span><span class="sxs-lookup"><span data-stu-id="a10d2-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="a10d2-105">Se você estiver usando atributos em seu código, a reflexão permite acessá-los.</span><span class="sxs-lookup"><span data-stu-id="a10d2-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="a10d2-106">Para obter mais informações, consulte [Atributos](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="a10d2-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>

<span data-ttu-id="a10d2-107">Veja um exemplo simples de reflexão usando o método de <xref:System.Object.GetType> herdado por todos os tipos da classe base `Object`-para obter o tipo de uma variável:</span><span class="sxs-lookup"><span data-stu-id="a10d2-107">Here's a simple example of reflection using the <xref:System.Object.GetType> method - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>

> [!NOTE]
> <span data-ttu-id="a10d2-108">Certifique-se de adicionar `using System;` e `using System.Reflection;` na parte superior do seu arquivo *. cs* .</span><span class="sxs-lookup"><span data-stu-id="a10d2-108">Make sure you add `using System;` and `using System.Reflection;` at the top of your *.cs* file.</span></span>

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

<span data-ttu-id="a10d2-109">A saída é: `System.Int32`.</span><span class="sxs-lookup"><span data-stu-id="a10d2-109">The output is: `System.Int32`.</span></span>

<span data-ttu-id="a10d2-110">O exemplo a seguir usa a reflexão para obter o nome completo do assembly carregado.</span><span class="sxs-lookup"><span data-stu-id="a10d2-110">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

<span data-ttu-id="a10d2-111">A saída é: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span><span class="sxs-lookup"><span data-stu-id="a10d2-111">The output is: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.</span></span>

> [!NOTE]
> <span data-ttu-id="a10d2-112">As palavras-chave de C# `protected` e `internal` não têm significado no IL e não são usadas nas APIs de reflexão.</span><span class="sxs-lookup"><span data-stu-id="a10d2-112">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="a10d2-113">Os termos correspondentes na IL são *Família* e *Assembly*.</span><span class="sxs-lookup"><span data-stu-id="a10d2-113">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="a10d2-114">Para identificar um método `internal` usando a reflexão, use a propriedade <xref:System.Reflection.MethodBase.IsAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="a10d2-114">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="a10d2-115">Para identificar um método `protected internal`, use o <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="a10d2-115">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>

## <a name="reflection-overview"></a><span data-ttu-id="a10d2-116">Visão geral da reflexão</span><span class="sxs-lookup"><span data-stu-id="a10d2-116">Reflection overview</span></span>

<span data-ttu-id="a10d2-117">A reflexão é útil nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="a10d2-117">Reflection is useful in the following situations:</span></span>

- <span data-ttu-id="a10d2-118">Quando você precisa acessar atributos nos metadados do seu programa.</span><span class="sxs-lookup"><span data-stu-id="a10d2-118">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="a10d2-119">Para obter mais informações, consulte [Recuperando informações armazenadas em atributos](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a10d2-119">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>
- <span data-ttu-id="a10d2-120">Para examinar e instanciar tipos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="a10d2-120">For examining and instantiating types in an assembly.</span></span>
- <span data-ttu-id="a10d2-121">Para criar novos tipos em runtime.</span><span class="sxs-lookup"><span data-stu-id="a10d2-121">For building new types at runtime.</span></span> <span data-ttu-id="a10d2-122">Usar as classes em <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="a10d2-122">Use classes in <xref:System.Reflection.Emit>.</span></span>
- <span data-ttu-id="a10d2-123">Para executar a associação tardia, acessar métodos em tipos criados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a10d2-123">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="a10d2-124">Consulte o tópico [Carregando e usando tipos dinamicamente](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="a10d2-124">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>

## <a name="related-sections"></a><span data-ttu-id="a10d2-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a10d2-125">Related sections</span></span>

<span data-ttu-id="a10d2-126">Para obter mais informações: ,</span><span class="sxs-lookup"><span data-stu-id="a10d2-126">For more information:</span></span>

- [<span data-ttu-id="a10d2-127">Reflexão</span><span class="sxs-lookup"><span data-stu-id="a10d2-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="a10d2-128">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="a10d2-128">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="a10d2-129">Reflexão e tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="a10d2-129">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [<span data-ttu-id="a10d2-130">Recuperando informações armazenadas em atributos</span><span class="sxs-lookup"><span data-stu-id="a10d2-130">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a><span data-ttu-id="a10d2-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a10d2-131">See also</span></span>

- [<span data-ttu-id="a10d2-132">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a10d2-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a10d2-133">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="a10d2-133">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
