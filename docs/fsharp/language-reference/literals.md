---
title: Literais
description: Saiba mais sobre os tipos de literais no F# linguagem de programação.
ms.date: 02/08/2019
ms.openlocfilehash: 032bc82d222cd34e7ac62e42ee4394c97d975b2e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490981"
---
# <a name="literals"></a><span data-ttu-id="79c1c-103">Literais</span><span class="sxs-lookup"><span data-stu-id="79c1c-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="79c1c-104">Os links de referência de API neste artigo você será levado ao MSDN (por enquanto).</span><span class="sxs-lookup"><span data-stu-id="79c1c-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="79c1c-105">Este tópico fornece uma tabela que mostra como especificar o tipo de um literal em F#.</span><span class="sxs-lookup"><span data-stu-id="79c1c-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="79c1c-106">Tipos literais</span><span class="sxs-lookup"><span data-stu-id="79c1c-106">Literal Types</span></span>

<span data-ttu-id="79c1c-107">A tabela a seguir mostra os tipos de literais no F#.</span><span class="sxs-lookup"><span data-stu-id="79c1c-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="79c1c-108">Caracteres que representam dígitos em notação hexadecimal não diferenciam maiusculas de minúsculas; caracteres que identifica o tipo diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="79c1c-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="79c1c-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="79c1c-109">Type</span></span>|<span data-ttu-id="79c1c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="79c1c-110">Description</span></span>|<span data-ttu-id="79c1c-111">Prefixo ou sufixo</span><span class="sxs-lookup"><span data-stu-id="79c1c-111">Suffix or prefix</span></span>|<span data-ttu-id="79c1c-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="79c1c-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="79c1c-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="79c1c-113">sbyte</span></span>|<span data-ttu-id="79c1c-114">inteiro com sinal de 8 bits</span><span class="sxs-lookup"><span data-stu-id="79c1c-114">signed 8-bit integer</span></span>|<span data-ttu-id="79c1c-115">y</span><span class="sxs-lookup"><span data-stu-id="79c1c-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="79c1c-116">byte</span><span class="sxs-lookup"><span data-stu-id="79c1c-116">byte</span></span>|<span data-ttu-id="79c1c-117">número de natural de 8 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="79c1c-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="79c1c-118">uy</span><span class="sxs-lookup"><span data-stu-id="79c1c-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="79c1c-119">int16</span><span class="sxs-lookup"><span data-stu-id="79c1c-119">int16</span></span>|<span data-ttu-id="79c1c-120">inteiro com sinal de 16 bits</span><span class="sxs-lookup"><span data-stu-id="79c1c-120">signed 16-bit integer</span></span>|<span data-ttu-id="79c1c-121">s</span><span class="sxs-lookup"><span data-stu-id="79c1c-121">s</span></span>|`86s`|
|<span data-ttu-id="79c1c-122">uint16</span><span class="sxs-lookup"><span data-stu-id="79c1c-122">uint16</span></span>|<span data-ttu-id="79c1c-123">número de natural de 16 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="79c1c-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="79c1c-124">us</span><span class="sxs-lookup"><span data-stu-id="79c1c-124">us</span></span>|`86us`|
|<span data-ttu-id="79c1c-125">int</span><span class="sxs-lookup"><span data-stu-id="79c1c-125">int</span></span><br /><br /><span data-ttu-id="79c1c-126">int32</span><span class="sxs-lookup"><span data-stu-id="79c1c-126">int32</span></span>|<span data-ttu-id="79c1c-127">inteiro com sinal de 32 bits</span><span class="sxs-lookup"><span data-stu-id="79c1c-127">signed 32-bit integer</span></span>|<span data-ttu-id="79c1c-128">l ou none</span><span class="sxs-lookup"><span data-stu-id="79c1c-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="79c1c-129">uint</span><span class="sxs-lookup"><span data-stu-id="79c1c-129">uint</span></span><br /><br /><span data-ttu-id="79c1c-130">uint32</span><span class="sxs-lookup"><span data-stu-id="79c1c-130">uint32</span></span>|<span data-ttu-id="79c1c-131">número de natural de 32 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="79c1c-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="79c1c-132">u ou ul</span><span class="sxs-lookup"><span data-stu-id="79c1c-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="79c1c-133">nativeint</span><span class="sxs-lookup"><span data-stu-id="79c1c-133">nativeint</span></span>|<span data-ttu-id="79c1c-134">ponteiro nativo para um número natural assinado</span><span class="sxs-lookup"><span data-stu-id="79c1c-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="79c1c-135">n</span><span class="sxs-lookup"><span data-stu-id="79c1c-135">n</span></span>|`123n`|
|<span data-ttu-id="79c1c-136">unativeint</span><span class="sxs-lookup"><span data-stu-id="79c1c-136">unativeint</span></span>|<span data-ttu-id="79c1c-137">ponteiro nativo como um número natural sem sinal</span><span class="sxs-lookup"><span data-stu-id="79c1c-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="79c1c-138">Cancelar</span><span class="sxs-lookup"><span data-stu-id="79c1c-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="79c1c-139">int64</span><span class="sxs-lookup"><span data-stu-id="79c1c-139">int64</span></span>|<span data-ttu-id="79c1c-140">inteiro com sinal de 64 bits</span><span class="sxs-lookup"><span data-stu-id="79c1c-140">signed 64-bit integer</span></span>|<span data-ttu-id="79c1c-141">L</span><span class="sxs-lookup"><span data-stu-id="79c1c-141">L</span></span>|`86L`|
|<span data-ttu-id="79c1c-142">uint64</span><span class="sxs-lookup"><span data-stu-id="79c1c-142">uint64</span></span>|<span data-ttu-id="79c1c-143">número de natural de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="79c1c-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="79c1c-144">UL</span><span class="sxs-lookup"><span data-stu-id="79c1c-144">UL</span></span>|`86UL`|
|<span data-ttu-id="79c1c-145">simples, float32</span><span class="sxs-lookup"><span data-stu-id="79c1c-145">single, float32</span></span>|<span data-ttu-id="79c1c-146">número de ponto flutuante de 32 bits</span><span class="sxs-lookup"><span data-stu-id="79c1c-146">32-bit floating point number</span></span>|<span data-ttu-id="79c1c-147">F ou f</span><span class="sxs-lookup"><span data-stu-id="79c1c-147">F or f</span></span>|<span data-ttu-id="79c1c-148">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="79c1c-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="79c1c-149">LF</span><span class="sxs-lookup"><span data-stu-id="79c1c-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="79c1c-150">float; Double</span><span class="sxs-lookup"><span data-stu-id="79c1c-150">float; double</span></span>|<span data-ttu-id="79c1c-151">número de ponto flutuante de 64 bits</span><span class="sxs-lookup"><span data-stu-id="79c1c-151">64-bit floating point number</span></span>|<span data-ttu-id="79c1c-152">nenhum</span><span class="sxs-lookup"><span data-stu-id="79c1c-152">none</span></span>|<span data-ttu-id="79c1c-153">`4.14`, `2.3E+32` ou `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="79c1c-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="79c1c-154">LF</span><span class="sxs-lookup"><span data-stu-id="79c1c-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="79c1c-155">bigint</span><span class="sxs-lookup"><span data-stu-id="79c1c-155">bigint</span></span>|<span data-ttu-id="79c1c-156">inteiro não limitado a representação de 64 bits</span><span class="sxs-lookup"><span data-stu-id="79c1c-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="79c1c-157">I</span><span class="sxs-lookup"><span data-stu-id="79c1c-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="79c1c-158">decimal</span><span class="sxs-lookup"><span data-stu-id="79c1c-158">decimal</span></span>|<span data-ttu-id="79c1c-159">número fracionário representado como um ponto fixo ou um número racional</span><span class="sxs-lookup"><span data-stu-id="79c1c-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="79c1c-160">M ou m</span><span class="sxs-lookup"><span data-stu-id="79c1c-160">M or m</span></span>|<span data-ttu-id="79c1c-161">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="79c1c-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="79c1c-162">Char</span><span class="sxs-lookup"><span data-stu-id="79c1c-162">Char</span></span>|<span data-ttu-id="79c1c-163">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="79c1c-163">Unicode character</span></span>|<span data-ttu-id="79c1c-164">nenhum</span><span class="sxs-lookup"><span data-stu-id="79c1c-164">none</span></span>|`'a'`|
|<span data-ttu-id="79c1c-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="79c1c-165">String</span></span>|<span data-ttu-id="79c1c-166">Cadeia de caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="79c1c-166">Unicode string</span></span>|<span data-ttu-id="79c1c-167">nenhum</span><span class="sxs-lookup"><span data-stu-id="79c1c-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="79c1c-168">ou</span><span class="sxs-lookup"><span data-stu-id="79c1c-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="79c1c-169">ou</span><span class="sxs-lookup"><span data-stu-id="79c1c-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="79c1c-170">ou</span><span class="sxs-lookup"><span data-stu-id="79c1c-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="79c1c-171">Consulte também [cadeias de caracteres](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="79c1c-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="79c1c-172">byte</span><span class="sxs-lookup"><span data-stu-id="79c1c-172">byte</span></span>|<span data-ttu-id="79c1c-173">Caractere ASCII</span><span class="sxs-lookup"><span data-stu-id="79c1c-173">ASCII character</span></span>|<span data-ttu-id="79c1c-174">B</span><span class="sxs-lookup"><span data-stu-id="79c1c-174">B</span></span>|`'a'B`|
|<span data-ttu-id="79c1c-175">byte[]</span><span class="sxs-lookup"><span data-stu-id="79c1c-175">byte[]</span></span>|<span data-ttu-id="79c1c-176">Cadeia de caracteres ASCII</span><span class="sxs-lookup"><span data-stu-id="79c1c-176">ASCII string</span></span>|<span data-ttu-id="79c1c-177">B</span><span class="sxs-lookup"><span data-stu-id="79c1c-177">B</span></span>|`"text"B`|
|<span data-ttu-id="79c1c-178">Cadeia de caracteres ou byte]</span><span class="sxs-lookup"><span data-stu-id="79c1c-178">String or byte[]</span></span>|<span data-ttu-id="79c1c-179">cadeia de caracteres textual</span><span class="sxs-lookup"><span data-stu-id="79c1c-179">verbatim string</span></span>|<span data-ttu-id="79c1c-180">@ prefix</span><span class="sxs-lookup"><span data-stu-id="79c1c-180">@ prefix</span></span>|<span data-ttu-id="79c1c-181">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="79c1c-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="79c1c-182">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="79c1c-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="79c1c-183">Comentários</span><span class="sxs-lookup"><span data-stu-id="79c1c-183">Remarks</span></span>

<span data-ttu-id="79c1c-184">Cadeias de caracteres Unicode podem conter as codificações explícitas que você pode especificar usando `\u` seguido por um código hexadecimal de 16 bits ou codificações UTF-32 que você pode especificar usando `\U` seguido por um código hexadecimal de 32 bits que representa a Unicode par substituto.</span><span class="sxs-lookup"><span data-stu-id="79c1c-184">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="79c1c-185">Como de F# 3.1, você pode usar o `+` entrar para combinar literais de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="79c1c-185">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="79c1c-186">Você também pode usar o bit a bit ou (`|||`) operador para combinar sinalizadores de enum.</span><span class="sxs-lookup"><span data-stu-id="79c1c-186">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="79c1c-187">Por exemplo, o código a seguir é legal no F# 3.1:</span><span class="sxs-lookup"><span data-stu-id="79c1c-187">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="79c1c-188">Não é permitido o uso de outros operadores bit a bit.</span><span class="sxs-lookup"><span data-stu-id="79c1c-188">The use of other bitwise operators isn't allowed.</span></span>

## <a name="named-literals"></a><span data-ttu-id="79c1c-189">Literais nomeados</span><span class="sxs-lookup"><span data-stu-id="79c1c-189">Named Literals</span></span>

<span data-ttu-id="79c1c-190">Os valores que devem ser constantes podem ser marcados com o [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atributo.</span><span class="sxs-lookup"><span data-stu-id="79c1c-190">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="79c1c-191">Este atributo tem o efeito de causar um valor a ser compilado como uma constante.</span><span class="sxs-lookup"><span data-stu-id="79c1c-191">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="79c1c-192">Em expressões de correspondência, identificadores que começam com caracteres minúsculos sempre são tratados como variáveis a serem associadas, em vez de como literais, portanto, você deve geralmente usar iniciais maiusculas ao definir literais.</span><span class="sxs-lookup"><span data-stu-id="79c1c-192">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="79c1c-193">Números inteiros em outras Bases</span><span class="sxs-lookup"><span data-stu-id="79c1c-193">Integers In Other Bases</span></span>

<span data-ttu-id="79c1c-194">Inteiros com sinal de 32 bits também podem ser especificados em octal, hexadecimal ou binário usando um `0x`, `0o` ou `0b` do prefixo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="79c1c-194">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="79c1c-195">Sublinhados em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="79c1c-195">Underscores in Numeric Literals</span></span>

<span data-ttu-id="79c1c-196">Começando com F# 4.1, você pode separar dígitos com o caractere de sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="79c1c-196">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="79c1c-197">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79c1c-197">See also</span></span>

- [<span data-ttu-id="79c1c-198">Classe Core. literalattribute</span><span class="sxs-lookup"><span data-stu-id="79c1c-198">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
