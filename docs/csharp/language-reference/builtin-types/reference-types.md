---
title: Tipos de referência internos – Referência de C#
description: Saiba mais sobre os tipos de referência que têm palavras-chave do C# que você pode usar para declará-las.
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: 4bc93216d74e2732870e08edd4bdb9570391cf5f
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67872164"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="04e9f-103">Tipos de referência internos (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="04e9f-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="04e9f-104">O C# tem um número de tipos de referência internos.</span><span class="sxs-lookup"><span data-stu-id="04e9f-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="04e9f-105">Eles têm palavras-chave ou operadores que são sinônimos de um tipo na biblioteca do .NET.</span><span class="sxs-lookup"><span data-stu-id="04e9f-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span> 

## <a name="the-object-type"></a><span data-ttu-id="04e9f-106">O tipo de objeto</span><span class="sxs-lookup"><span data-stu-id="04e9f-106">The object type</span></span>

<span data-ttu-id="04e9f-107">O tipo `object` é um alias de <xref:System.Object?displayProperty=nameWithType> no .NET.</span><span class="sxs-lookup"><span data-stu-id="04e9f-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="04e9f-108">No sistema de tipos unificado do C#, todos os tipos, predefinidos e definidos pelo usuário, tipos de referência e tipos de valor, herdam direta ou indiretamente de <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04e9f-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="04e9f-109">Você pode atribuir valores de qualquer tipo a variáveis do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="04e9f-110">Qualquer variável `object` pode ser atribuída ao seu valor padrão usando o literal `null`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="04e9f-111">Quando uma variável de um tipo de valor é convertida para um objeto, ela é chamada de *boxed*.</span><span class="sxs-lookup"><span data-stu-id="04e9f-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="04e9f-112">Quando uma variável do objeto do tipo é convertida para um tipo de valor, ela é chamada de *unboxed*.</span><span class="sxs-lookup"><span data-stu-id="04e9f-112">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="04e9f-113">Para obter mais informações, consulte [Boxing e unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="04e9f-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span> 

## <a name="the-string-type"></a><span data-ttu-id="04e9f-114">O tipo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04e9f-114">The string type</span></span>

<span data-ttu-id="04e9f-115">O tipo `string` representa uma sequência de zero ou mais caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="04e9f-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="04e9f-116">`string` é um alias de <xref:System.String?displayProperty=nameWithType> no .NET.</span><span class="sxs-lookup"><span data-stu-id="04e9f-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="04e9f-117">Embora `string` seja um tipo de referência, os [operadores de igualdade `==` e `!=`](../operators/equality-operators.md#string-equality) são definidos para comparar os valores de objetos `string`, não referências.</span><span class="sxs-lookup"><span data-stu-id="04e9f-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="04e9f-118">Isso torna o teste de igualdade de cadeia de caracteres mais intuitivo.</span><span class="sxs-lookup"><span data-stu-id="04e9f-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="04e9f-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="04e9f-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="04e9f-120">Isso exibe "True" e, em seguida, "False" porque os conteúdos das cadeias de caracteres são equivalentes, mas `a` e `b` não fazem referência à mesma instância da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="04e9f-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="04e9f-121">O [operador +](../operators/addition-operator.md#string-concatenation) concatena as cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="04e9f-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="04e9f-122">Isso cria um objeto de cadeia de caracteres que contém “good morning”.</span><span class="sxs-lookup"><span data-stu-id="04e9f-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="04e9f-123">Cadeias de caracteres são *imutável* – o conteúdo de um objeto de cadeia de caracteres não pode ser alterado depois que o objeto é criado, embora a sintaxe faça com que pareça que você pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="04e9f-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="04e9f-124">Por exemplo, quando você escreve esse código, o compilador, na verdade, cria um objeto de cadeia de caracteres para manter a nova sequência de caracteres e esse novo objeto é atribuído a `b`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="04e9f-125">A memória que tiver sido alocada para `b` (quando ela continha a cadeia de caracteres "h") será elegível para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="04e9f-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="04e9f-126">O [operador](../operators/member-access-operators.md#indexer-operator-) `[]` pode ser usado para acesso somente leitura a caracteres individuais de um `string`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a `string`.</span></span> <span data-ttu-id="04e9f-127">Os valores válidos começam em `0` e devem ser menores do que o comprimento do `string`:</span><span class="sxs-lookup"><span data-stu-id="04e9f-127">Valid values start at `0` and must be less than the length of the `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="04e9f-128">De maneira semelhante, o operador `[]` também pode ser usado para iterar em cada caractere em um `string`:</span><span class="sxs-lookup"><span data-stu-id="04e9f-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a `string`:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="04e9f-129">Literais de cadeia de caracteres são do tipo `string` e podem ser escritos de duas formas, entre aspas e `@`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="04e9f-130">Os literais de cadeia de caracteres entre aspas são colocados entre aspas duplas ("):</span><span class="sxs-lookup"><span data-stu-id="04e9f-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="04e9f-131">Os literais de cadeia de caracteres podem conter qualquer literal de caractere.</span><span class="sxs-lookup"><span data-stu-id="04e9f-131">String literals can contain any character literal.</span></span> <span data-ttu-id="04e9f-132">Sequências de escape são incluídas.</span><span class="sxs-lookup"><span data-stu-id="04e9f-132">Escape sequences are included.</span></span> <span data-ttu-id="04e9f-133">O exemplo a seguir usa a sequência de escape `\\` de barra invertida, `\u0066` para a letra f e `\n` para a nova linha.</span><span class="sxs-lookup"><span data-stu-id="04e9f-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> <span data-ttu-id="04e9f-134">O código de escape `\udddd` (em que `dddd` é um número de quatro dígitos) representa o caractere Unicode U+`dddd`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="04e9f-135">Os códigos de escape Unicode de oito dígitos também são reconhecidos: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="04e9f-136">Os [literais de cadeia de caracteres textuais](../tokens/verbatim.md) começam com `@` e também são colocados entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="04e9f-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="04e9f-137">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="04e9f-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="04e9f-138">A vantagem das cadeias de caracteres textuais é que as sequências de escape *não* são processadas, o que torna mais fácil escrever, por exemplo, um nome de arquivo totalmente qualificado do Windows:</span><span class="sxs-lookup"><span data-stu-id="04e9f-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="04e9f-139">Para incluir aspas duplas em uma cadeia de caracteres @-quoted, dobre-a:</span><span class="sxs-lookup"><span data-stu-id="04e9f-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="04e9f-140">O tipo de delegado</span><span class="sxs-lookup"><span data-stu-id="04e9f-140">The delegate type</span></span>

<span data-ttu-id="04e9f-141">A declaração de um tipo de delegado é semelhante a uma assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="04e9f-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="04e9f-142">Ela tem um valor retornado e parâmetros de qualquer tipo:</span><span class="sxs-lookup"><span data-stu-id="04e9f-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="04e9f-143">No .NET, os tipos `System.Action` e `System.Func` fornecem definições genéricas para muitos delegados comuns.</span><span class="sxs-lookup"><span data-stu-id="04e9f-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="04e9f-144">Você provavelmente não precisa definir novos tipos de delegado personalizado.</span><span class="sxs-lookup"><span data-stu-id="04e9f-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="04e9f-145">Em vez disso, é possível criar instâncias dos tipos genéricos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="04e9f-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="04e9f-146">Um `delegate` é um tipo de referência que pode ser usado para encapsular um método nomeado ou anônimo.</span><span class="sxs-lookup"><span data-stu-id="04e9f-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="04e9f-147">Representantes são semelhantes a ponteiros de função em C++. No entanto, os representantes são fortemente tipados e seguros.</span><span class="sxs-lookup"><span data-stu-id="04e9f-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="04e9f-148">Para aplicativos de representantes, consulte [Representantes](../../programming-guide/delegates/index.md) e [Representantes genéricos](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="04e9f-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="04e9f-149">Os representantes são a base dos [Eventos](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="04e9f-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="04e9f-150">Um delegado pode ser instanciado associando-o a um método nomeado ou anônimo.</span><span class="sxs-lookup"><span data-stu-id="04e9f-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="04e9f-151">O delegado deve ser instanciado com um método ou expressão lambda que tenha um tipo de retorno compatível e parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="04e9f-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="04e9f-152">Para obter mais informações sobre o grau de variação permitido na assinatura do método, consulte [Variação em representantes](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="04e9f-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="04e9f-153">Para uso com métodos anônimos, o delegado e o código a ser associado a ele são declarados juntos.</span><span class="sxs-lookup"><span data-stu-id="04e9f-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> 

## <a name="the-dynamic-type"></a><span data-ttu-id="04e9f-154">O tipo dinâmico</span><span class="sxs-lookup"><span data-stu-id="04e9f-154">The dynamic type</span></span>

<span data-ttu-id="04e9f-155">O tipo `dynamic` indica que o uso de variável e as referências aos seus membros ignoram a verificação de tipo de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="04e9f-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="04e9f-156">Em vez disso, essas operações são resolvidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="04e9f-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="04e9f-157">O tipo `dynamic` simplifica o acesso a APIs COM, como as APIs de Automação do Office e também às APIs dinâmicas, como bibliotecas do IronPython e ao DOM (Modelo de Objeto do Documento) HTML.</span><span class="sxs-lookup"><span data-stu-id="04e9f-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="04e9f-158">O tipo `dynamic` se comporta como o tipo `object` na maioria das circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="04e9f-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="04e9f-159">Em particular, qualquer expressão não nula pode ser convertida no tipo `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="04e9f-160">O tipo `dynamic` é diferente de `object` nas operações que contêm expressões do tipo `dynamic` não resolvidas ou com tipo verificado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="04e9f-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="04e9f-161">O compilador junta as informações sobre a operação em pacotes e, posteriormente, essas informações são usadas para avaliar a operação em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="04e9f-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="04e9f-162">Como parte do processo, as variáveis do tipo `dynamic` são compiladas em variáveis do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="04e9f-163">Portanto, o tipo `dynamic` existe somente em tempo de compilação e não em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="04e9f-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="04e9f-164">O exemplo a seguir compara uma variável do tipo `dynamic` a uma variável do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="04e9f-165">Para verificar o tipo de cada variável no tempo de compilação, coloque o ponteiro do mouse sobre `dyn` ou `obj` nas instruções `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="04e9f-166">Copie o seguinte código para um editor em que o IntelliSense está disponível.</span><span class="sxs-lookup"><span data-stu-id="04e9f-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="04e9f-167">O IntelliSense mostra **dinâmico** para `dyn` e **objeto** para `obj`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="04e9f-168">As instruções <xref:System.Console.WriteLine%2A> exibem os tipos de tempo de execução de `dyn` e `obj`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="04e9f-169">Nesse ponto, ambos têm o mesmo tipo, inteiro.</span><span class="sxs-lookup"><span data-stu-id="04e9f-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="04e9f-170">A saída a seguir será produzida:</span><span class="sxs-lookup"><span data-stu-id="04e9f-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="04e9f-171">Para ver a diferença entre `dyn` e `obj` em tempo de compilação, adicione as duas linhas a seguir entre as declarações e as instruções `WriteLine` no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="04e9f-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="04e9f-172">Um erro de compilador será relatado em virtude da tentativa de adição de um inteiro e um objeto à expressão `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="04e9f-173">No entanto, nenhum erro será relatado para `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="04e9f-174">A expressão contém `dyn` não é verificada em tempo de compilação, pois o tipo de `dyn` é `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="04e9f-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="04e9f-175">O exemplo a seguir usa `dynamic` em várias declarações.</span><span class="sxs-lookup"><span data-stu-id="04e9f-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="04e9f-176">O método `Main` também compara a verificação de tipo em tempo de compilação com a verificação de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="04e9f-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="04e9f-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04e9f-177">See also</span></span>

- [<span data-ttu-id="04e9f-178">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="04e9f-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="04e9f-179">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="04e9f-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="04e9f-180">Eventos</span><span class="sxs-lookup"><span data-stu-id="04e9f-180">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="04e9f-181">Usando o tipo dynamic</span><span class="sxs-lookup"><span data-stu-id="04e9f-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="04e9f-182">Melhores práticas para o uso de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="04e9f-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="04e9f-183">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="04e9f-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="04e9f-184">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="04e9f-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="04e9f-185">Operadores de conversão e teste de tipo</span><span class="sxs-lookup"><span data-stu-id="04e9f-185">Type-testing and conversion operators</span></span>](../operators/type-testing-and-conversion-operators.md)
- [<span data-ttu-id="04e9f-186">Como converter com segurança usando a correspondência de padrões e os operadores is e as</span><span class="sxs-lookup"><span data-stu-id="04e9f-186">How to: safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="04e9f-187">Passo a passo: Criando e usando objetos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="04e9f-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
