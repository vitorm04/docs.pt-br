---
title: Identificadores de linha, arquivo e demarcador de origem (F#)
description: Saiba como usar F# identificador valores internos que permitem que você acesse o número de linha de código-fonte, o diretório e o nome do arquivo em seu código.
ms.date: 05/16/2016
ms.openlocfilehash: 14f710d1412c3420ec627dc30216ba2e89f16bcd
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865121"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="5792e-103">Identificadores de linha, arquivo e demarcador de origem</span><span class="sxs-lookup"><span data-stu-id="5792e-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="5792e-104">Os identificadores `__LINE__`, `__SOURCE_DIRECTORY__` e `__SOURCE_FILE__` são valores internos que permitem que você acesse o nome de arquivo e diretório, número da linha de código-fonte em seu código.</span><span class="sxs-lookup"><span data-stu-id="5792e-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="5792e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5792e-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="5792e-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="5792e-106">Remarks</span></span>

<span data-ttu-id="5792e-107">Cada um desses valores tem tipo `string`.</span><span class="sxs-lookup"><span data-stu-id="5792e-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="5792e-108">A tabela a seguir resume a linha de código-fonte, arquivos e identificadores de caminho que estão disponíveis no F#.</span><span class="sxs-lookup"><span data-stu-id="5792e-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="5792e-109">Esses identificadores não são macros de pré-processador; eles são valores internos que são reconhecidos pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="5792e-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="5792e-110">Identificador predefinido</span><span class="sxs-lookup"><span data-stu-id="5792e-110">Predefined identifier</span></span>|<span data-ttu-id="5792e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="5792e-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="5792e-112">Retorna o número de linha atual, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="5792e-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="5792e-113">É avaliada como o caminho completo atual do diretório de origem, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="5792e-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="5792e-114">É avaliada como o nome do arquivo de origem atual e seu caminho, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="5792e-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="5792e-115">Para obter mais informações sobre o `#line` diretiva, consulte [diretivas de compilador](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="5792e-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="5792e-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5792e-116">Example</span></span>

<span data-ttu-id="5792e-117">O exemplo de código a seguir demonstra o uso desses valores.</span><span class="sxs-lookup"><span data-stu-id="5792e-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="5792e-118">Saída:</span><span class="sxs-lookup"><span data-stu-id="5792e-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="5792e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5792e-119">See also</span></span>

- [<span data-ttu-id="5792e-120">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="5792e-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="5792e-121">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="5792e-121">F# Language Reference</span></span>](index.md)
