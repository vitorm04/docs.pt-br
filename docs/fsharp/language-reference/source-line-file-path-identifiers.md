---
title: Identificadores de linha, arquivo e demarcador de origem (F#)
description: "Saiba como usar o F # identificador valores internos que permitem que você acesse o número de linha de origem, o diretório e o nome do arquivo no seu código."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4cfe7439-275c-4d08-980b-784e240bbf29
ms.openlocfilehash: 44cc0914226c120f2b877ce3decd25caa6817eec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="a21e1-104">Identificadores de linha, arquivo e demarcador de origem</span><span class="sxs-lookup"><span data-stu-id="a21e1-104">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="a21e1-105">Os identificadores de `__LINE__`, `__SOURCE_DIRECTORY__` e `__SOURCE_FILE__` são valores internos que permitem acessar o nome de arquivo e diretório, número da linha de código-fonte em seu código.</span><span class="sxs-lookup"><span data-stu-id="a21e1-105">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="a21e1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a21e1-106">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="a21e1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a21e1-107">Remarks</span></span>
<span data-ttu-id="a21e1-108">Cada um desses valores tem tipo `string`.</span><span class="sxs-lookup"><span data-stu-id="a21e1-108">Each of these values has type `string`.</span></span>

<span data-ttu-id="a21e1-109">A tabela a seguir resume os identificadores de caminho que estão disponíveis no F #, de arquivo e a linha de origem.</span><span class="sxs-lookup"><span data-stu-id="a21e1-109">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="a21e1-110">Esses identificadores não são macros de pré-processador; eles são valores internos que são reconhecidos pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="a21e1-110">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="a21e1-111">Identificador predefinida</span><span class="sxs-lookup"><span data-stu-id="a21e1-111">Predefined identifier</span></span>|<span data-ttu-id="a21e1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a21e1-112">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="a21e1-113">Retorna o número da linha atual, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="a21e1-113">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="a21e1-114">Avalia o caminho completo atual do diretório de origem, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="a21e1-114">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="a21e1-115">É avaliada como o nome de arquivo de origem atual e seu caminho, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="a21e1-115">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="a21e1-116">Para obter mais informações sobre o `#line` diretiva, consulte [diretivas de compilador](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="a21e1-116">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="a21e1-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a21e1-117">Example</span></span>

<span data-ttu-id="a21e1-118">O exemplo de código a seguir demonstra o uso desses valores.</span><span class="sxs-lookup"><span data-stu-id="a21e1-118">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="a21e1-119">Saída:</span><span class="sxs-lookup"><span data-stu-id="a21e1-119">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="a21e1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a21e1-120">See Also</span></span>
[<span data-ttu-id="a21e1-121">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="a21e1-121">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="a21e1-122">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="a21e1-122">F# Language Reference</span></span>](index.md)
