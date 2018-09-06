---
title: Literais (F#)
description: 'Saiba mais sobre os tipos de literais na linguagem de programação F #.'
ms.date: 05/16/2016
ms.openlocfilehash: e6d34acd928edce8447c793105b08085ab0757b9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44035772"
---
# <a name="literals"></a><span data-ttu-id="abc06-103">Literais</span><span class="sxs-lookup"><span data-stu-id="abc06-103">Literals</span></span>

> [!NOTE]
<span data-ttu-id="abc06-104">Os links de referência de API neste artigo você será levado ao MSDN (por enquanto).</span><span class="sxs-lookup"><span data-stu-id="abc06-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="abc06-105">Este tópico fornece uma tabela que mostra como especificar o tipo de um literal em F #.</span><span class="sxs-lookup"><span data-stu-id="abc06-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="abc06-106">Tipos literais</span><span class="sxs-lookup"><span data-stu-id="abc06-106">Literal Types</span></span>

<span data-ttu-id="abc06-107">A tabela a seguir mostra os tipos de literais no F #.</span><span class="sxs-lookup"><span data-stu-id="abc06-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="abc06-108">Caracteres que representam dígitos em notação hexadecimal não diferenciam maiusculas de minúsculas; caracteres que identifica o tipo diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="abc06-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="abc06-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="abc06-109">Type</span></span>|<span data-ttu-id="abc06-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="abc06-110">Description</span></span>|<span data-ttu-id="abc06-111">Prefixo ou sufixo</span><span class="sxs-lookup"><span data-stu-id="abc06-111">Suffix or prefix</span></span>|<span data-ttu-id="abc06-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="abc06-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="abc06-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="abc06-113">sbyte</span></span>|<span data-ttu-id="abc06-114">inteiro com sinal de 8 bits</span><span class="sxs-lookup"><span data-stu-id="abc06-114">signed 8-bit integer</span></span>|<span data-ttu-id="abc06-115">y</span><span class="sxs-lookup"><span data-stu-id="abc06-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="abc06-116">byte</span><span class="sxs-lookup"><span data-stu-id="abc06-116">byte</span></span>|<span data-ttu-id="abc06-117">número de natural de 8 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="abc06-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="abc06-118">uy</span><span class="sxs-lookup"><span data-stu-id="abc06-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="abc06-119">int16</span><span class="sxs-lookup"><span data-stu-id="abc06-119">int16</span></span>|<span data-ttu-id="abc06-120">inteiro com sinal de 16 bits</span><span class="sxs-lookup"><span data-stu-id="abc06-120">signed 16-bit integer</span></span>|<span data-ttu-id="abc06-121">s</span><span class="sxs-lookup"><span data-stu-id="abc06-121">s</span></span>|`86s`|
|<span data-ttu-id="abc06-122">uint16</span><span class="sxs-lookup"><span data-stu-id="abc06-122">uint16</span></span>|<span data-ttu-id="abc06-123">número de natural de 16 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="abc06-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="abc06-124">us</span><span class="sxs-lookup"><span data-stu-id="abc06-124">us</span></span>|`86us`|
|<span data-ttu-id="abc06-125">int</span><span class="sxs-lookup"><span data-stu-id="abc06-125">int</span></span><br /><br /><span data-ttu-id="abc06-126">int32</span><span class="sxs-lookup"><span data-stu-id="abc06-126">int32</span></span>|<span data-ttu-id="abc06-127">inteiro com sinal de 32 bits</span><span class="sxs-lookup"><span data-stu-id="abc06-127">signed 32-bit integer</span></span>|<span data-ttu-id="abc06-128">l ou none</span><span class="sxs-lookup"><span data-stu-id="abc06-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="abc06-129">uint</span><span class="sxs-lookup"><span data-stu-id="abc06-129">uint</span></span><br /><br /><span data-ttu-id="abc06-130">uint32</span><span class="sxs-lookup"><span data-stu-id="abc06-130">uint32</span></span>|<span data-ttu-id="abc06-131">número de natural de 32 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="abc06-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="abc06-132">u ou ul</span><span class="sxs-lookup"><span data-stu-id="abc06-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="abc06-133">unativeint</span><span class="sxs-lookup"><span data-stu-id="abc06-133">unativeint</span></span>|<span data-ttu-id="abc06-134">ponteiro nativo como um número natural sem sinal</span><span class="sxs-lookup"><span data-stu-id="abc06-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="abc06-135">Cancelar</span><span class="sxs-lookup"><span data-stu-id="abc06-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="abc06-136">int64</span><span class="sxs-lookup"><span data-stu-id="abc06-136">int64</span></span>|<span data-ttu-id="abc06-137">inteiro com sinal de 64 bits</span><span class="sxs-lookup"><span data-stu-id="abc06-137">signed 64-bit integer</span></span>|<span data-ttu-id="abc06-138">L</span><span class="sxs-lookup"><span data-stu-id="abc06-138">L</span></span>|`86L`|
|<span data-ttu-id="abc06-139">uint64</span><span class="sxs-lookup"><span data-stu-id="abc06-139">uint64</span></span>|<span data-ttu-id="abc06-140">número de natural de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="abc06-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="abc06-141">UL</span><span class="sxs-lookup"><span data-stu-id="abc06-141">UL</span></span>|`86UL`|
|<span data-ttu-id="abc06-142">simples, float32</span><span class="sxs-lookup"><span data-stu-id="abc06-142">single, float32</span></span>|<span data-ttu-id="abc06-143">número de ponto flutuante de 32 bits</span><span class="sxs-lookup"><span data-stu-id="abc06-143">32-bit floating point number</span></span>|<span data-ttu-id="abc06-144">F ou f</span><span class="sxs-lookup"><span data-stu-id="abc06-144">F or f</span></span>|<span data-ttu-id="abc06-145">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="abc06-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="abc06-146">LF</span><span class="sxs-lookup"><span data-stu-id="abc06-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="abc06-147">float; Double</span><span class="sxs-lookup"><span data-stu-id="abc06-147">float; double</span></span>|<span data-ttu-id="abc06-148">número de ponto flutuante de 64 bits</span><span class="sxs-lookup"><span data-stu-id="abc06-148">64-bit floating point number</span></span>|<span data-ttu-id="abc06-149">nenhum</span><span class="sxs-lookup"><span data-stu-id="abc06-149">none</span></span>|<span data-ttu-id="abc06-150">`4.14` ou `2.3E+32` ou `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="abc06-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="abc06-151">LF</span><span class="sxs-lookup"><span data-stu-id="abc06-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="abc06-152">bigint</span><span class="sxs-lookup"><span data-stu-id="abc06-152">bigint</span></span>|<span data-ttu-id="abc06-153">inteiro não limitado a representação de 64 bits</span><span class="sxs-lookup"><span data-stu-id="abc06-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="abc06-154">I</span><span class="sxs-lookup"><span data-stu-id="abc06-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="abc06-155">decimal</span><span class="sxs-lookup"><span data-stu-id="abc06-155">decimal</span></span>|<span data-ttu-id="abc06-156">número fracionário representado como um ponto fixo ou um número racional</span><span class="sxs-lookup"><span data-stu-id="abc06-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="abc06-157">M ou m</span><span class="sxs-lookup"><span data-stu-id="abc06-157">M or m</span></span>|<span data-ttu-id="abc06-158">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="abc06-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="abc06-159">Char</span><span class="sxs-lookup"><span data-stu-id="abc06-159">Char</span></span>|<span data-ttu-id="abc06-160">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="abc06-160">Unicode character</span></span>|<span data-ttu-id="abc06-161">nenhum</span><span class="sxs-lookup"><span data-stu-id="abc06-161">none</span></span>|`'a'`|
|<span data-ttu-id="abc06-162">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="abc06-162">String</span></span>|<span data-ttu-id="abc06-163">Cadeia de caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="abc06-163">Unicode string</span></span>|<span data-ttu-id="abc06-164">nenhum</span><span class="sxs-lookup"><span data-stu-id="abc06-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="abc06-165">ou</span><span class="sxs-lookup"><span data-stu-id="abc06-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="abc06-166">ou</span><span class="sxs-lookup"><span data-stu-id="abc06-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="abc06-167">ou</span><span class="sxs-lookup"><span data-stu-id="abc06-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="abc06-168">Consulte também [cadeias de caracteres](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="abc06-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="abc06-169">byte</span><span class="sxs-lookup"><span data-stu-id="abc06-169">byte</span></span>|<span data-ttu-id="abc06-170">Caractere ASCII</span><span class="sxs-lookup"><span data-stu-id="abc06-170">ASCII character</span></span>|<span data-ttu-id="abc06-171">B</span><span class="sxs-lookup"><span data-stu-id="abc06-171">B</span></span>|`'a'B`|
|<span data-ttu-id="abc06-172">byte[]</span><span class="sxs-lookup"><span data-stu-id="abc06-172">byte[]</span></span>|<span data-ttu-id="abc06-173">Cadeia de caracteres ASCII</span><span class="sxs-lookup"><span data-stu-id="abc06-173">ASCII string</span></span>|<span data-ttu-id="abc06-174">B</span><span class="sxs-lookup"><span data-stu-id="abc06-174">B</span></span>|`"text"B`|
|<span data-ttu-id="abc06-175">Cadeia de caracteres ou byte]</span><span class="sxs-lookup"><span data-stu-id="abc06-175">String or byte[]</span></span>|<span data-ttu-id="abc06-176">cadeia de caracteres textual</span><span class="sxs-lookup"><span data-stu-id="abc06-176">verbatim string</span></span>|<span data-ttu-id="abc06-177">prefixo @</span><span class="sxs-lookup"><span data-stu-id="abc06-177">@ prefix</span></span>|<span data-ttu-id="abc06-178">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="abc06-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="abc06-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="abc06-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="abc06-180">Comentários</span><span class="sxs-lookup"><span data-stu-id="abc06-180">Remarks</span></span>

<span data-ttu-id="abc06-181">Cadeias de caracteres Unicode podem conter as codificações explícitas que você pode especificar usando `\u` seguido por um código hexadecimal de 16 bits ou codificações UTF-32 que você pode especificar usando `\U` seguido por um código hexadecimal de 32 bits que representa a Unicode par substituto.</span><span class="sxs-lookup"><span data-stu-id="abc06-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="abc06-182">A partir do F # 3.1, você pode usar o `+` entrar para combinar literais de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="abc06-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="abc06-183">Você também pode usar o bit a bit ou (`|||`) operador para combinar sinalizadores de enum.</span><span class="sxs-lookup"><span data-stu-id="abc06-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="abc06-184">Por exemplo, o código a seguir é legal no F # 3.1:</span><span class="sxs-lookup"><span data-stu-id="abc06-184">For example, the following code is legal in F# 3.1:</span></span>

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

<span data-ttu-id="abc06-185">Não é permitido o uso de outros operadores bit a bit.</span><span class="sxs-lookup"><span data-stu-id="abc06-185">The use of other bitwise operators isn't allowed.</span></span>

## <a name="named-literals"></a><span data-ttu-id="abc06-186">Literais nomeados</span><span class="sxs-lookup"><span data-stu-id="abc06-186">Named Literals</span></span>

<span data-ttu-id="abc06-187">Os valores que devem ser constantes podem ser marcados com o [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atributo.</span><span class="sxs-lookup"><span data-stu-id="abc06-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="abc06-188">Este atributo tem o efeito de causar um valor a ser compilado como uma constante.</span><span class="sxs-lookup"><span data-stu-id="abc06-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="abc06-189">Em expressões de correspondência, identificadores que começam com caracteres minúsculos sempre são tratados como variáveis a serem associadas, em vez de como literais, portanto, você deve geralmente usar iniciais maiusculas ao definir literais.</span><span class="sxs-lookup"><span data-stu-id="abc06-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="abc06-190">Números inteiros em outras Bases</span><span class="sxs-lookup"><span data-stu-id="abc06-190">Integers In Other Bases</span></span>

<span data-ttu-id="abc06-191">Inteiros com sinal de 32 bits também podem ser especificados em octal, hexadecimal ou binário usando um `0x`, `0o` ou `0b` do prefixo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="abc06-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="abc06-192">Sublinhados em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="abc06-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="abc06-193">Começando com o F # 4.1, você pode separar dígitos com o caractere de sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="abc06-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="abc06-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abc06-194">See also</span></span>

- [<span data-ttu-id="abc06-195">Classe Core. literalattribute</span><span class="sxs-lookup"><span data-stu-id="abc06-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
