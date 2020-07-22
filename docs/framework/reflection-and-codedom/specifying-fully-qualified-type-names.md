---
title: Especificando nomes de tipo totalmente qualificados
description: Para obter uma entrada válida para operações de reflexão, use nomes de tipo totalmente qualificado, que têm especificações de nome de assembly, especificações de namespace e nomes de tipo.
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
ms.openlocfilehash: ff33b6abd31a82c6b80aa794564c5c48648cde63
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865223"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="5ebe7-103">Especificar nomes de tipo totalmente qualificado</span><span class="sxs-lookup"><span data-stu-id="5ebe7-103">Specifying fully qualified type names</span></span>

<span data-ttu-id="5ebe7-104">Você deve especificar nomes de tipo para ter uma entrada válida para várias operações de reflexão.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-104">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="5ebe7-105">Um nome de tipo totalmente qualificado consiste em uma especificação de nome de assembly, uma especificação de namespace e um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-105">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="5ebe7-106">Especificações de nome de tipo são usadas por métodos como <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> e <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-106">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="5ebe7-107">Gramática para nomes de tipo</span><span class="sxs-lookup"><span data-stu-id="5ebe7-107">Grammar for type names</span></span>

 <span data-ttu-id="5ebe7-108">A gramática define a sintaxe de linguagens formais.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-108">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="5ebe7-109">A tabela a seguir lista as regras lexicais que descrevem como reconhecer uma entrada válida.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-109">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="5ebe7-110">Terminais (elementos que não poder ser mais reduzidos) são mostrados em letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-110">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="5ebe7-111">Não terminais (elementos que ainda podem ser reduzidos) são mostrados em cadeias de caracteres combinando maiúsculas e minúsculas ou entre aspas simples, porém a aspa simples (') não faz parte da sintaxe em si.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-111">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="5ebe7-112">O caractere de barra vertical (& #124;) indica que as regras que têm sub-regras.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-112">The pipe character (&#124;) denotes rules that have subrules.</span></span>

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a><span data-ttu-id="5ebe7-113">Especificar caracteres especiais</span><span class="sxs-lookup"><span data-stu-id="5ebe7-113">Specifying special characters</span></span>

<span data-ttu-id="5ebe7-114">Em um nome de tipo, IDENTIFIER é qualquer nome válido determinado pelas regras de uma linguagem.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-114">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="5ebe7-115">Use a barra invertida (\\) como um caractere de escape para separar os seguintes tokens quando usados como parte do IDENTIFIER.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-115">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="5ebe7-116">Token</span><span class="sxs-lookup"><span data-stu-id="5ebe7-116">Token</span></span>|<span data-ttu-id="5ebe7-117">Significado</span><span class="sxs-lookup"><span data-stu-id="5ebe7-117">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="5ebe7-118">\\,</span><span class="sxs-lookup"><span data-stu-id="5ebe7-118">\\,</span></span>|<span data-ttu-id="5ebe7-119">Separador de assembly.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-119">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="5ebe7-120">Separador de tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-120">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="5ebe7-121">Tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-121">Reference type.</span></span>|
|\\*|<span data-ttu-id="5ebe7-122">Tipo do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-122">Pointer type.</span></span>|
|<span data-ttu-id="5ebe7-123">\\[</span><span class="sxs-lookup"><span data-stu-id="5ebe7-123">\\[</span></span>|<span data-ttu-id="5ebe7-124">Delimitador de dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-124">Array dimension delimiter.</span></span>|
|<span data-ttu-id="5ebe7-125">\\]</span><span class="sxs-lookup"><span data-stu-id="5ebe7-125">\\]</span></span>|<span data-ttu-id="5ebe7-126">Delimitador de dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-126">Array dimension delimiter.</span></span>|
|<span data-ttu-id="5ebe7-127">\\.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-127">\\.</span></span>|<span data-ttu-id="5ebe7-128">Use a barra invertida antes de um ponto somente se ele for usado em uma especificação de matriz.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-128">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="5ebe7-129">Os pontos em NamespaceSpec não usam a barra invertida.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-129">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="5ebe7-130">\\\|Barra invertida quando for necessária como uma cadeia de caracteres literal.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-130">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="5ebe7-131">Observe que, em todos os componentes de TypeSpec, exceto AssemblyNameSpec, os espaços são relevantes.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-131">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="5ebe7-132">No AssemblyNameSpec, os espaços antes do separador ',' são relevantes, mas espaços depois do separador ',' são ignorados.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-132">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="5ebe7-133">Classes de reflexão, como <xref:System.Type.FullName%2A?displayProperty=nameWithType>, retornam o nome danificado, de forma que o nome retornado pode ser usado em uma chamada para <xref:System.Type.GetType%2A>, como em `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-133">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="5ebe7-134">Por exemplo, o nome totalmente qualificado para um tipo pode ser `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-134">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="5ebe7-135">Se o namespace fosse `Ozzy.Out+Back`, o sinal de adição deve ser precedido por uma barra invertida.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-135">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="5ebe7-136">Caso contrário, o analisador o interpretaria como um separador de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-136">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="5ebe7-137">A reflexão emite essa cadeia de caracteres como `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-137">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="5ebe7-138">Especificar nomes de assembly</span><span class="sxs-lookup"><span data-stu-id="5ebe7-138">Specifying assembly names</span></span>

<span data-ttu-id="5ebe7-139">A informação mínima necessária em uma especificação de nome do assembly é o nome textual (IDENTIFIER) do assembly.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-139">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="5ebe7-140">Você pode seguir o IDENTIFIER de uma lista separada por vírgulas de pares propriedade/valor, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-140">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="5ebe7-141">A nomenclatura do IDENTIFIER deve seguir as regras de nomenclatura de arquivo.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-141">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="5ebe7-142">O IDENTIFIER não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-142">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="5ebe7-143">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="5ebe7-143">Property name</span></span>|<span data-ttu-id="5ebe7-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ebe7-144">Description</span></span>|<span data-ttu-id="5ebe7-145">Valores permitidos</span><span class="sxs-lookup"><span data-stu-id="5ebe7-145">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="5ebe7-146">**Versão**</span><span class="sxs-lookup"><span data-stu-id="5ebe7-146">**Version**</span></span>|<span data-ttu-id="5ebe7-147">Número de versão do assembly</span><span class="sxs-lookup"><span data-stu-id="5ebe7-147">Assembly version number</span></span>|<span data-ttu-id="5ebe7-148">*Major.Minor.Build.Revision*, em que *Major*, *Minor*, *Build* e *Revision* são inteiro entre 0 e 65535, inclusive.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-148">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="5ebe7-149">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="5ebe7-149">**PublicKey**</span></span>|<span data-ttu-id="5ebe7-150">Chave pública completa</span><span class="sxs-lookup"><span data-stu-id="5ebe7-150">Full public key</span></span>|<span data-ttu-id="5ebe7-151">O valor da cadeia de caracteres da chave pública completa em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-151">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="5ebe7-152">Especifique uma referência nula (**Nothing** no Visual Basic) para indicar explicitamente um assembly particular.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-152">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="5ebe7-153">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="5ebe7-153">**PublicKeyToken**</span></span>|<span data-ttu-id="5ebe7-154">Token de chave pública (hash de 8 bytes da chave pública completa)</span><span class="sxs-lookup"><span data-stu-id="5ebe7-154">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="5ebe7-155">Valor da cadeia de caracteres do token de chave pública em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-155">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="5ebe7-156">Especifique uma referência nula (**Nothing** no Visual Basic) para indicar explicitamente um assembly particular.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-156">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="5ebe7-157">**Cultura**</span><span class="sxs-lookup"><span data-stu-id="5ebe7-157">**Culture**</span></span>|<span data-ttu-id="5ebe7-158">Cultura do assembly</span><span class="sxs-lookup"><span data-stu-id="5ebe7-158">Assembly culture</span></span>|<span data-ttu-id="5ebe7-159">A cultura do assembly no formato RFC-1766 ou “neutra” para assemblies independente de linguagem (não satélite).</span><span class="sxs-lookup"><span data-stu-id="5ebe7-159">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="5ebe7-160">**Custom**</span><span class="sxs-lookup"><span data-stu-id="5ebe7-160">**Custom**</span></span>|<span data-ttu-id="5ebe7-161">BLOB (objeto binário grande) personalizado.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-161">Custom binary large object (BLOB).</span></span> <span data-ttu-id="5ebe7-162">No momento, isso é usado apenas em assemblies gerados pelo [Ngen (Gerador de Imagens Nativas)](../tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="5ebe7-162">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="5ebe7-163">A cadeia de caracteres personalizada usada pela ferramenta do Gerador de Imagens Nativas para notificar o cache de assembly que o assembly que está sendo instalado é uma imagem nativa e, portanto, deve ser instalada no cache de imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-163">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="5ebe7-164">Também chamado de cadeia de caracteres zap.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-164">Also called a zap string.</span></span>|

<span data-ttu-id="5ebe7-165">A exemplo a seguir mostra um **AssemblyName** para um assembly de nome simples com cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-165">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="5ebe7-166">O exemplo a seguir mostra uma referência totalmente especificada para um assembly de nome forte com a cultura “en”.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-166">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="5ebe7-167">Todos os exemplos a seguir mostram **AssemblyName** parcialmente especificado, que pode ser atendido por um assembly de nome forte ou simples.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-167">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="5ebe7-168">Todos os exemplos a seguir mostram um **AssemblyName** parcialmente especificado, que deve ser atendido por um assembly de nome simples.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="5ebe7-169">Todos os exemplos a seguir mostram um **AssemblyName** parcialmente especificado, que deve ser atendido por um assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-169">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="5ebe7-170">Especificar tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="5ebe7-170">Specifying generic types</span></span>

<span data-ttu-id="5ebe7-171">SimpleTypeSpec\`NÚMERO representa um tipo genérico aberto com 1 a *n* parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-171">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="5ebe7-172">Por exemplo, para obter referência à lista de tipos genéricos abertos \<T> ou à lista de tipos genéricos fechados \<String> , use ``Type.GetType("System.Collections.Generic.List`1")`` para obter uma referência ao dicionário de tipo genérico \<TKey,TValue> , use ``Type.GetType("System.Collections.Generic.Dictionary`2")`` .</span><span class="sxs-lookup"><span data-stu-id="5ebe7-172">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="5ebe7-173">Especificar ponteiros</span><span class="sxs-lookup"><span data-stu-id="5ebe7-173">Specifying pointers</span></span>

<span data-ttu-id="5ebe7-174">SimpleTypeSpec\* representa um ponteiro não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-174">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="5ebe7-175">Por exemplo, para obter um ponteiro para o tipo MyType, use `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-175">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="5ebe7-176">Para obter um ponteiro para o tipo MyType, use `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-176">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="5ebe7-177">Especificar referências</span><span class="sxs-lookup"><span data-stu-id="5ebe7-177">Specifying references</span></span>

<span data-ttu-id="5ebe7-178">SimpleTypeSpec & representa um ponteiro ou referência gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-178">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="5ebe7-179">Por exemplo, para obter uma referência ao tipo MyType, use `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-179">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="5ebe7-180">Observe que, ao contrário dos ponteiros, as referências são limitadas a um nível.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-180">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="5ebe7-181">Especificar matrizes</span><span class="sxs-lookup"><span data-stu-id="5ebe7-181">Specifying arrays</span></span>

<span data-ttu-id="5ebe7-182">Na Gramática BNF, ReflectionEmitDimension só se aplica às definições de tipo incompletas recuperadas usando <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-182">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5ebe7-183">As definições de tipo incompletas são objetos <xref:System.Reflection.Emit.TypeBuilder> construídos usando <xref:System.Reflection.Emit?displayProperty=nameWithType>, mas no qual <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> não foi chamado.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-183">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="5ebe7-184">É possível usar ReflectionDimension para recuperar qualquer definição de tipo que foi concluída, ou seja, um tipo que foi carregado.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-184">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="5ebe7-185">Matrizes são acessadas na reflexão ao especificar a classificação da matriz:</span><span class="sxs-lookup"><span data-stu-id="5ebe7-185">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="5ebe7-186">`Type.GetType("MyArray[]")` obtém uma matriz de dimensão única com o limite inferior 0.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-186">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="5ebe7-187">`Type.GetType("MyArray[*]")` obtém uma matriz de dimensão única com limite inferior desconhecido.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-187">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="5ebe7-188">`Type.GetType("MyArray[][]")` recebe uma matriz bidimensional.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-188">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="5ebe7-189">`Type.GetType("MyArray[*,*]")` e `Type.GetType("MyArray[,]")` obtém uma matriz bidimensional retangular com limites inferiores desconhecidos.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-189">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="5ebe7-190">Observe que, do ponto de vista do runtime, `MyArray[] != MyArray[*]`, mas para matrizes multidimensionais, as duas notações são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-190">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="5ebe7-191">Ou seja, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` é avaliada como **true**.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-191">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="5ebe7-192">Para o o **. GetType**, `MyArray[0..5]` indica uma matriz de dimensão única com tamanho 6, menor limite 0.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-192">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="5ebe7-193">`MyArray[4…]` indica uma matriz de dimensão única de tamanho desconhecido e limite inferior 4.</span><span class="sxs-lookup"><span data-stu-id="5ebe7-193">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ebe7-194">Veja também</span><span class="sxs-lookup"><span data-stu-id="5ebe7-194">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5ebe7-195">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="5ebe7-195">Viewing Type Information</span></span>](viewing-type-information.md)
