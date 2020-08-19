---
title: Literais
description: 'Saiba mais sobre os tipos literais na linguagem de programação F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 15f73db3c36f7c60ab1eeba96c63a28ebc6d7f01
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559148"
---
# <a name="literals"></a><span data-ttu-id="aa9d1-103">Literais</span><span class="sxs-lookup"><span data-stu-id="aa9d1-103">Literals</span></span>

<span data-ttu-id="aa9d1-104">Este artigo fornece uma tabela que mostra como especificar o tipo de um literal em F #.</span><span class="sxs-lookup"><span data-stu-id="aa9d1-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="aa9d1-105"> Tipos literais</span><span class="sxs-lookup"><span data-stu-id="aa9d1-105">Literal types</span></span>

<span data-ttu-id="aa9d1-106">A tabela a seguir mostra os tipos literais em F #.</span><span class="sxs-lookup"><span data-stu-id="aa9d1-106">The following table shows the literal types in F#.</span></span> <span data-ttu-id="aa9d1-107">Os caracteres que representam dígitos na notação hexadecimal não diferenciam maiúsculas de minúsculas; os caracteres que identificam o tipo diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="aa9d1-107">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="aa9d1-108">Type</span><span class="sxs-lookup"><span data-stu-id="aa9d1-108">Type</span></span>|<span data-ttu-id="aa9d1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa9d1-109">Description</span></span>|<span data-ttu-id="aa9d1-110">Sufixo ou prefixo</span><span class="sxs-lookup"><span data-stu-id="aa9d1-110">Suffix or prefix</span></span>|<span data-ttu-id="aa9d1-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="aa9d1-111">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="aa9d1-112">sbyte</span><span class="sxs-lookup"><span data-stu-id="aa9d1-112">sbyte</span></span>|<span data-ttu-id="aa9d1-113">inteiro de 8 bits assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-113">signed 8-bit integer</span></span>|<span data-ttu-id="aa9d1-114">a</span><span class="sxs-lookup"><span data-stu-id="aa9d1-114">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="aa9d1-115">byte</span><span class="sxs-lookup"><span data-stu-id="aa9d1-115">byte</span></span>|<span data-ttu-id="aa9d1-116">número natural de 8 bits não assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-116">unsigned 8-bit natural number</span></span>|<span data-ttu-id="aa9d1-117">uy</span><span class="sxs-lookup"><span data-stu-id="aa9d1-117">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="aa9d1-118">int16</span><span class="sxs-lookup"><span data-stu-id="aa9d1-118">int16</span></span>|<span data-ttu-id="aa9d1-119">inteiro de 16 bits assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-119">signed 16-bit integer</span></span>|<span data-ttu-id="aa9d1-120">s</span><span class="sxs-lookup"><span data-stu-id="aa9d1-120">s</span></span>|`86s`|
|<span data-ttu-id="aa9d1-121">uint16</span><span class="sxs-lookup"><span data-stu-id="aa9d1-121">uint16</span></span>|<span data-ttu-id="aa9d1-122">número natural de 16 bits não assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-122">unsigned 16-bit natural number</span></span>|<span data-ttu-id="aa9d1-123">us</span><span class="sxs-lookup"><span data-stu-id="aa9d1-123">us</span></span>|`86us`|
|<span data-ttu-id="aa9d1-124">INT</span><span class="sxs-lookup"><span data-stu-id="aa9d1-124">int</span></span><br /><br /><span data-ttu-id="aa9d1-125">int32</span><span class="sxs-lookup"><span data-stu-id="aa9d1-125">int32</span></span>|<span data-ttu-id="aa9d1-126">inteiro de 32 bits assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-126">signed 32-bit integer</span></span>|<span data-ttu-id="aa9d1-127">l ou None</span><span class="sxs-lookup"><span data-stu-id="aa9d1-127">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="aa9d1-128">uint</span><span class="sxs-lookup"><span data-stu-id="aa9d1-128">uint</span></span><br /><br /><span data-ttu-id="aa9d1-129">uint32</span><span class="sxs-lookup"><span data-stu-id="aa9d1-129">uint32</span></span>|<span data-ttu-id="aa9d1-130">número natural de 32 bits não assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-130">unsigned 32-bit natural number</span></span>|<span data-ttu-id="aa9d1-131">u ou UL</span><span class="sxs-lookup"><span data-stu-id="aa9d1-131">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="aa9d1-132">nativeint</span><span class="sxs-lookup"><span data-stu-id="aa9d1-132">nativeint</span></span>|<span data-ttu-id="aa9d1-133">ponteiro nativo para um número natural assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-133">native pointer to a signed natural number</span></span>|<span data-ttu-id="aa9d1-134">n</span><span class="sxs-lookup"><span data-stu-id="aa9d1-134">n</span></span>|`123n`|
|<span data-ttu-id="aa9d1-135">unativeint</span><span class="sxs-lookup"><span data-stu-id="aa9d1-135">unativeint</span></span>|<span data-ttu-id="aa9d1-136">ponteiro nativo como um número natural não assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-136">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="aa9d1-137">anula</span><span class="sxs-lookup"><span data-stu-id="aa9d1-137">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="aa9d1-138">int64</span><span class="sxs-lookup"><span data-stu-id="aa9d1-138">int64</span></span>|<span data-ttu-id="aa9d1-139">inteiro de 64 bits assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-139">signed 64-bit integer</span></span>|<span data-ttu-id="aa9d1-140">L</span><span class="sxs-lookup"><span data-stu-id="aa9d1-140">L</span></span>|`86L`|
|<span data-ttu-id="aa9d1-141">uint64</span><span class="sxs-lookup"><span data-stu-id="aa9d1-141">uint64</span></span>|<span data-ttu-id="aa9d1-142">número natural de 64 bits não assinado</span><span class="sxs-lookup"><span data-stu-id="aa9d1-142">unsigned 64-bit natural number</span></span>|<span data-ttu-id="aa9d1-143">UL</span><span class="sxs-lookup"><span data-stu-id="aa9d1-143">UL</span></span>|`86UL`|
|<span data-ttu-id="aa9d1-144">único, float32</span><span class="sxs-lookup"><span data-stu-id="aa9d1-144">single, float32</span></span>|<span data-ttu-id="aa9d1-145">número de ponto flutuante de 32 bits</span><span class="sxs-lookup"><span data-stu-id="aa9d1-145">32-bit floating point number</span></span>|<span data-ttu-id="aa9d1-146">F ou f</span><span class="sxs-lookup"><span data-stu-id="aa9d1-146">F or f</span></span>|<span data-ttu-id="aa9d1-147">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="aa9d1-147">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="aa9d1-148">alimentação</span><span class="sxs-lookup"><span data-stu-id="aa9d1-148">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="aa9d1-149">barra Clique</span><span class="sxs-lookup"><span data-stu-id="aa9d1-149">float; double</span></span>|<span data-ttu-id="aa9d1-150">número de ponto flutuante de 64 bits</span><span class="sxs-lookup"><span data-stu-id="aa9d1-150">64-bit floating point number</span></span>|<span data-ttu-id="aa9d1-151">nenhum</span><span class="sxs-lookup"><span data-stu-id="aa9d1-151">none</span></span>|<span data-ttu-id="aa9d1-152">`4.14` ou `2.3E+32` ou `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="aa9d1-152">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="aa9d1-153">ALIMENTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="aa9d1-153">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="aa9d1-154">BIGINT</span><span class="sxs-lookup"><span data-stu-id="aa9d1-154">bigint</span></span>|<span data-ttu-id="aa9d1-155">inteiro não limitado à representação de 64 bits</span><span class="sxs-lookup"><span data-stu-id="aa9d1-155">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="aa9d1-156">I</span><span class="sxs-lookup"><span data-stu-id="aa9d1-156">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="aa9d1-157">decimal</span><span class="sxs-lookup"><span data-stu-id="aa9d1-157">decimal</span></span>|<span data-ttu-id="aa9d1-158">número fracionário representado como um ponto fixo ou um número racional</span><span class="sxs-lookup"><span data-stu-id="aa9d1-158">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="aa9d1-159">M ou m</span><span class="sxs-lookup"><span data-stu-id="aa9d1-159">M or m</span></span>|<span data-ttu-id="aa9d1-160">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="aa9d1-160">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="aa9d1-161">Char</span><span class="sxs-lookup"><span data-stu-id="aa9d1-161">Char</span></span>|<span data-ttu-id="aa9d1-162">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="aa9d1-162">Unicode character</span></span>|<span data-ttu-id="aa9d1-163">nenhum</span><span class="sxs-lookup"><span data-stu-id="aa9d1-163">none</span></span>|<span data-ttu-id="aa9d1-164">`'a'` ou `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="aa9d1-164">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="aa9d1-165">String</span><span class="sxs-lookup"><span data-stu-id="aa9d1-165">String</span></span>|<span data-ttu-id="aa9d1-166">Cadeia de caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="aa9d1-166">Unicode string</span></span>|<span data-ttu-id="aa9d1-167">nenhum</span><span class="sxs-lookup"><span data-stu-id="aa9d1-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="aa9d1-168">ou</span><span class="sxs-lookup"><span data-stu-id="aa9d1-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="aa9d1-169">ou</span><span class="sxs-lookup"><span data-stu-id="aa9d1-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="aa9d1-170">ou</span><span class="sxs-lookup"><span data-stu-id="aa9d1-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="aa9d1-171">Consulte também [cadeias de caracteres](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="aa9d1-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="aa9d1-172">byte</span><span class="sxs-lookup"><span data-stu-id="aa9d1-172">byte</span></span>|<span data-ttu-id="aa9d1-173">Caractere ASCII</span><span class="sxs-lookup"><span data-stu-id="aa9d1-173">ASCII character</span></span>|<span data-ttu-id="aa9d1-174">B</span><span class="sxs-lookup"><span data-stu-id="aa9d1-174">B</span></span>|`'a'B`|
|<span data-ttu-id="aa9d1-175">byte[]</span><span class="sxs-lookup"><span data-stu-id="aa9d1-175">byte[]</span></span>|<span data-ttu-id="aa9d1-176">Cadeia de caracteres ASCII</span><span class="sxs-lookup"><span data-stu-id="aa9d1-176">ASCII string</span></span>|<span data-ttu-id="aa9d1-177">B</span><span class="sxs-lookup"><span data-stu-id="aa9d1-177">B</span></span>|`"text"B`|
|<span data-ttu-id="aa9d1-178">Cadeia de caracteres ou byte []</span><span class="sxs-lookup"><span data-stu-id="aa9d1-178">String or byte[]</span></span>|<span data-ttu-id="aa9d1-179">Cadeia de caracteres textual</span><span class="sxs-lookup"><span data-stu-id="aa9d1-179">verbatim string</span></span>|<span data-ttu-id="aa9d1-180">@ prefix</span><span class="sxs-lookup"><span data-stu-id="aa9d1-180">@ prefix</span></span>|<span data-ttu-id="aa9d1-181">`@"\\server\share"` Unicode</span><span class="sxs-lookup"><span data-stu-id="aa9d1-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="aa9d1-182">`@"\\server\share"B` LOCALIZADOS</span><span class="sxs-lookup"><span data-stu-id="aa9d1-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="aa9d1-183">Literais nomeadas</span><span class="sxs-lookup"><span data-stu-id="aa9d1-183">Named literals</span></span>

<span data-ttu-id="aa9d1-184">Os valores que se destinam a serem constantes podem ser marcados com o atributo [literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) .</span><span class="sxs-lookup"><span data-stu-id="aa9d1-184">Values that are intended to be constants can be marked with the [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) attribute.</span></span> <span data-ttu-id="aa9d1-185">Esse atributo tem o efeito de fazer com que um valor seja compilado como uma constante.</span><span class="sxs-lookup"><span data-stu-id="aa9d1-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="aa9d1-186">Em expressões de correspondência de padrões, os identificadores que começam com caracteres minúsculos são sempre tratados como variáveis a serem associadas, e não como literais, de modo que você geralmente deve usar maiúsculas iniciais ao definir literais.</span><span class="sxs-lookup"><span data-stu-id="aa9d1-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a><span data-ttu-id="aa9d1-187">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa9d1-187">Remarks</span></span>

<span data-ttu-id="aa9d1-188">As cadeias de caracteres Unicode podem conter codificações explícitas que você pode especificar usando `\u` seguido por um código hexadecimal de 16 bits (0000-ffff) ou codificações UTF-32 que você pode especificar usando `\U` seguido por um código hexadecimal de 32 bits que representa qualquer ponto de código Unicode (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="aa9d1-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="aa9d1-189">O uso de outros outros operadores bit a não `|||` é permitido.</span><span class="sxs-lookup"><span data-stu-id="aa9d1-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="aa9d1-190">Inteiros em outras bases</span><span class="sxs-lookup"><span data-stu-id="aa9d1-190">Integers in other bases</span></span>

<span data-ttu-id="aa9d1-191">Os inteiros de 32 bits assinados também podem ser especificados em hexadecimal, octal ou binário usando um `0x` `0o` prefixo, ou `0b` respectivamente.</span><span class="sxs-lookup"><span data-stu-id="aa9d1-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="aa9d1-192">Sublinhados em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="aa9d1-192">Underscores in numeric literals</span></span>

<span data-ttu-id="aa9d1-193">Você pode separar dígitos com o caractere de sublinhado ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="aa9d1-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```
