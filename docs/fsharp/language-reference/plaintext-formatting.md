---
title: Formatação de texto sem formatação
description: 'Saiba como usar printf e outra formatação de texto sem formatação em aplicativos e scripts em F #.'
ms.date: 07/22/2020
ms.openlocfilehash: 90a861736dae69dfbc199a19e24f587c42404737
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063777"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="83cce-103">Formatação de texto sem formatação</span><span class="sxs-lookup"><span data-stu-id="83cce-103">Plain text formatting</span></span>

<span data-ttu-id="83cce-104">O F # dá suporte à formatação verificada por tipo de texto sem formatação usando as `printf` `printfn` funções relacionadas,, e `sprintf` .</span><span class="sxs-lookup"><span data-stu-id="83cce-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="83cce-105">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="83cce-106">fornece a saída</span><span class="sxs-lookup"><span data-stu-id="83cce-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="83cce-107">O F # também permite que valores estruturados sejam formatados como texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="83cce-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="83cce-108">Por exemplo, considere o exemplo a seguir que formata a saída como uma exibição matricial de tuplas.</span><span class="sxs-lookup"><span data-stu-id="83cce-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="83cce-109">A formatação de texto simples estruturado é ativada quando você usa o `%A` formato em `printf` cadeias de caracteres de formatação.</span><span class="sxs-lookup"><span data-stu-id="83cce-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="83cce-110">Ele também é ativado ao Formatar a saída de valores em F # Interactive, em que a saída inclui informações extras e também é personalizável.</span><span class="sxs-lookup"><span data-stu-id="83cce-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="83cce-111">A formatação de texto sem formatação também é observável por meio de todas as chamadas para `x.ToString()` valores de União e registro em F #, incluindo aquelas que ocorrem implicitamente na depuração, no registro em log e em outras ferramentas.</span><span class="sxs-lookup"><span data-stu-id="83cce-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="83cce-112">Verificação de `printf` cadeias de caracteres de formato</span><span class="sxs-lookup"><span data-stu-id="83cce-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="83cce-113">Um erro de tempo de compilação será relatado se uma `printf` função de formatação for usada com um argumento que não corresponda aos especificadores de formato printf na cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="83cce-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="83cce-114">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="83cce-115">fornece a saída</span><span class="sxs-lookup"><span data-stu-id="83cce-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="83cce-116">Falando tecnicamente, ao usar `printf` e outras funções relacionadas, uma regra especial no compilador F # verifica o literal de cadeia de caracteres passado como a cadeia de caracteres de formato, garantindo que os argumentos subsequentes aplicados sejam do tipo correto para corresponder aos especificadores de formato usados.</span><span class="sxs-lookup"><span data-stu-id="83cce-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="83cce-117">Especificadores de formato para`printf`</span><span class="sxs-lookup"><span data-stu-id="83cce-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="83cce-118">As especificações de formato para `printf` formatos são cadeias de caracteres com `%` marcadores que indicam o formato.</span><span class="sxs-lookup"><span data-stu-id="83cce-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="83cce-119">Espaços reservados de formato consistem `%[flags][width][.precision][type]` em onde o tipo é interpretado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="83cce-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="83cce-120">Especificador de formato</span><span class="sxs-lookup"><span data-stu-id="83cce-120">Format specifier</span></span>   | <span data-ttu-id="83cce-121">Tipo (s)</span><span class="sxs-lookup"><span data-stu-id="83cce-121">Type(s)</span></span>        | <span data-ttu-id="83cce-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="83cce-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="83cce-123">bool</span><span class="sxs-lookup"><span data-stu-id="83cce-123">bool</span></span>      | <span data-ttu-id="83cce-124">Formatado como `true` ou`false`</span><span class="sxs-lookup"><span data-stu-id="83cce-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="83cce-125">string</span><span class="sxs-lookup"><span data-stu-id="83cce-125">string</span></span>    | <span data-ttu-id="83cce-126">Formatado como seu conteúdo sem escape</span><span class="sxs-lookup"><span data-stu-id="83cce-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="83cce-127">char</span><span class="sxs-lookup"><span data-stu-id="83cce-127">char</span></span>      | <span data-ttu-id="83cce-128">Formatado como o literal de caractere</span><span class="sxs-lookup"><span data-stu-id="83cce-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="83cce-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="83cce-129">`%d`, `%i`</span></span>         | <span data-ttu-id="83cce-130">um tipo inteiro básico</span><span class="sxs-lookup"><span data-stu-id="83cce-130">a basic integer type</span></span> | <span data-ttu-id="83cce-131">Formatado como um inteiro decimal, assinado se o tipo de inteiro básico for assinado</span><span class="sxs-lookup"><span data-stu-id="83cce-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="83cce-132">um tipo inteiro básico</span><span class="sxs-lookup"><span data-stu-id="83cce-132">a basic integer type</span></span> | <span data-ttu-id="83cce-133">Formatado como um inteiro decimal sem sinal</span><span class="sxs-lookup"><span data-stu-id="83cce-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="83cce-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="83cce-134">`%x`, `%X`</span></span>         | <span data-ttu-id="83cce-135">um tipo inteiro básico</span><span class="sxs-lookup"><span data-stu-id="83cce-135">a basic integer type</span></span> | <span data-ttu-id="83cce-136">Formatado como um número hexadecimal não assinado (a-f ou A-F para dígitos hexadecimais, respectivamente)</span><span class="sxs-lookup"><span data-stu-id="83cce-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="83cce-137">um tipo inteiro básico</span><span class="sxs-lookup"><span data-stu-id="83cce-137">a basic integer type</span></span> | <span data-ttu-id="83cce-138">Formatado como um número octal não assinado</span><span class="sxs-lookup"><span data-stu-id="83cce-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="83cce-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="83cce-139">`%e`, `%E`</span></span>         | <span data-ttu-id="83cce-140">um tipo de ponto flutuante básico</span><span class="sxs-lookup"><span data-stu-id="83cce-140">a basic floating point type</span></span> | <span data-ttu-id="83cce-141">Formatado como um valor assinado, tendo o formato `[-]d.dddde[sign]ddd` em que d é um único dígito decimal, dddd é um ou mais dígitos decimais, o DDD tem exatamente três dígitos decimais e o sinal é `+` ou`-`</span><span class="sxs-lookup"><span data-stu-id="83cce-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="83cce-142">um tipo de ponto flutuante básico</span><span class="sxs-lookup"><span data-stu-id="83cce-142">a basic floating point type</span></span> | <span data-ttu-id="83cce-143">Formatado como um valor assinado com o formulário `[-]dddd.dddd` , em que `dddd` é um ou mais dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="83cce-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="83cce-144">O número de dígitos antes do ponto decimal depende da magnitude do número, e o número de dígitos após o ponto decimal depende da precisão solicitada.</span><span class="sxs-lookup"><span data-stu-id="83cce-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="83cce-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="83cce-145">`%g`, `%G`</span></span> | <span data-ttu-id="83cce-146">um tipo de ponto flutuante básico</span><span class="sxs-lookup"><span data-stu-id="83cce-146">a basic floating point type</span></span> |  <span data-ttu-id="83cce-147">Formatado usando como um valor assinado, impresso em `%f` ou `%e` formato, o que for mais compacto para o valor e a precisão especificados.</span><span class="sxs-lookup"><span data-stu-id="83cce-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="83cce-148">um `System.Decimal` valor</span><span class="sxs-lookup"><span data-stu-id="83cce-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="83cce-149">Formatado usando o `"G"` especificador de formato para`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="83cce-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="83cce-150">qualquer valor</span><span class="sxs-lookup"><span data-stu-id="83cce-150">any value</span></span>  |   <span data-ttu-id="83cce-151">Formatado por Boxing o objeto e chamando seu `System.Object.ToString()` método</span><span class="sxs-lookup"><span data-stu-id="83cce-151">Formatted by boxing the object and calling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="83cce-152">qualquer valor</span><span class="sxs-lookup"><span data-stu-id="83cce-152">any value</span></span>  |   <span data-ttu-id="83cce-153">Formatado usando a [formatação de texto simples estruturado](plaintext-formatting.md) com as configurações de layout padrão</span><span class="sxs-lookup"><span data-stu-id="83cce-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="83cce-154">qualquer valor</span><span class="sxs-lookup"><span data-stu-id="83cce-154">any value</span></span>  |   <span data-ttu-id="83cce-155">Requer dois argumentos: uma função de formatação que aceita um parâmetro de contexto e o valor, e o valor específico a ser impresso</span><span class="sxs-lookup"><span data-stu-id="83cce-155">Requires two arguments: a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="83cce-156">qualquer valor</span><span class="sxs-lookup"><span data-stu-id="83cce-156">any value</span></span>  |   <span data-ttu-id="83cce-157">Requer um argumento: uma função de formatação que aceita um parâmetro de contexto que gera ou retorna o texto apropriado</span><span class="sxs-lookup"><span data-stu-id="83cce-157">Requires one argument: a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |
| `%%` | <span data-ttu-id="83cce-158">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="83cce-158">(none)</span></span>  |   <span data-ttu-id="83cce-159">Não requer argumentos e imprime um sinal de porcentagem simples:`%`</span><span class="sxs-lookup"><span data-stu-id="83cce-159">Requires no arguments and prints a plain percent sign: `%`</span></span> |

<span data-ttu-id="83cce-160">Os tipos de inteiro básicos são `byte` ( `System.Byte` ), `sbyte` ( `System.SByte` ), `int16` ( `System.Int16` ), `uint16` ( `System.UInt16` ), `int32` ( `System.Int32` ), `uint32` ( `System.UInt32` ), `int64` () `System.Int64` , `uint64` ( `System.UInt64` ), `nativeint` ( `System.IntPtr` ), e `unativeint` ( `System.UIntPtr` ).</span><span class="sxs-lookup"><span data-stu-id="83cce-160">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="83cce-161">Os tipos de ponto flutuante básicos são `float` ( `System.Double` ) e `float32` ( `System.Single` ).</span><span class="sxs-lookup"><span data-stu-id="83cce-161">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="83cce-162">A largura opcional é um inteiro que indica a largura mínima do resultado.</span><span class="sxs-lookup"><span data-stu-id="83cce-162">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="83cce-163">Por exemplo, `%6d` imprime um inteiro, prefixando-o com espaços para preencher pelo menos seis caracteres.</span><span class="sxs-lookup"><span data-stu-id="83cce-163">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least six characters.</span></span> <span data-ttu-id="83cce-164">Se Width for `*` , será usado um argumento inteiro extra para especificar a largura correspondente.</span><span class="sxs-lookup"><span data-stu-id="83cce-164">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="83cce-165">Os sinalizadores válidos são:</span><span class="sxs-lookup"><span data-stu-id="83cce-165">Valid flags are:</span></span>

| <span data-ttu-id="83cce-166">Sinalizador</span><span class="sxs-lookup"><span data-stu-id="83cce-166">Flag</span></span>   | <span data-ttu-id="83cce-167">Efeito</span><span class="sxs-lookup"><span data-stu-id="83cce-167">Effect</span></span>        | <span data-ttu-id="83cce-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="83cce-168">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="83cce-169">Adicionar zeros em vez de espaços para criar a largura necessária</span><span class="sxs-lookup"><span data-stu-id="83cce-169">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="83cce-170">Justificar à esquerda o resultado dentro da largura especificada</span><span class="sxs-lookup"><span data-stu-id="83cce-170">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="83cce-171">Adicionar um `+` caractere se o número for positivo (para corresponder a um `-` sinal para negativos)</span><span class="sxs-lookup"><span data-stu-id="83cce-171">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="83cce-172">caractere de espaço</span><span class="sxs-lookup"><span data-stu-id="83cce-172">space character</span></span> | <span data-ttu-id="83cce-173">Adicione um espaço extra se o número for positivo (para corresponder a um sinal "-" para negativos)</span><span class="sxs-lookup"><span data-stu-id="83cce-173">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="83cce-174">O `#` sinalizador printf é inválido e um erro de tempo de compilação será relatado se for usado.</span><span class="sxs-lookup"><span data-stu-id="83cce-174">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="83cce-175">Os valores são formatados usando cultura invariável.</span><span class="sxs-lookup"><span data-stu-id="83cce-175">Values are formatted using invariant culture.</span></span> <span data-ttu-id="83cce-176">As configurações de cultura são irrelevantes para a `printf` formatação, exceto quando afetam os resultados `%O` e a `%A` formatação.</span><span class="sxs-lookup"><span data-stu-id="83cce-176">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="83cce-177">Para obter mais informações, consulte [formatação de texto sem formatação estruturada](plaintext-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="83cce-177">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="83cce-178">`%A`formatação</span><span class="sxs-lookup"><span data-stu-id="83cce-178">`%A` formatting</span></span>

<span data-ttu-id="83cce-179">O `%A` especificador de formato é usado para formatar valores de uma maneira legível por humanos e também pode ser útil para relatar informações de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="83cce-179">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="83cce-180">Valores primitivos</span><span class="sxs-lookup"><span data-stu-id="83cce-180">Primitive values</span></span>

<span data-ttu-id="83cce-181">Ao formatar texto sem formatação usando o `%A` especificador, os valores numéricos de F # são formatados com seu sufixo e cultura invariável.</span><span class="sxs-lookup"><span data-stu-id="83cce-181">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="83cce-182">Os valores de ponto flutuante são formatados usando 10 locais de precisão de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="83cce-182">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="83cce-183">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-183">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="83cce-184">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-184">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="83cce-185">Ao usar o `%A` especificador, as cadeias de caracteres são formatadas usando aspas.</span><span class="sxs-lookup"><span data-stu-id="83cce-185">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="83cce-186">Os códigos de escape não são adicionados e, em vez disso, os caracteres brutos são impressos.</span><span class="sxs-lookup"><span data-stu-id="83cce-186">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="83cce-187">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-187">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="83cce-188">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-188">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="83cce-189">Valores do .NET</span><span class="sxs-lookup"><span data-stu-id="83cce-189">.NET values</span></span>

<span data-ttu-id="83cce-190">Ao formatar texto sem formatação usando o `%A` especificador, os objetos não F # .NET são formatados com `x.ToString()` o uso das configurações padrão do .NET fornecido pelo `System.Globalization.CultureInfo.CurrentCulture` e pelo `System.Globalization.CultureInfo.CurrentUICulture` .</span><span class="sxs-lookup"><span data-stu-id="83cce-190">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="83cce-191">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-191">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="83cce-192">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-192">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="83cce-193">Valores estruturados</span><span class="sxs-lookup"><span data-stu-id="83cce-193">Structured values</span></span>

<span data-ttu-id="83cce-194">Ao formatar texto sem formatação usando o `%A` especificador, o recuo de bloco é usado para listas e tuplas F #.</span><span class="sxs-lookup"><span data-stu-id="83cce-194">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="83cce-195">Isso é mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="83cce-195">This shown in the previous example.</span></span>
<span data-ttu-id="83cce-196">A estrutura de matrizes também é usada, incluindo matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="83cce-196">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="83cce-197">Matrizes unidimensionais são mostradas com a `[| ... |]` sintaxe.</span><span class="sxs-lookup"><span data-stu-id="83cce-197">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="83cce-198">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-198">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="83cce-199">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-199">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="83cce-200">A largura de impressão padrão é 80.</span><span class="sxs-lookup"><span data-stu-id="83cce-200">The default print width is 80.</span></span>  <span data-ttu-id="83cce-201">Essa largura pode ser personalizada usando uma largura de impressão no especificador de formato.</span><span class="sxs-lookup"><span data-stu-id="83cce-201">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="83cce-202">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-202">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="83cce-203">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-203">produces</span></span>

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

<span data-ttu-id="83cce-204">A especificação de uma largura de impressão de 0 resulta na não utilização da largura de impressão.</span><span class="sxs-lookup"><span data-stu-id="83cce-204">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="83cce-205">Uma única linha de texto resultará, exceto onde as cadeias de caracteres inseridas na saída contiverem quebras de linha.</span><span class="sxs-lookup"><span data-stu-id="83cce-205">A single line of text will result, except where embedded strings in the output contain line breaks.</span></span>  <span data-ttu-id="83cce-206">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="83cce-206">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

<span data-ttu-id="83cce-207">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-207">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="83cce-208">Um limite de profundidade de 4 é usado para valores de Sequence ( `IEnumerable` ), que são mostrados como `seq { ...}` .</span><span class="sxs-lookup"><span data-stu-id="83cce-208">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="83cce-209">Um limite de profundidade de 100 é usado para valores de lista e matriz.</span><span class="sxs-lookup"><span data-stu-id="83cce-209">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="83cce-210">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-210">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="83cce-211">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-211">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="83cce-212">O recuo de bloco também é usado para a estrutura de valores públicos de registro e União.</span><span class="sxs-lookup"><span data-stu-id="83cce-212">Block indentation is also used for the structure of public record and union values.</span></span> <span data-ttu-id="83cce-213">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-213">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="83cce-214">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-214">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="83cce-215">Se `%+A` for usado, a estrutura privada de registros e uniões também será revelada com o uso de reflexão.</span><span class="sxs-lookup"><span data-stu-id="83cce-215">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="83cce-216">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="83cce-216">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="83cce-217">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-217">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="83cce-218">Valores grandes, cíclicos ou profundamente aninhados</span><span class="sxs-lookup"><span data-stu-id="83cce-218">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="83cce-219">Os valores estruturados grandes são formatados para uma contagem máxima de nós de objeto geral de 10000.</span><span class="sxs-lookup"><span data-stu-id="83cce-219">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="83cce-220">Valores profundamente aninhados são formatados para uma profundidade de 100.</span><span class="sxs-lookup"><span data-stu-id="83cce-220">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="83cce-221">Em ambos os casos, `...` é usado para Elide parte da saída.</span><span class="sxs-lookup"><span data-stu-id="83cce-221">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="83cce-222">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-222">For example,</span></span>

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

<span data-ttu-id="83cce-223">produz uma saída grande com algumas partes omitido:</span><span class="sxs-lookup"><span data-stu-id="83cce-223">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="83cce-224">Os ciclos são detectados nos grafos de objeto e `...` são usados em locais onde os ciclos são detectados.</span><span class="sxs-lookup"><span data-stu-id="83cce-224">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="83cce-225">Por exemplo</span><span class="sxs-lookup"><span data-stu-id="83cce-225">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="83cce-226">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-226">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="83cce-227">Valores lentos, nulos e de função</span><span class="sxs-lookup"><span data-stu-id="83cce-227">Lazy, null, and function values</span></span>

<span data-ttu-id="83cce-228">Valores lentos são impressos como `Value is not created` ou texto equivalente quando o valor ainda não foi avaliado.</span><span class="sxs-lookup"><span data-stu-id="83cce-228">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="83cce-229">Valores nulos são impressos como `null` a menos que o tipo estático do valor seja determinado para ser um tipo de União em que `null` é uma representação permitida.</span><span class="sxs-lookup"><span data-stu-id="83cce-229">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted representation.</span></span>

<span data-ttu-id="83cce-230">Os valores da função F # são impressos como seu nome de fechamento gerado internamente, por exemplo, `<fun:it@43-7>` .</span><span class="sxs-lookup"><span data-stu-id="83cce-230">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="83cce-231">Personalizar a formatação de texto sem formatação com`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="83cce-231">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="83cce-232">Ao usar o `%A` especificador, a presença do `StructuredFormatDisplay` atributo em declarações de tipo é respeitada.</span><span class="sxs-lookup"><span data-stu-id="83cce-232">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="83cce-233">Isso pode ser usado para especificar o texto e a propriedade substitutos para exibir um valor.</span><span class="sxs-lookup"><span data-stu-id="83cce-233">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="83cce-234">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="83cce-234">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="83cce-235">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-235">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="83cce-236">Personalizar a formatação de texto sem formatação substituindo`ToString`</span><span class="sxs-lookup"><span data-stu-id="83cce-236">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="83cce-237">A implementação padrão de `ToString` é observável na programação em F #.</span><span class="sxs-lookup"><span data-stu-id="83cce-237">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="83cce-238">Geralmente, os resultados padrão não são adequados para uso em exibição de informações voltadas para o programador ou saída do usuário e, como resultado, é comum substituir a implementação padrão.</span><span class="sxs-lookup"><span data-stu-id="83cce-238">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="83cce-239">Por padrão, os tipos de registro e União F # substituem a implementação de `ToString` por uma implementação que usa o `sprintf "%+A"` .</span><span class="sxs-lookup"><span data-stu-id="83cce-239">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="83cce-240">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-240">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="83cce-241">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-241">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="83cce-242">Para tipos de classe, nenhuma implementação padrão de `ToString` é fornecida e o padrão .net é usado, o que relata o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="83cce-242">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="83cce-243">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="83cce-243">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="83cce-244">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-244">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="83cce-245">Adicionar uma substituição para `ToString` pode dar melhor formatação.</span><span class="sxs-lookup"><span data-stu-id="83cce-245">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="83cce-246">grava</span><span class="sxs-lookup"><span data-stu-id="83cce-246">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="83cce-247">F# Interativo impressão estruturada</span><span class="sxs-lookup"><span data-stu-id="83cce-247">F# Interactive structured printing</span></span>

<span data-ttu-id="83cce-248">F# Interativo ( `dotnet fsi` ) usa uma versão estendida da formatação de texto sem formatação estruturada para relatar valores e permite personalização adicional.</span><span class="sxs-lookup"><span data-stu-id="83cce-248">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="83cce-249">Para obter mais informações, consulte [F# interativo](fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="83cce-249">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="83cce-250">Personalizar exibições de depuração</span><span class="sxs-lookup"><span data-stu-id="83cce-250">Customize debug displays</span></span>

<span data-ttu-id="83cce-251">Os depuradores para .NET respeitam o uso de atributos como `DebuggerDisplay` e `DebuggerTypeProxy` , e eles afetam a exibição estruturada de objetos nas janelas de inspeção do depurador.</span><span class="sxs-lookup"><span data-stu-id="83cce-251">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="83cce-252">O compilador F # gerou automaticamente esses atributos para tipos de registro e União discriminados, mas não tipos de classe, interface ou struct.</span><span class="sxs-lookup"><span data-stu-id="83cce-252">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="83cce-253">Esses atributos são ignorados na formatação de texto sem formatação F #, mas pode ser útil implementar esses métodos para melhorar as exibições ao depurar tipos F #.</span><span class="sxs-lookup"><span data-stu-id="83cce-253">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="83cce-254">Confira também</span><span class="sxs-lookup"><span data-stu-id="83cce-254">See also</span></span>

- [<span data-ttu-id="83cce-255">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="83cce-255">Strings</span></span>](strings.md)
- [<span data-ttu-id="83cce-256">Registros</span><span class="sxs-lookup"><span data-stu-id="83cce-256">Records</span></span>](records.md)
- [<span data-ttu-id="83cce-257">Uniões discriminadas</span><span class="sxs-lookup"><span data-stu-id="83cce-257">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="83cce-258">F# Interativo</span><span class="sxs-lookup"><span data-stu-id="83cce-258">F# Interactive</span></span>](fsharp-interactive-options.md)
