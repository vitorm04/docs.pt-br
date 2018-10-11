---
title: Novidades no C# 7.3
description: Uma visão geral dos novos recursos no C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: 570da53059242c0242609ddcba5cb23f1728aa9f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47235225"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="928c3-103">Novidades no C# 7.3</span><span class="sxs-lookup"><span data-stu-id="928c3-103">What's new in C# 7.3</span></span>

<span data-ttu-id="928c3-104">Há dois temas principais para a versão C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="928c3-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="928c3-105">Um tema fornece recursos que permitem que o código seguro tenha o mesmo desempenho que o código não seguro.</span><span class="sxs-lookup"><span data-stu-id="928c3-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="928c3-106">O segundo tema fornece melhorias incrementais aos recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="928c3-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="928c3-107">Além disso, novas opções do compilador foram adicionadas nesta versão.</span><span class="sxs-lookup"><span data-stu-id="928c3-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="928c3-108">Os novos recursos a seguir são compatíveis com o tema de melhor desempenho para código seguro:</span><span class="sxs-lookup"><span data-stu-id="928c3-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="928c3-109">Você pode acessar campos fixos sem fixação.</span><span class="sxs-lookup"><span data-stu-id="928c3-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="928c3-110">Você pode reatribuir variáveis locais `ref`.</span><span class="sxs-lookup"><span data-stu-id="928c3-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="928c3-111">Você pode usar inicializadores em matrizes `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="928c3-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="928c3-112">Você pode usar instruções `fixed` com qualquer tipo compatível com um padrão.</span><span class="sxs-lookup"><span data-stu-id="928c3-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="928c3-113">Você pode usar restrições genéricas adicionais.</span><span class="sxs-lookup"><span data-stu-id="928c3-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="928c3-114">Os seguintes recursos e aprimoramentos foram feitos nos recursos existentes:</span><span class="sxs-lookup"><span data-stu-id="928c3-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="928c3-115">Você pode testar `==` e `!=` com tipos de tupla.</span><span class="sxs-lookup"><span data-stu-id="928c3-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="928c3-116">Você pode usar variáveis de expressão em mais locais.</span><span class="sxs-lookup"><span data-stu-id="928c3-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="928c3-117">Você pode anexar atributos ao campo de suporte de propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="928c3-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="928c3-118">A resolução de métodos quando os argumentos se diferenciam por `in` foi aprimorada.</span><span class="sxs-lookup"><span data-stu-id="928c3-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="928c3-119">A resolução de sobrecarga agora tem menos casos ambíguos.</span><span class="sxs-lookup"><span data-stu-id="928c3-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="928c3-120">As novas opções do compilador são:</span><span class="sxs-lookup"><span data-stu-id="928c3-120">The new compiler options are:</span></span>

- <span data-ttu-id="928c3-121">`-publicsign` para habilitar a assinatura de Software de código aberto (OSS) de assemblies.</span><span class="sxs-lookup"><span data-stu-id="928c3-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="928c3-122">`-pathmap` para fornecer um mapeamento para diretórios de origem.</span><span class="sxs-lookup"><span data-stu-id="928c3-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="928c3-123">O restante deste artigo fornece detalhes e links para saber mais sobre cada uma das melhorias.</span><span class="sxs-lookup"><span data-stu-id="928c3-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="928c3-124">Como habilitar código seguro mais eficiente</span><span class="sxs-lookup"><span data-stu-id="928c3-124">Enabling more efficient safe code</span></span>

<span data-ttu-id="928c3-125">Você deve ser capaz de escrever um código C# de forma segurança que seja executado tão bem quanto o código não seguro.</span><span class="sxs-lookup"><span data-stu-id="928c3-125">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="928c3-126">O código seguro evita classes de erros, como estouros de buffer, ponteiros perdidos e outros erros de acesso à memória.</span><span class="sxs-lookup"><span data-stu-id="928c3-126">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="928c3-127">Esses novos recursos expandem as capacidades do código seguro verificável.</span><span class="sxs-lookup"><span data-stu-id="928c3-127">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="928c3-128">Tente escrever mais partes do seu código usando construções seguras.</span><span class="sxs-lookup"><span data-stu-id="928c3-128">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="928c3-129">Esses recursos tornam isso mais fácil.</span><span class="sxs-lookup"><span data-stu-id="928c3-129">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="928c3-130">A indexação de campos `fixed` não requer fixação</span><span class="sxs-lookup"><span data-stu-id="928c3-130">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="928c3-131">Considere este struct:</span><span class="sxs-lookup"><span data-stu-id="928c3-131">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="928c3-132">Em versões anteriores do C#, era preciso fixar uma variável para acessar um dos números inteiros que fazem parte de `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="928c3-132">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="928c3-133">Agora, o código abaixo é compilado em um contexto seguro:</span><span class="sxs-lookup"><span data-stu-id="928c3-133">Now, the following code compiles in a safe context:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="928c3-134">A variável `p` acessa um elemento em `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="928c3-134">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="928c3-135">Não é necessário declarar uma variável `int*` separada.</span><span class="sxs-lookup"><span data-stu-id="928c3-135">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="928c3-136">Você ainda pode precisar de um contexto `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="928c3-136">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="928c3-137">Em versões anteriores do C#, é necessário declarar um segundo ponteiro fixo:</span><span class="sxs-lookup"><span data-stu-id="928c3-137">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="928c3-138">Para obter mais informações, confira o artigo sobre como a [instrução `fixed`](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="928c3-138">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="928c3-139">É possível reatribuir variáveis locais `ref`</span><span class="sxs-lookup"><span data-stu-id="928c3-139">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="928c3-140">Agora, as variáveis locais `ref` podem ser reatribuídas para se referir a diferentes instâncias depois de serem inicializadas.</span><span class="sxs-lookup"><span data-stu-id="928c3-140">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="928c3-141">O comando a seguir agora compila:</span><span class="sxs-lookup"><span data-stu-id="928c3-141">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="928c3-142">Para saber mais, confira o artigo sobre [retornos `ref` e locais `ref`](../programming-guide/classes-and-structs/ref-returns.md) e o artigo sobre [`foreach`](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="928c3-142">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="928c3-143">Matrizes `stackalloc` são compatíveis com inicializadores</span><span class="sxs-lookup"><span data-stu-id="928c3-143">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="928c3-144">Você conseguiu especificar os valores dos elementos em uma matriz ao inicializá-la:</span><span class="sxs-lookup"><span data-stu-id="928c3-144">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="928c3-145">Agora, essa mesma sintaxe pode ser aplicada a matrizes declaradas com `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="928c3-145">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="928c3-146">Para saber mais, confira o artigo [Instrução `stackalloc`](../language-reference/keywords/stackalloc.md) na referência da linguagem.</span><span class="sxs-lookup"><span data-stu-id="928c3-146">For more information, see the [`stackalloc` statement](../language-reference/keywords/stackalloc.md) article in the language reference.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="928c3-147">Mais tipos são compatíveis com a instrução `fixed`</span><span class="sxs-lookup"><span data-stu-id="928c3-147">More types support the `fixed` statement</span></span>

<span data-ttu-id="928c3-148">A instrução `fixed` era compatível com um conjunto limitado de tipos.</span><span class="sxs-lookup"><span data-stu-id="928c3-148">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="928c3-149">A partir do C# 7.3, qualquer tipo que contenha um método `GetPinnableReference()` que retorna `ref T` ou `ref readonly T` pode ser `fixed`.</span><span class="sxs-lookup"><span data-stu-id="928c3-149">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="928c3-150">A adição desse recurso significa que `fixed` pode ser usado com <xref:System.Span%601?displayProperty=nameWithType> e tipos relacionados.</span><span class="sxs-lookup"><span data-stu-id="928c3-150">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="928c3-151">Para saber mais, confira o artigo [Instrução `fixed`](../language-reference/keywords/fixed-statement.md) na referência da linguagem.</span><span class="sxs-lookup"><span data-stu-id="928c3-151">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="928c3-152">Restrições genéricas aprimoradas</span><span class="sxs-lookup"><span data-stu-id="928c3-152">Enhanced generic constraints</span></span>

<span data-ttu-id="928c3-153">Agora é possível especificar o tipo <xref:System.Enum?displayProperty=nameWithType> ou <xref:System.Delegate?displayProperty=nameWithType> como restrições de classe base para um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="928c3-153">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="928c3-154">Você também pode usar a nova restrição `unmanaged` para especificar que um parâmetro de tipo deve ser um **tipo não gerenciado**.</span><span class="sxs-lookup"><span data-stu-id="928c3-154">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="928c3-155">Um **tipo não gerenciado** é um tipo que não é um tipo de referência e não contém campos de tipo de referência em nenhum nível de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="928c3-155">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="928c3-156">Para saber mais, confira os artigos sobre [restrições genéricas `where`](../language-reference/keywords/where-generic-type-constraint.md) e [Restrições a parâmetros de tipo](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="928c3-156">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="928c3-157">Adicionar essas restrições a tipos existentes é uma [alteração incompatível](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="928c3-157">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="928c3-158">Tipos genéricos fechados podem não atender mais a essas novas restrições.</span><span class="sxs-lookup"><span data-stu-id="928c3-158">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="928c3-159">Melhorias nos recursos existentes</span><span class="sxs-lookup"><span data-stu-id="928c3-159">Make existing features better</span></span>

<span data-ttu-id="928c3-160">O segundo tema fornece melhorias aos recursos da linguagem.</span><span class="sxs-lookup"><span data-stu-id="928c3-160">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="928c3-161">Esses recursos melhoram a produtividade ao escrever em C#.</span><span class="sxs-lookup"><span data-stu-id="928c3-161">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="928c3-162">As tuplas são compatíveis com `==` e `!=`</span><span class="sxs-lookup"><span data-stu-id="928c3-162">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="928c3-163">Os tipos de tupla de C# agora são compatíveis com `==` e `!=`.</span><span class="sxs-lookup"><span data-stu-id="928c3-163">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="928c3-164">Para obter mais informações, confira a seção que aborda [igualdade](../tuples.md#equality-and-tuples) no artigo sobre [tuplas](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="928c3-164">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="928c3-165">Anexar atributos aos campos de suporte de propriedades autoimplementadas</span><span class="sxs-lookup"><span data-stu-id="928c3-165">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="928c3-166">Agora há suporte para esta sintaxe:</span><span class="sxs-lookup"><span data-stu-id="928c3-166">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="928c3-167">O atributo `SomeThingAboutFieldAttribute` é aplicado ao campo de suporte gerado pelo compilador para `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="928c3-167">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="928c3-168">Para saber mais, confira [atributos](../programming-guide/concepts/attributes/index.md) no guia de programação em C#.</span><span class="sxs-lookup"><span data-stu-id="928c3-168">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="928c3-169">Resolução de ambiguidade de sobrecarga com o método `in`</span><span class="sxs-lookup"><span data-stu-id="928c3-169">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="928c3-170">Quando o modificador de argumento `in` era adicionado, estes dois métodos causariam ambiguidade:</span><span class="sxs-lookup"><span data-stu-id="928c3-170">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="928c3-171">Agora, a sobrecarga por valor (primeira no exemplo anterior) é melhor do que a versão da referência somente leitura.</span><span class="sxs-lookup"><span data-stu-id="928c3-171">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="928c3-172">Para chamar a versão com o argumento de referência somente leitura, inclua o modificador `in` ao chamar o método.</span><span class="sxs-lookup"><span data-stu-id="928c3-172">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="928c3-173">Isso foi implementado como uma correção de bug.</span><span class="sxs-lookup"><span data-stu-id="928c3-173">This was implemented as a bug fix.</span></span> <span data-ttu-id="928c3-174">Não é mais ambíguo nem mesmo com a versão da linguagem definida como "7.2".</span><span class="sxs-lookup"><span data-stu-id="928c3-174">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="928c3-175">Para saber mais, confira o artigo sobre o [modificador de parâmetro`in`](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="928c3-175">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="928c3-176">Estender variáveis de expressão em inicializadores</span><span class="sxs-lookup"><span data-stu-id="928c3-176">Extend expression variables in initializers</span></span>

<span data-ttu-id="928c3-177">A sintaxe adicionada no C# 7.0 para permitir declarações de variável `out` foi estendida para incluir inicializadores de campo, inicializadores de propriedade, inicializadores de construtor e cláusulas de consulta.</span><span class="sxs-lookup"><span data-stu-id="928c3-177">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="928c3-178">Ela permite código como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="928c3-178">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="928c3-179">Candidatos de sobrecarga aprimorados</span><span class="sxs-lookup"><span data-stu-id="928c3-179">Improved overload candidates</span></span>

<span data-ttu-id="928c3-180">Em cada versão, as regras de resolução de sobrecarga são atualizadas para resolver situações em que as chamadas de método ambíguas têm uma opção "óbvia".</span><span class="sxs-lookup"><span data-stu-id="928c3-180">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="928c3-181">Esta versão adiciona três novas regras para ajudar o compilador a escolher a opção óbvia:</span><span class="sxs-lookup"><span data-stu-id="928c3-181">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="928c3-182">Quando um grupo de métodos contém membros de instância e estáticos, o compilador descartará os membros da instância se o método tiver sido chamado sem um receptor ou contexto de instância.</span><span class="sxs-lookup"><span data-stu-id="928c3-182">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="928c3-183">O compilador descartará os membros estáticos se o método tiver sido chamado com um receptor de instância.</span><span class="sxs-lookup"><span data-stu-id="928c3-183">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="928c3-184">Quando não há receptor, o compilador inclui apenas membros estáticos em um contexto estático, caso contrário, membros estáticos e de instância.</span><span class="sxs-lookup"><span data-stu-id="928c3-184">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="928c3-185">Quando o receptor é ambiguamente uma instância ou um tipo, o compilador inclui ambos.</span><span class="sxs-lookup"><span data-stu-id="928c3-185">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="928c3-186">Um contexto estático, em que não é possível usar um receptor de instância `this` implícito, inclui o corpo de membros em que nenhum `this` é definido, como membros estáticos, bem como locais onde `this` não pode ser usado, como inicializadores de campo e inicializadores de construtor.</span><span class="sxs-lookup"><span data-stu-id="928c3-186">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="928c3-187">Quando um grupo de métodos contém alguns métodos genéricos cujos argumentos de tipo não satisfazem suas restrições, esses membros são removidos do conjunto de candidatos.</span><span class="sxs-lookup"><span data-stu-id="928c3-187">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="928c3-188">Para uma conversão de grupo de métodos, os métodos candidatos cujo tipo de retorno não corresponda ao tipo de retorno do delegado são removidos do conjunto.</span><span class="sxs-lookup"><span data-stu-id="928c3-188">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="928c3-189">Você notará essa mudança somente porque encontrará menos erros de compilador para sobrecargas de métodos ambíguos quando tiver certeza de qual método é melhor.</span><span class="sxs-lookup"><span data-stu-id="928c3-189">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="928c3-190">Novas opções do compilador</span><span class="sxs-lookup"><span data-stu-id="928c3-190">New compiler options</span></span>

<span data-ttu-id="928c3-191">Novas opções do compilador são compatíveis com novos cenários de build e DevOps para programas C#.</span><span class="sxs-lookup"><span data-stu-id="928c3-191">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="928c3-192">Assinatura pública ou de código aberto</span><span class="sxs-lookup"><span data-stu-id="928c3-192">Public or Open Source signing</span></span>

<span data-ttu-id="928c3-193">A opção de compilador `-publicsign` instrui o compilador a assinar o assembly usando uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="928c3-193">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="928c3-194">O assembly é marcado como assinado, mas a assinatura é obtida da chave pública.</span><span class="sxs-lookup"><span data-stu-id="928c3-194">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="928c3-195">Essa opção permite criar crie assemblies assinados a partir de projetos de código aberto usando uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="928c3-195">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="928c3-196">Para saber mais, confira o artigo [Opção do compilador -publicsign](../language-reference/compiler-options/publicsign-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="928c3-196">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="928c3-197">pathmap</span><span class="sxs-lookup"><span data-stu-id="928c3-197">pathmap</span></span>

<span data-ttu-id="928c3-198">A opção de compilador `-pathmap` instrui o compilador a substituir os caminhos de origem do ambiente de build com caminhos de origem mapeados.</span><span class="sxs-lookup"><span data-stu-id="928c3-198">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="928c3-199">A opção `-pathmap` controla o caminho de origem gravado pelo compilador para arquivos PDB ou para o <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="928c3-199">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="928c3-200">Para saber mais, confira o artigo [Opção do compilador -pathmap](../language-reference/compiler-options/pathmap-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="928c3-200">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
