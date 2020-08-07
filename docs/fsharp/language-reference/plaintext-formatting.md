---
title: Formatação de texto sem formatação
description: 'Saiba como usar printf e outra formatação de texto sem formatação em aplicativos e scripts em F #.'
ms.date: 07/22/2020
ms.openlocfilehash: 6b14633e074961757d0f0cd258d1b1667f5fd8ee
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854913"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="91e5a-103">Formatação de texto sem formatação</span><span class="sxs-lookup"><span data-stu-id="91e5a-103">Plain text formatting</span></span>

<span data-ttu-id="91e5a-104">O F # dá suporte à formatação verificada por tipo de texto sem formatação usando as `printf` `printfn` funções relacionadas,, e `sprintf` .</span><span class="sxs-lookup"><span data-stu-id="91e5a-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="91e5a-105">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="91e5a-106">fornece a saída</span><span class="sxs-lookup"><span data-stu-id="91e5a-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="91e5a-107">O F # também permite que valores estruturados sejam formatados como texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="91e5a-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="91e5a-108">Por exemplo, considere o exemplo a seguir que formata a saída como uma exibição matricial de tuplas.</span><span class="sxs-lookup"><span data-stu-id="91e5a-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="91e5a-109">A formatação de texto simples estruturado é ativada quando você usa o `%A` formato em `printf` cadeias de caracteres de formatação.</span><span class="sxs-lookup"><span data-stu-id="91e5a-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="91e5a-110">Ele também é ativado ao Formatar a saída de valores em F # Interactive, em que a saída inclui informações extras e também é personalizável.</span><span class="sxs-lookup"><span data-stu-id="91e5a-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="91e5a-111">A formatação de texto sem formatação também é observável por meio de todas as chamadas para `x.ToString()` valores de União e registro em F #, incluindo aquelas que ocorrem implicitamente na depuração, no registro em log e em outras ferramentas.</span><span class="sxs-lookup"><span data-stu-id="91e5a-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="91e5a-112">Verificação de `printf` cadeias de caracteres de formato</span><span class="sxs-lookup"><span data-stu-id="91e5a-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="91e5a-113">Um erro de tempo de compilação será relatado se uma `printf` função de formatação for usada com um argumento que não corresponda aos especificadores de formato printf na cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="91e5a-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="91e5a-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="91e5a-115">fornece a saída</span><span class="sxs-lookup"><span data-stu-id="91e5a-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="91e5a-116">Falando tecnicamente, ao usar `printf` e outras funções relacionadas, uma regra especial no compilador F # verifica o literal de cadeia de caracteres passado como a cadeia de caracteres de formato, garantindo que os argumentos subsequentes aplicados sejam do tipo correto para corresponder aos especificadores de formato usados.</span><span class="sxs-lookup"><span data-stu-id="91e5a-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="91e5a-117">Especificadores de formato para`printf`</span><span class="sxs-lookup"><span data-stu-id="91e5a-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="91e5a-118">As especificações de formato para `printf` formatos são cadeias de caracteres com `%` marcadores que indicam o formato.</span><span class="sxs-lookup"><span data-stu-id="91e5a-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="91e5a-119">Espaços reservados de formato consistem `%[flags][width][.precision][type]` em onde o tipo é interpretado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="91e5a-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="91e5a-120">Especificador de formato</span><span class="sxs-lookup"><span data-stu-id="91e5a-120">Format specifier</span></span>   | <span data-ttu-id="91e5a-121">Tipo (s)</span><span class="sxs-lookup"><span data-stu-id="91e5a-121">Type(s)</span></span>        | <span data-ttu-id="91e5a-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="91e5a-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="91e5a-123">bool</span><span class="sxs-lookup"><span data-stu-id="91e5a-123">bool</span></span>      | <span data-ttu-id="91e5a-124">Formatado como `true` ou`false`</span><span class="sxs-lookup"><span data-stu-id="91e5a-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="91e5a-125">string</span><span class="sxs-lookup"><span data-stu-id="91e5a-125">string</span></span>    | <span data-ttu-id="91e5a-126">Formatado como seu conteúdo sem escape</span><span class="sxs-lookup"><span data-stu-id="91e5a-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="91e5a-127">char</span><span class="sxs-lookup"><span data-stu-id="91e5a-127">char</span></span>      | <span data-ttu-id="91e5a-128">Formatado como o literal de caractere</span><span class="sxs-lookup"><span data-stu-id="91e5a-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="91e5a-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="91e5a-129">`%d`, `%i`</span></span>         | <span data-ttu-id="91e5a-130">um tipo inteiro básico</span><span class="sxs-lookup"><span data-stu-id="91e5a-130">a basic integer type</span></span> | <span data-ttu-id="91e5a-131">Formatado como um inteiro decimal, assinado se o tipo de inteiro básico for assinado</span><span class="sxs-lookup"><span data-stu-id="91e5a-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="91e5a-132">um tipo inteiro básico</span><span class="sxs-lookup"><span data-stu-id="91e5a-132">a basic integer type</span></span> | <span data-ttu-id="91e5a-133">Formatado como um inteiro decimal sem sinal</span><span class="sxs-lookup"><span data-stu-id="91e5a-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="91e5a-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="91e5a-134">`%x`, `%X`</span></span>         | <span data-ttu-id="91e5a-135">um tipo inteiro básico</span><span class="sxs-lookup"><span data-stu-id="91e5a-135">a basic integer type</span></span> | <span data-ttu-id="91e5a-136">Formatado como um número hexadecimal não assinado (a-f ou A-F para dígitos hexadecimais, respectivamente)</span><span class="sxs-lookup"><span data-stu-id="91e5a-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="91e5a-137">um tipo inteiro básico</span><span class="sxs-lookup"><span data-stu-id="91e5a-137">a basic integer type</span></span> | <span data-ttu-id="91e5a-138">Formatado como um número octal não assinado</span><span class="sxs-lookup"><span data-stu-id="91e5a-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="91e5a-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="91e5a-139">`%e`, `%E`</span></span>         | <span data-ttu-id="91e5a-140">um tipo de ponto flutuante básico</span><span class="sxs-lookup"><span data-stu-id="91e5a-140">a basic floating point type</span></span> | <span data-ttu-id="91e5a-141">Formatado como um valor assinado, tendo o formato `[-]d.dddde[sign]ddd` em que d é um único dígito decimal, dddd é um ou mais dígitos decimais, o DDD tem exatamente três dígitos decimais e o sinal é `+` ou`-`</span><span class="sxs-lookup"><span data-stu-id="91e5a-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="91e5a-142">um tipo de ponto flutuante básico</span><span class="sxs-lookup"><span data-stu-id="91e5a-142">a basic floating point type</span></span> | <span data-ttu-id="91e5a-143">Formatado como um valor assinado com o formulário `[-]dddd.dddd` , em que `dddd` é um ou mais dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="91e5a-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="91e5a-144">O número de dígitos antes do ponto decimal depende da magnitude do número, e o número de dígitos após o ponto decimal depende da precisão solicitada.</span><span class="sxs-lookup"><span data-stu-id="91e5a-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="91e5a-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="91e5a-145">`%g`, `%G`</span></span> | <span data-ttu-id="91e5a-146">um tipo de ponto flutuante básico</span><span class="sxs-lookup"><span data-stu-id="91e5a-146">a basic floating point type</span></span> |  <span data-ttu-id="91e5a-147">Formatado usando como um valor assinado, impresso em `%f` ou `%e` formato, o que for mais compacto para o valor e a precisão especificados.</span><span class="sxs-lookup"><span data-stu-id="91e5a-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="91e5a-148">um `System.Decimal` valor</span><span class="sxs-lookup"><span data-stu-id="91e5a-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="91e5a-149">Formatado usando o `"G"` especificador de formato para`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="91e5a-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="91e5a-150">qualquer valor</span><span class="sxs-lookup"><span data-stu-id="91e5a-150">any value</span></span>  |   <span data-ttu-id="91e5a-151">Formatado por Boxing o objeto e chamando seu `System.Object.ToString()` método</span><span class="sxs-lookup"><span data-stu-id="91e5a-151">Formatted by boxing the object and calling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="91e5a-152">qualquer valor</span><span class="sxs-lookup"><span data-stu-id="91e5a-152">any value</span></span>  |   <span data-ttu-id="91e5a-153">Formatado usando a [formatação de texto simples estruturado](plaintext-formatting.md) com as configurações de layout padrão</span><span class="sxs-lookup"><span data-stu-id="91e5a-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="91e5a-154">qualquer valor</span><span class="sxs-lookup"><span data-stu-id="91e5a-154">any value</span></span>  |   <span data-ttu-id="91e5a-155">Requer dois argumentos: uma função de formatação que aceita um parâmetro de contexto e o valor, e o valor específico a ser impresso</span><span class="sxs-lookup"><span data-stu-id="91e5a-155">Requires two arguments: a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="91e5a-156">qualquer valor</span><span class="sxs-lookup"><span data-stu-id="91e5a-156">any value</span></span>  |   <span data-ttu-id="91e5a-157">Requer um argumento: uma função de formatação que aceita um parâmetro de contexto que gera ou retorna o texto apropriado</span><span class="sxs-lookup"><span data-stu-id="91e5a-157">Requires one argument: a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |

<span data-ttu-id="91e5a-158">Os tipos de inteiro básicos são `byte` ( `System.Byte` ), `sbyte` ( `System.SByte` ), `int16` ( `System.Int16` ), `uint16` ( `System.UInt16` ), `int32` ( `System.Int32` ), `uint32` ( `System.UInt32` ), `int64` () `System.Int64` , `uint64` ( `System.UInt64` ), `nativeint` ( `System.IntPtr` ), e `unativeint` ( `System.UIntPtr` ).</span><span class="sxs-lookup"><span data-stu-id="91e5a-158">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="91e5a-159">Os tipos de ponto flutuante básicos são `float` ( `System.Double` ) e `float32` ( `System.Single` ).</span><span class="sxs-lookup"><span data-stu-id="91e5a-159">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="91e5a-160">A largura opcional é um inteiro que indica a largura mínima do resultado.</span><span class="sxs-lookup"><span data-stu-id="91e5a-160">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="91e5a-161">Por exemplo, `%6d` imprime um inteiro, prefixando-o com espaços para preencher pelo menos seis caracteres.</span><span class="sxs-lookup"><span data-stu-id="91e5a-161">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least six characters.</span></span> <span data-ttu-id="91e5a-162">Se Width for `*` , será usado um argumento inteiro extra para especificar a largura correspondente.</span><span class="sxs-lookup"><span data-stu-id="91e5a-162">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="91e5a-163">Os sinalizadores válidos são:</span><span class="sxs-lookup"><span data-stu-id="91e5a-163">Valid flags are:</span></span>

| <span data-ttu-id="91e5a-164">Sinalizador</span><span class="sxs-lookup"><span data-stu-id="91e5a-164">Flag</span></span>   | <span data-ttu-id="91e5a-165">Efeito</span><span class="sxs-lookup"><span data-stu-id="91e5a-165">Effect</span></span>        | <span data-ttu-id="91e5a-166">Comentários</span><span class="sxs-lookup"><span data-stu-id="91e5a-166">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="91e5a-167">Adicionar zeros em vez de espaços para criar a largura necessária</span><span class="sxs-lookup"><span data-stu-id="91e5a-167">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="91e5a-168">Justificar à esquerda o resultado dentro da largura especificada</span><span class="sxs-lookup"><span data-stu-id="91e5a-168">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="91e5a-169">Adicionar um `+` caractere se o número for positivo (para corresponder a um `-` sinal para negativos)</span><span class="sxs-lookup"><span data-stu-id="91e5a-169">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="91e5a-170">caractere de espaço</span><span class="sxs-lookup"><span data-stu-id="91e5a-170">space character</span></span> | <span data-ttu-id="91e5a-171">Adicione um espaço extra se o número for positivo (para corresponder a um sinal "-" para negativos)</span><span class="sxs-lookup"><span data-stu-id="91e5a-171">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="91e5a-172">O `#` sinalizador printf é inválido e um erro de tempo de compilação será relatado se for usado.</span><span class="sxs-lookup"><span data-stu-id="91e5a-172">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="91e5a-173">Os valores são formatados usando cultura invariável.</span><span class="sxs-lookup"><span data-stu-id="91e5a-173">Values are formatted using invariant culture.</span></span> <span data-ttu-id="91e5a-174">As configurações de cultura são irrelevantes para a `printf` formatação, exceto quando afetam os resultados `%O` e a `%A` formatação.</span><span class="sxs-lookup"><span data-stu-id="91e5a-174">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="91e5a-175">Para obter mais informações, consulte [formatação de texto sem formatação estruturada](plaintext-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="91e5a-175">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="91e5a-176">`%A`formatação</span><span class="sxs-lookup"><span data-stu-id="91e5a-176">`%A` formatting</span></span>

<span data-ttu-id="91e5a-177">O `%A` especificador de formato é usado para formatar valores de uma maneira legível por humanos e também pode ser útil para relatar informações de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="91e5a-177">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="91e5a-178">Valores primitivos</span><span class="sxs-lookup"><span data-stu-id="91e5a-178">Primitive values</span></span>

<span data-ttu-id="91e5a-179">Ao formatar texto sem formatação usando o `%A` especificador, os valores numéricos de F # são formatados com seu sufixo e cultura invariável.</span><span class="sxs-lookup"><span data-stu-id="91e5a-179">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="91e5a-180">Os valores de ponto flutuante são formatados usando 10 locais de precisão de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="91e5a-180">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="91e5a-181">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-181">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="91e5a-182">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-182">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="91e5a-183">Ao usar o `%A` especificador, as cadeias de caracteres são formatadas usando aspas.</span><span class="sxs-lookup"><span data-stu-id="91e5a-183">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="91e5a-184">Os códigos de escape não são adicionados e, em vez disso, os caracteres brutos são impressos.</span><span class="sxs-lookup"><span data-stu-id="91e5a-184">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="91e5a-185">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-185">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="91e5a-186">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-186">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="91e5a-187">Valores do .NET</span><span class="sxs-lookup"><span data-stu-id="91e5a-187">.NET values</span></span>

<span data-ttu-id="91e5a-188">Ao formatar texto sem formatação usando o `%A` especificador, os objetos não F # .NET são formatados com `x.ToString()` o uso das configurações padrão do .NET fornecido pelo `System.Globalization.CultureInfo.CurrentCulture` e pelo `System.Globalization.CultureInfo.CurrentUICulture` .</span><span class="sxs-lookup"><span data-stu-id="91e5a-188">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="91e5a-189">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-189">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="91e5a-190">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-190">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="91e5a-191">Valores estruturados</span><span class="sxs-lookup"><span data-stu-id="91e5a-191">Structured values</span></span>

<span data-ttu-id="91e5a-192">Ao formatar texto sem formatação usando o `%A` especificador, o recuo de bloco é usado para listas e tuplas F #.</span><span class="sxs-lookup"><span data-stu-id="91e5a-192">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="91e5a-193">Isso é mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="91e5a-193">This shown in the previous example.</span></span>
<span data-ttu-id="91e5a-194">A estrutura de matrizes também é usada, incluindo matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="91e5a-194">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="91e5a-195">Matrizes unidimensionais são mostradas com a `[| ... |]` sintaxe.</span><span class="sxs-lookup"><span data-stu-id="91e5a-195">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="91e5a-196">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-196">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="91e5a-197">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-197">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="91e5a-198">A largura de impressão padrão é 80.</span><span class="sxs-lookup"><span data-stu-id="91e5a-198">The default print width is 80.</span></span>  <span data-ttu-id="91e5a-199">Essa largura pode ser personalizada usando uma largura de impressão no especificador de formato.</span><span class="sxs-lookup"><span data-stu-id="91e5a-199">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="91e5a-200">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-200">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="91e5a-201">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-201">produces</span></span>

```console
[|(1, 1);
  (2, 4);
  (3, 9);
  (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4);
  (3, 9); (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
```

<span data-ttu-id="91e5a-202">A especificação de uma largura de impressão de 0 resulta na não utilização da largura de impressão.</span><span class="sxs-lookup"><span data-stu-id="91e5a-202">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="91e5a-203">Uma única linha de texto resultará, exceto onde as cadeias de caracteres inseridas na saída contiverem quebras de linha.</span><span class="sxs-lookup"><span data-stu-id="91e5a-203">A single line of text will result, except where embedded strings in the output contain line breaks.</span></span>  <span data-ttu-id="91e5a-204">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="91e5a-204">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

<span data-ttu-id="91e5a-205">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-205">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="91e5a-206">Um limite de profundidade de 4 é usado para valores de Sequence ( `IEnumerable` ), que são mostrados como `seq { ...}` .</span><span class="sxs-lookup"><span data-stu-id="91e5a-206">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="91e5a-207">Um limite de profundidade de 100 é usado para valores de lista e matriz.</span><span class="sxs-lookup"><span data-stu-id="91e5a-207">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="91e5a-208">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-208">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="91e5a-209">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-209">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="91e5a-210">O recuo de bloco também é usado para a estrutura de valores públicos de registro e União.</span><span class="sxs-lookup"><span data-stu-id="91e5a-210">Block indentation is also used for the structure of public record and union values.</span></span> <span data-ttu-id="91e5a-211">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-211">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="91e5a-212">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-212">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="91e5a-213">Se `%+A` for usado, a estrutura privada de registros e uniões também será revelada com o uso de reflexão.</span><span class="sxs-lookup"><span data-stu-id="91e5a-213">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="91e5a-214">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="91e5a-214">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="91e5a-215">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-215">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="91e5a-216">Valores grandes, cíclicos ou profundamente aninhados</span><span class="sxs-lookup"><span data-stu-id="91e5a-216">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="91e5a-217">Os valores estruturados grandes são formatados para uma contagem máxima de nós de objeto geral de 10000.</span><span class="sxs-lookup"><span data-stu-id="91e5a-217">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="91e5a-218">Valores profundamente aninhados são formatados para uma profundidade de 100.</span><span class="sxs-lookup"><span data-stu-id="91e5a-218">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="91e5a-219">Em ambos os casos, `...` é usado para Elide parte da saída.</span><span class="sxs-lookup"><span data-stu-id="91e5a-219">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="91e5a-220">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-220">For example,</span></span>

```fsharp
type Tree =
    | Tip
    | Node of Tree * Tree

let rec make n =
    if n = 0 then
        Tip
    else
        Node(Tip, make (n-1))

printfn "%A" (make 1000)
```

<span data-ttu-id="91e5a-221">produz uma saída grande com algumas partes omitido:</span><span class="sxs-lookup"><span data-stu-id="91e5a-221">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="91e5a-222">Os ciclos são detectados nos grafos de objeto e `...` são usados em locais onde os ciclos são detectados.</span><span class="sxs-lookup"><span data-stu-id="91e5a-222">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="91e5a-223">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="91e5a-223">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="91e5a-224">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-224">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="91e5a-225">Valores lentos, nulos e de função</span><span class="sxs-lookup"><span data-stu-id="91e5a-225">Lazy, null, and function values</span></span>

<span data-ttu-id="91e5a-226">Valores lentos são impressos como `Value is not created` ou texto equivalente quando o valor ainda não foi avaliado.</span><span class="sxs-lookup"><span data-stu-id="91e5a-226">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="91e5a-227">Valores nulos são impressos como `null` a menos que o tipo estático do valor seja determinado para ser um tipo de União em que `null` é uma representação permitida.</span><span class="sxs-lookup"><span data-stu-id="91e5a-227">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted representation.</span></span>

<span data-ttu-id="91e5a-228">Os valores da função F # são impressos como seu nome de fechamento gerado internamente, por exemplo, `<fun:it@43-7>` .</span><span class="sxs-lookup"><span data-stu-id="91e5a-228">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="91e5a-229">Personalizar a formatação de texto sem formatação com`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="91e5a-229">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="91e5a-230">Ao usar o `%A` especificador, a presença do `StructuredFormatDisplay` atributo em declarações de tipo é respeitada.</span><span class="sxs-lookup"><span data-stu-id="91e5a-230">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="91e5a-231">Isso pode ser usado para especificar o texto e a propriedade substitutos para exibir um valor.</span><span class="sxs-lookup"><span data-stu-id="91e5a-231">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="91e5a-232">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-232">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="91e5a-233">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-233">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="91e5a-234">Personalizar a formatação de texto sem formatação substituindo`ToString`</span><span class="sxs-lookup"><span data-stu-id="91e5a-234">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="91e5a-235">A implementação padrão de `ToString` é observável na programação em F #.</span><span class="sxs-lookup"><span data-stu-id="91e5a-235">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="91e5a-236">Geralmente, os resultados padrão não são adequados para uso em exibição de informações voltadas para o programador ou saída do usuário e, como resultado, é comum substituir a implementação padrão.</span><span class="sxs-lookup"><span data-stu-id="91e5a-236">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="91e5a-237">Por padrão, os tipos de registro e União F # substituem a implementação de `ToString` por uma implementação que usa o `sprintf "%+A"` .</span><span class="sxs-lookup"><span data-stu-id="91e5a-237">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="91e5a-238">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-238">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="91e5a-239">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-239">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="91e5a-240">Para tipos de classe, nenhuma implementação padrão de `ToString` é fornecida e o padrão .net é usado, o que relata o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="91e5a-240">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="91e5a-241">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91e5a-241">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="91e5a-242">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-242">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="91e5a-243">Adicionar uma substituição para `ToString` pode dar melhor formatação.</span><span class="sxs-lookup"><span data-stu-id="91e5a-243">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="91e5a-244">grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-244">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="91e5a-245">F# Interativo impressão estruturada</span><span class="sxs-lookup"><span data-stu-id="91e5a-245">F# Interactive structured printing</span></span>

<span data-ttu-id="91e5a-246">F# Interativo ( `dotnet fsi` ) usa uma versão estendida da formatação de texto sem formatação estruturada para relatar valores e permite personalização adicional.</span><span class="sxs-lookup"><span data-stu-id="91e5a-246">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="91e5a-247">Para obter mais informações, consulte [F# interativo](fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="91e5a-247">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="91e5a-248">Personalizar exibições de depuração</span><span class="sxs-lookup"><span data-stu-id="91e5a-248">Customize debug displays</span></span>

<span data-ttu-id="91e5a-249">Os depuradores para .NET respeitam o uso de atributos como `DebuggerDisplay` e `DebuggerTypeProxy` , e eles afetam a exibição estruturada de objetos nas janelas de inspeção do depurador.</span><span class="sxs-lookup"><span data-stu-id="91e5a-249">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="91e5a-250">O compilador F # gerou automaticamente esses atributos para tipos de registro e União discriminados, mas não tipos de classe, interface ou struct.</span><span class="sxs-lookup"><span data-stu-id="91e5a-250">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="91e5a-251">Esses atributos são ignorados na formatação de texto sem formatação F #, mas pode ser útil implementar esses métodos para melhorar as exibições ao depurar tipos F #.</span><span class="sxs-lookup"><span data-stu-id="91e5a-251">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="91e5a-252">Confira também</span><span class="sxs-lookup"><span data-stu-id="91e5a-252">See also</span></span>

- [<span data-ttu-id="91e5a-253">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="91e5a-253">Strings</span></span>](strings.md)
- [<span data-ttu-id="91e5a-254">Grava</span><span class="sxs-lookup"><span data-stu-id="91e5a-254">Records</span></span>](records.md)
- [<span data-ttu-id="91e5a-255">Uniões Discriminadas</span><span class="sxs-lookup"><span data-stu-id="91e5a-255">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="91e5a-256">F# Interativo</span><span class="sxs-lookup"><span data-stu-id="91e5a-256">F# Interactive</span></span>](fsharp-interactive-options.md)
