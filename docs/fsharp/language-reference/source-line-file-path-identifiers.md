---
title: Identificadores de linha, arquivo e caminho de origem
description: Saiba como usar interno F# valores do identificador que permitem que você acessar a fonte de linha número, diretório e nome de arquivo em seu código.
ms.date: 05/16/2016
ms.openlocfilehash: 3f2048aed9ef75037b43cd091a749e3d6bbaf9a3
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152059"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="b6ac0-103">Identificadores de linha, arquivo e caminho de origem</span><span class="sxs-lookup"><span data-stu-id="b6ac0-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="b6ac0-104">Os identificadores `__LINE__`, `__SOURCE_DIRECTORY__` e `__SOURCE_FILE__` são valores internos que permitem que você acesse o nome de arquivo e diretório, número da linha de código-fonte em seu código.</span><span class="sxs-lookup"><span data-stu-id="b6ac0-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6ac0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6ac0-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="b6ac0-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6ac0-106">Remarks</span></span>

<span data-ttu-id="b6ac0-107">Cada um desses valores tem tipo `string`.</span><span class="sxs-lookup"><span data-stu-id="b6ac0-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="b6ac0-108">A tabela a seguir resume os identificadores de linha, arquivo e caminho de origem que estão disponíveis no F#.</span><span class="sxs-lookup"><span data-stu-id="b6ac0-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="b6ac0-109">Esses identificadores não são macros de pré-processador; eles são valores internos que são reconhecidos pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="b6ac0-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="b6ac0-110">Identificador predefinido</span><span class="sxs-lookup"><span data-stu-id="b6ac0-110">Predefined identifier</span></span>|<span data-ttu-id="b6ac0-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6ac0-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="b6ac0-112">Retorna o número de linha atual, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="b6ac0-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="b6ac0-113">É avaliada como o caminho completo atual do diretório de origem, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="b6ac0-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="b6ac0-114">É avaliada como o nome de arquivo de origem atual, sem o caminho, considerando `#line` diretivas.</span><span class="sxs-lookup"><span data-stu-id="b6ac0-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="b6ac0-115">Para obter mais informações sobre o `#line` diretiva, consulte [diretivas de compilador](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="b6ac0-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="b6ac0-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6ac0-116">Example</span></span>

<span data-ttu-id="b6ac0-117">O exemplo de código a seguir demonstra o uso desses valores.</span><span class="sxs-lookup"><span data-stu-id="b6ac0-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="b6ac0-118">Saída:</span><span class="sxs-lookup"><span data-stu-id="b6ac0-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="b6ac0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6ac0-119">See also</span></span>

- [<span data-ttu-id="b6ac0-120">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="b6ac0-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="b6ac0-121">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="b6ac0-121">F# Language Reference</span></span>](index.md)
