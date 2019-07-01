---
title: Literais
description: Saiba mais sobre os tipos de literais no F# linguagem de programação.
ms.date: 06/28/2019
ms.openlocfilehash: 53647d8cbc2a59527a50e122bc1abc6055c1fce5
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487777"
---
# <a name="literals"></a><span data-ttu-id="2ff78-103">Literais</span><span class="sxs-lookup"><span data-stu-id="2ff78-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="2ff78-104">Os links de referência de API neste artigo você será levado ao MSDN (por enquanto).</span><span class="sxs-lookup"><span data-stu-id="2ff78-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="2ff78-105">Este tópico fornece uma tabela que mostra como especificar o tipo de um literal em F#.</span><span class="sxs-lookup"><span data-stu-id="2ff78-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="2ff78-106">Tipos literais</span><span class="sxs-lookup"><span data-stu-id="2ff78-106">Literal Types</span></span>

<span data-ttu-id="2ff78-107">A tabela a seguir mostra os tipos de literais no F#.</span><span class="sxs-lookup"><span data-stu-id="2ff78-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="2ff78-108">Caracteres que representam dígitos em notação hexadecimal não diferenciam maiusculas de minúsculas; caracteres que identifica o tipo diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="2ff78-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="2ff78-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="2ff78-109">Type</span></span>|<span data-ttu-id="2ff78-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ff78-110">Description</span></span>|<span data-ttu-id="2ff78-111">Prefixo ou sufixo</span><span class="sxs-lookup"><span data-stu-id="2ff78-111">Suffix or prefix</span></span>|<span data-ttu-id="2ff78-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2ff78-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="2ff78-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="2ff78-113">sbyte</span></span>|<span data-ttu-id="2ff78-114">inteiro com sinal de 8 bits</span><span class="sxs-lookup"><span data-stu-id="2ff78-114">signed 8-bit integer</span></span>|<span data-ttu-id="2ff78-115">y</span><span class="sxs-lookup"><span data-stu-id="2ff78-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="2ff78-116">byte</span><span class="sxs-lookup"><span data-stu-id="2ff78-116">byte</span></span>|<span data-ttu-id="2ff78-117">número de natural de 8 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="2ff78-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="2ff78-118">uy</span><span class="sxs-lookup"><span data-stu-id="2ff78-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="2ff78-119">int16</span><span class="sxs-lookup"><span data-stu-id="2ff78-119">int16</span></span>|<span data-ttu-id="2ff78-120">inteiro com sinal de 16 bits</span><span class="sxs-lookup"><span data-stu-id="2ff78-120">signed 16-bit integer</span></span>|<span data-ttu-id="2ff78-121">s</span><span class="sxs-lookup"><span data-stu-id="2ff78-121">s</span></span>|`86s`|
|<span data-ttu-id="2ff78-122">uint16</span><span class="sxs-lookup"><span data-stu-id="2ff78-122">uint16</span></span>|<span data-ttu-id="2ff78-123">número de natural de 16 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="2ff78-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="2ff78-124">us</span><span class="sxs-lookup"><span data-stu-id="2ff78-124">us</span></span>|`86us`|
|<span data-ttu-id="2ff78-125">int</span><span class="sxs-lookup"><span data-stu-id="2ff78-125">int</span></span><br /><br /><span data-ttu-id="2ff78-126">int32</span><span class="sxs-lookup"><span data-stu-id="2ff78-126">int32</span></span>|<span data-ttu-id="2ff78-127">inteiro com sinal de 32 bits</span><span class="sxs-lookup"><span data-stu-id="2ff78-127">signed 32-bit integer</span></span>|<span data-ttu-id="2ff78-128">l ou none</span><span class="sxs-lookup"><span data-stu-id="2ff78-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="2ff78-129">uint</span><span class="sxs-lookup"><span data-stu-id="2ff78-129">uint</span></span><br /><br /><span data-ttu-id="2ff78-130">uint32</span><span class="sxs-lookup"><span data-stu-id="2ff78-130">uint32</span></span>|<span data-ttu-id="2ff78-131">número de natural de 32 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="2ff78-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="2ff78-132">u ou ul</span><span class="sxs-lookup"><span data-stu-id="2ff78-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="2ff78-133">nativeint</span><span class="sxs-lookup"><span data-stu-id="2ff78-133">nativeint</span></span>|<span data-ttu-id="2ff78-134">ponteiro nativo para um número natural assinado</span><span class="sxs-lookup"><span data-stu-id="2ff78-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="2ff78-135">n</span><span class="sxs-lookup"><span data-stu-id="2ff78-135">n</span></span>|`123n`|
|<span data-ttu-id="2ff78-136">unativeint</span><span class="sxs-lookup"><span data-stu-id="2ff78-136">unativeint</span></span>|<span data-ttu-id="2ff78-137">ponteiro nativo como um número natural sem sinal</span><span class="sxs-lookup"><span data-stu-id="2ff78-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="2ff78-138">Cancelar</span><span class="sxs-lookup"><span data-stu-id="2ff78-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="2ff78-139">int64</span><span class="sxs-lookup"><span data-stu-id="2ff78-139">int64</span></span>|<span data-ttu-id="2ff78-140">inteiro com sinal de 64 bits</span><span class="sxs-lookup"><span data-stu-id="2ff78-140">signed 64-bit integer</span></span>|<span data-ttu-id="2ff78-141">L</span><span class="sxs-lookup"><span data-stu-id="2ff78-141">L</span></span>|`86L`|
|<span data-ttu-id="2ff78-142">uint64</span><span class="sxs-lookup"><span data-stu-id="2ff78-142">uint64</span></span>|<span data-ttu-id="2ff78-143">número de natural de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="2ff78-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="2ff78-144">UL</span><span class="sxs-lookup"><span data-stu-id="2ff78-144">UL</span></span>|`86UL`|
|<span data-ttu-id="2ff78-145">simples, float32</span><span class="sxs-lookup"><span data-stu-id="2ff78-145">single, float32</span></span>|<span data-ttu-id="2ff78-146">número de ponto flutuante de 32 bits</span><span class="sxs-lookup"><span data-stu-id="2ff78-146">32-bit floating point number</span></span>|<span data-ttu-id="2ff78-147">F ou f</span><span class="sxs-lookup"><span data-stu-id="2ff78-147">F or f</span></span>|<span data-ttu-id="2ff78-148">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="2ff78-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="2ff78-149">LF</span><span class="sxs-lookup"><span data-stu-id="2ff78-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="2ff78-150">float; Double</span><span class="sxs-lookup"><span data-stu-id="2ff78-150">float; double</span></span>|<span data-ttu-id="2ff78-151">número de ponto flutuante de 64 bits</span><span class="sxs-lookup"><span data-stu-id="2ff78-151">64-bit floating point number</span></span>|<span data-ttu-id="2ff78-152">nenhum</span><span class="sxs-lookup"><span data-stu-id="2ff78-152">none</span></span>|<span data-ttu-id="2ff78-153">`4.14`, `2.3E+32` ou `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="2ff78-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="2ff78-154">LF</span><span class="sxs-lookup"><span data-stu-id="2ff78-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="2ff78-155">bigint</span><span class="sxs-lookup"><span data-stu-id="2ff78-155">bigint</span></span>|<span data-ttu-id="2ff78-156">inteiro não limitado a representação de 64 bits</span><span class="sxs-lookup"><span data-stu-id="2ff78-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="2ff78-157">I</span><span class="sxs-lookup"><span data-stu-id="2ff78-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="2ff78-158">decimal</span><span class="sxs-lookup"><span data-stu-id="2ff78-158">decimal</span></span>|<span data-ttu-id="2ff78-159">número fracionário representado como um ponto fixo ou um número racional</span><span class="sxs-lookup"><span data-stu-id="2ff78-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="2ff78-160">M ou m</span><span class="sxs-lookup"><span data-stu-id="2ff78-160">M or m</span></span>|<span data-ttu-id="2ff78-161">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="2ff78-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="2ff78-162">Char</span><span class="sxs-lookup"><span data-stu-id="2ff78-162">Char</span></span>|<span data-ttu-id="2ff78-163">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="2ff78-163">Unicode character</span></span>|<span data-ttu-id="2ff78-164">nenhum</span><span class="sxs-lookup"><span data-stu-id="2ff78-164">none</span></span>|`'a'`|
|<span data-ttu-id="2ff78-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="2ff78-165">String</span></span>|<span data-ttu-id="2ff78-166">Cadeia de caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="2ff78-166">Unicode string</span></span>|<span data-ttu-id="2ff78-167">nenhum</span><span class="sxs-lookup"><span data-stu-id="2ff78-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="2ff78-168">ou</span><span class="sxs-lookup"><span data-stu-id="2ff78-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="2ff78-169">ou</span><span class="sxs-lookup"><span data-stu-id="2ff78-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="2ff78-170">ou</span><span class="sxs-lookup"><span data-stu-id="2ff78-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="2ff78-171">Consulte também [cadeias de caracteres](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="2ff78-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="2ff78-172">byte</span><span class="sxs-lookup"><span data-stu-id="2ff78-172">byte</span></span>|<span data-ttu-id="2ff78-173">Caractere ASCII</span><span class="sxs-lookup"><span data-stu-id="2ff78-173">ASCII character</span></span>|<span data-ttu-id="2ff78-174">B</span><span class="sxs-lookup"><span data-stu-id="2ff78-174">B</span></span>|`'a'B`|
|<span data-ttu-id="2ff78-175">byte[]</span><span class="sxs-lookup"><span data-stu-id="2ff78-175">byte[]</span></span>|<span data-ttu-id="2ff78-176">Cadeia de caracteres ASCII</span><span class="sxs-lookup"><span data-stu-id="2ff78-176">ASCII string</span></span>|<span data-ttu-id="2ff78-177">B</span><span class="sxs-lookup"><span data-stu-id="2ff78-177">B</span></span>|`"text"B`|
|<span data-ttu-id="2ff78-178">Cadeia de caracteres ou byte]</span><span class="sxs-lookup"><span data-stu-id="2ff78-178">String or byte[]</span></span>|<span data-ttu-id="2ff78-179">cadeia de caracteres textual</span><span class="sxs-lookup"><span data-stu-id="2ff78-179">verbatim string</span></span>|<span data-ttu-id="2ff78-180">@ prefix</span><span class="sxs-lookup"><span data-stu-id="2ff78-180">@ prefix</span></span>|<span data-ttu-id="2ff78-181">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="2ff78-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="2ff78-182">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="2ff78-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="2ff78-183">Literais nomeados</span><span class="sxs-lookup"><span data-stu-id="2ff78-183">Named literals</span></span>

<span data-ttu-id="2ff78-184">Os valores que devem ser constantes podem ser marcados com o [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atributo.</span><span class="sxs-lookup"><span data-stu-id="2ff78-184">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="2ff78-185">Este atributo tem o efeito de causar um valor a ser compilado como uma constante.</span><span class="sxs-lookup"><span data-stu-id="2ff78-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="2ff78-186">Em expressões de correspondência, identificadores que começam com caracteres minúsculos sempre são tratados como variáveis a serem associadas, em vez de como literais, portanto, você deve geralmente usar iniciais maiusculas ao definir literais.</span><span class="sxs-lookup"><span data-stu-id="2ff78-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="2ff78-187">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ff78-187">Remarks</span></span>

<span data-ttu-id="2ff78-188">Cadeias de caracteres Unicode podem conter as codificações explícitas que você pode especificar usando `\u` seguido por um código hexadecimal de 16 bits (0000 - FFFF) ou codificações UTF-32 que você pode especificar usando `\U` seguido por um código hexadecimal de 32 bits que representa qualquer ponto de código Unicode (00000000 - 00010FFFF).</span><span class="sxs-lookup"><span data-stu-id="2ff78-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 00010FFFF).</span></span>

<span data-ttu-id="2ff78-189">O uso de outros operadores bit a bit diferente de `|||` não é permitido.</span><span class="sxs-lookup"><span data-stu-id="2ff78-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="2ff78-190">Números inteiros em outras bases</span><span class="sxs-lookup"><span data-stu-id="2ff78-190">Integers in other bases</span></span>

<span data-ttu-id="2ff78-191">Inteiros com sinal de 32 bits também podem ser especificados em octal, hexadecimal ou binário usando um `0x`, `0o` ou `0b` do prefixo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2ff78-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="2ff78-192">Sublinhados em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="2ff78-192">Underscores in numeric literals</span></span>

<span data-ttu-id="2ff78-193">Você pode separar dígitos com o caractere de sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="2ff78-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="2ff78-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ff78-194">See also</span></span>

- [<span data-ttu-id="2ff78-195">Classe Core. literalattribute</span><span class="sxs-lookup"><span data-stu-id="2ff78-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
