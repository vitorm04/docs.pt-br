---
title: Identificadores de linha, arquivo e demarcador de origem (F#)
description: 'Saiba como usar o F # identificador valores internos que permitem que você acesse o número de linha de origem, o diretório e o nome do arquivo no seu código.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 18a26f0aa0a0c1f9c0b448ec46eaebd540391324
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="54498-103">Identificadores de linha, arquivo e demarcador de origem</span><span class="sxs-lookup"><span data-stu-id="54498-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="54498-104">Os identificadores de `__LINE__`, `__SOURCE_DIRECTORY__` e `__SOURCE_FILE__` são valores internos que permitem acessar o nome de arquivo e diretório, número da linha de código-fonte em seu código.</span><span class="sxs-lookup"><span data-stu-id="54498-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="54498-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54498-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="54498-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="54498-106">Remarks</span></span>
<span data-ttu-id="54498-107">Cada um desses valores tem tipo `string`.</span><span class="sxs-lookup"><span data-stu-id="54498-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="54498-108">A tabela a seguir resume os identificadores de caminho que estão disponíveis no F #, de arquivo e a linha de origem.</span><span class="sxs-lookup"><span data-stu-id="54498-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="54498-109">Esses identificadores não são macros de pré-processador; eles são valores internos que são reconhecidos pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="54498-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="54498-110">Identificador predefinida</span><span class="sxs-lookup"><span data-stu-id="54498-110">Predefined identifier</span></span>|<span data-ttu-id="54498-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="54498-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="54498-112">Retorna o número da linha atual, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="54498-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="54498-113">Avalia o caminho completo atual do diretório de origem, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="54498-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="54498-114">É avaliada como o nome de arquivo de origem atual e seu caminho, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="54498-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="54498-115">Para obter mais informações sobre o `#line` diretiva, consulte [diretivas de compilador](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="54498-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="54498-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54498-116">Example</span></span>

<span data-ttu-id="54498-117">O exemplo de código a seguir demonstra o uso desses valores.</span><span class="sxs-lookup"><span data-stu-id="54498-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="54498-118">Saída:</span><span class="sxs-lookup"><span data-stu-id="54498-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="54498-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54498-119">See Also</span></span>
[<span data-ttu-id="54498-120">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="54498-120">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="54498-121">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="54498-121">F# Language Reference</span></span>](index.md)
