---
title: Especificando nomes de tipo totalmente qualificados
ms.date: 03/14/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9281906f5500d954f3a0c7abface4ee43adcb64d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628533"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="ca8c3-102">Especificando nomes de tipo totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="ca8c3-102">Specifying Fully Qualified Type Names</span></span>
<span data-ttu-id="ca8c3-103">Você deve especificar nomes de tipo para ter uma entrada válida para várias operações de reflexão.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="ca8c3-104">Um nome de tipo totalmente qualificado consiste em uma especificação de nome de assembly, uma especificação de namespace e um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="ca8c3-105">Especificações de nome de tipo são usadas por métodos como <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> e <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="grammar-for-type-names"></a><span data-ttu-id="ca8c3-106">Gramática para nomes de tipo</span><span class="sxs-lookup"><span data-stu-id="ca8c3-106">Grammar for Type Names</span></span>  
 <span data-ttu-id="ca8c3-107">A gramática define a sintaxe de linguagens formais.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="ca8c3-108">A tabela a seguir lista as regras lexicais que descrevem como reconhecer uma entrada válida.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="ca8c3-109">Terminais (elementos que não poder ser mais reduzidos) são mostrados em letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="ca8c3-110">Não terminais (elementos que ainda podem ser reduzidos) são mostrados em cadeias de caracteres combinando maiúsculas e minúsculas ou entre aspas simples, porém a aspa simples (') não faz parte da sintaxe em si.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="ca8c3-111">O caractere de barra vertical (&#124;) indica que as regras que têm sub-regras.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>  

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
    | ArrayTypeSpec
    | TypeName
    ;

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

## <a name="specifying-special-characters"></a><span data-ttu-id="ca8c3-112">Especificando caracteres especiais</span><span class="sxs-lookup"><span data-stu-id="ca8c3-112">Specifying Special Characters</span></span>  
 <span data-ttu-id="ca8c3-113">Em um nome de tipo, IDENTIFIER é qualquer nome válido determinado pelas regras de uma linguagem.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>  
  
 <span data-ttu-id="ca8c3-114">Use a barra invertida (\\) como um caractere de escape para separar os seguintes tokens quando usados como parte do IDENTIFIER.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>  
  
|<span data-ttu-id="ca8c3-115">Token</span><span class="sxs-lookup"><span data-stu-id="ca8c3-115">Token</span></span>|<span data-ttu-id="ca8c3-116">Significado</span><span class="sxs-lookup"><span data-stu-id="ca8c3-116">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="ca8c3-117">\\,</span><span class="sxs-lookup"><span data-stu-id="ca8c3-117">\\,</span></span>|<span data-ttu-id="ca8c3-118">Separador de assembly.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-118">Assembly separator.</span></span>|  
|\\+|<span data-ttu-id="ca8c3-119">Separador de tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-119">Nested type separator.</span></span>|  
|\\&|<span data-ttu-id="ca8c3-120">Tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-120">Reference type.</span></span>|  
|\\*|<span data-ttu-id="ca8c3-121">Tipo do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-121">Pointer type.</span></span>|  
|<span data-ttu-id="ca8c3-122">\\[</span><span class="sxs-lookup"><span data-stu-id="ca8c3-122">\\[</span></span>|<span data-ttu-id="ca8c3-123">Delimitador de dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-123">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="ca8c3-124">\\]</span><span class="sxs-lookup"><span data-stu-id="ca8c3-124">\\]</span></span>|<span data-ttu-id="ca8c3-125">Delimitador de dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-125">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="ca8c3-126">\\.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-126">\\.</span></span>|<span data-ttu-id="ca8c3-127">Use a barra invertida antes de um ponto somente se ele for usado em uma especificação de matriz.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="ca8c3-128">Os pontos em NamespaceSpec não usam a barra invertida.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-128">Periods in NamespaceSpec do not take the backslash.</span></span>|  
|<span data-ttu-id="ca8c3-129">\\\|Barra invertida quando for necessária como uma cadeia de caracteres literal.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-129">\\\|Backslash when needed as a string literal.</span></span>|  
  
 <span data-ttu-id="ca8c3-130">Observe que, em todos os componentes de TypeSpec, exceto AssemblyNameSpec, os espaços são relevantes.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="ca8c3-131">No AssemblyNameSpec, os espaços antes do separador ',' são relevantes, mas espaços depois do separador ',' são ignorados.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>  
  
 <span data-ttu-id="ca8c3-132">Classes de reflexão, como <xref:System.Type.FullName%2A?displayProperty=nameWithType>, retornam o nome danificado, de forma que o nome retornado pode ser usado em uma chamada para <xref:System.Type.GetType%2A>, como em `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>  
  
 <span data-ttu-id="ca8c3-133">Por exemplo, o nome totalmente qualificado para um tipo pode ser `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
 <span data-ttu-id="ca8c3-134">Se o namespace fosse `Ozzy.Out+Back`, o sinal de adição deve ser precedido por uma barra invertida.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="ca8c3-135">Caso contrário, o analisador o interpretaria como um separador de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="ca8c3-136">A reflexão emite essa cadeia de caracteres como `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
## <a name="specifying-assembly-names"></a><span data-ttu-id="ca8c3-137">Especificando nomes de assembly</span><span class="sxs-lookup"><span data-stu-id="ca8c3-137">Specifying Assembly Names</span></span>  
 <span data-ttu-id="ca8c3-138">A informação mínima necessária em uma especificação de nome do assembly é o nome textual (IDENTIFIER) do assembly.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="ca8c3-139">Você pode seguir o IDENTIFIER de uma lista separada por vírgulas de pares propriedade/valor, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="ca8c3-140">A nomenclatura do IDENTIFIER deve seguir as regras de nomenclatura de arquivo.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="ca8c3-141">O IDENTIFIER não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-141">The IDENTIFIER is case-insensitive.</span></span>  
  
|<span data-ttu-id="ca8c3-142">Property name</span><span class="sxs-lookup"><span data-stu-id="ca8c3-142">Property name</span></span>|<span data-ttu-id="ca8c3-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca8c3-143">Description</span></span>|<span data-ttu-id="ca8c3-144">Valores permitidos</span><span class="sxs-lookup"><span data-stu-id="ca8c3-144">Allowable values</span></span>|  
|-------------------|-----------------|----------------------|  
|<span data-ttu-id="ca8c3-145">**Versão**</span><span class="sxs-lookup"><span data-stu-id="ca8c3-145">**Version**</span></span>|<span data-ttu-id="ca8c3-146">Número de versão do assembly</span><span class="sxs-lookup"><span data-stu-id="ca8c3-146">Assembly version number</span></span>|<span data-ttu-id="ca8c3-147">*Major.Minor.Build.Revision*, em que *Major*, *Minor*, *Build* e *Revision* são inteiro entre 0 e 65535, inclusive.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|  
|<span data-ttu-id="ca8c3-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="ca8c3-148">**PublicKey**</span></span>|<span data-ttu-id="ca8c3-149">Chave pública completa</span><span class="sxs-lookup"><span data-stu-id="ca8c3-149">Full public key</span></span>|<span data-ttu-id="ca8c3-150">O valor da cadeia de caracteres da chave pública completa em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="ca8c3-151">Especifique uma referência nula (**Nothing** no Visual Basic) para indicar explicitamente um assembly particular.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="ca8c3-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="ca8c3-152">**PublicKeyToken**</span></span>|<span data-ttu-id="ca8c3-153">Token de chave pública (hash de 8 bytes da chave pública completa)</span><span class="sxs-lookup"><span data-stu-id="ca8c3-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="ca8c3-154">Valor da cadeia de caracteres do token de chave pública em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="ca8c3-155">Especifique uma referência nula (**Nothing** no Visual Basic) para indicar explicitamente um assembly particular.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="ca8c3-156">**Cultura**</span><span class="sxs-lookup"><span data-stu-id="ca8c3-156">**Culture**</span></span>|<span data-ttu-id="ca8c3-157">Cultura do assembly</span><span class="sxs-lookup"><span data-stu-id="ca8c3-157">Assembly culture</span></span>|<span data-ttu-id="ca8c3-158">A cultura do assembly no formato RFC-1766 ou “neutra” para assemblies independente de linguagem (não satélite).</span><span class="sxs-lookup"><span data-stu-id="ca8c3-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|  
|<span data-ttu-id="ca8c3-159">**Personalizado**</span><span class="sxs-lookup"><span data-stu-id="ca8c3-159">**Custom**</span></span>|<span data-ttu-id="ca8c3-160">BLOB (objeto binário grande) personalizado.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="ca8c3-161">No momento, isso é usado apenas em assemblies gerados pelo [Ngen (Gerador de Imagens Nativas)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="ca8c3-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="ca8c3-162">A cadeia de caracteres personalizada usada pela ferramenta do Gerador de Imagens Nativas para notificar o cache de assembly que o assembly que está sendo instalado é uma imagem nativa e, portanto, deve ser instalada no cache de imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="ca8c3-163">Também chamado de cadeia de caracteres zap.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-163">Also called a zap string.</span></span>|  
  
 <span data-ttu-id="ca8c3-164">A exemplo a seguir mostra um **AssemblyName** para um assembly de nome simples com cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 <span data-ttu-id="ca8c3-165">O exemplo a seguir mostra uma referência totalmente especificada para um assembly de nome forte com a cultura “en”.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 <span data-ttu-id="ca8c3-166">Todos os exemplos a seguir mostram **AssemblyName** parcialmente especificado, que pode ser atendido por um assembly de nome forte ou simples.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 <span data-ttu-id="ca8c3-167">Todos os exemplos a seguir mostram um **AssemblyName** parcialmente especificado, que deve ser atendido por um assembly de nome simples.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 <span data-ttu-id="ca8c3-168">Todos os exemplos a seguir mostram um **AssemblyName** parcialmente especificado, que deve ser atendido por um assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a><span data-ttu-id="ca8c3-169">Especificando ponteiros</span><span class="sxs-lookup"><span data-stu-id="ca8c3-169">Specifying Pointers</span></span>  
 <span data-ttu-id="ca8c3-170">SimpleTypeSpec\* representa um ponteiro não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-170">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="ca8c3-171">Por exemplo, para obter um ponteiro para o tipo MyType, use `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-171">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="ca8c3-172">Para obter um ponteiro para o tipo MyType, use `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-172">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>  
  
## <a name="specifying-references"></a><span data-ttu-id="ca8c3-173">Especificando referências</span><span class="sxs-lookup"><span data-stu-id="ca8c3-173">Specifying References</span></span>  
 <span data-ttu-id="ca8c3-174">SimpleTypeSpec & representa um ponteiro ou referência gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-174">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="ca8c3-175">Por exemplo, para obter uma referência ao tipo MyType, use `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-175">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="ca8c3-176">Observe que, ao contrário dos ponteiros, as referências são limitadas a um nível.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-176">Note that unlike pointers, references are limited to one level.</span></span>  
  
## <a name="specifying-arrays"></a><span data-ttu-id="ca8c3-177">Especificando matrizes</span><span class="sxs-lookup"><span data-stu-id="ca8c3-177">Specifying Arrays</span></span>  
 <span data-ttu-id="ca8c3-178">Na Gramática BNF, ReflectionEmitDimension só se aplica às definições de tipo incompletas recuperadas usando <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-178">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ca8c3-179">As definições de tipo incompletas são objetos <xref:System.Reflection.Emit.TypeBuilder> construídos usando <xref:System.Reflection.Emit?displayProperty=nameWithType>, mas no qual <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> não foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-179">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="ca8c3-180">É possível usar ReflectionDimension para recuperar qualquer definição de tipo que foi concluída, ou seja, um tipo que foi carregado.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-180">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>  
  
 <span data-ttu-id="ca8c3-181">Matrizes são acessadas na reflexão ao especificar a classificação da matriz:</span><span class="sxs-lookup"><span data-stu-id="ca8c3-181">Arrays are accessed in reflection by specifying the rank of the array:</span></span>  
  
-   <span data-ttu-id="ca8c3-182">`Type.GetType("MyArray[]")` obtém uma matriz de dimensão única com o limite inferior 0.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-182">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>  
  
-   <span data-ttu-id="ca8c3-183">`Type.GetType("MyArray[*]")` obtém uma matriz de dimensão única com limite inferior desconhecido.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-183">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>  
  
-   <span data-ttu-id="ca8c3-184">`Type.GetType("MyArray[][]")` recebe uma matriz bidimensional.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-184">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>  
  
-   <span data-ttu-id="ca8c3-185">`Type.GetType("MyArray[*,*]")` e `Type.GetType("MyArray[,]")` obtém uma matriz bidimensional retangular com limites inferiores desconhecidos.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-185">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>  
  
 <span data-ttu-id="ca8c3-186">Observe que, do ponto de vista do tempo de execução, `MyArray[] != MyArray[*]`, mas para matrizes multidimensionais, as duas notações são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-186">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="ca8c3-187">Ou seja, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` é avaliada como **true**.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-187">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>  
  
 <span data-ttu-id="ca8c3-188">Para **ModuleBuilder.GetType**, `MyArray[0..5]` indica uma matriz de dimensão única com tamanho 6 e limite inferior 0.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-188">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="ca8c3-189">`MyArray[4…]` indica uma matriz de dimensão única de tamanho desconhecido e limite inferior 4.</span><span class="sxs-lookup"><span data-stu-id="ca8c3-189">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca8c3-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca8c3-190">See also</span></span>
- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ca8c3-191">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="ca8c3-191">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
