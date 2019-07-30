---
title: Identificadores de linha, arquivo e caminho de origem
description: Saiba como usar valores de F# identificador internos que permitem que você acesse o número da linha de origem, o diretório e o nome do arquivo em seu código.
ms.date: 05/16/2016
ms.openlocfilehash: 5ff36210edc75370f8baf9ee7be057f3ac0c3979
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627121"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="b4cbe-103">Identificadores de linha, arquivo e caminho de origem</span><span class="sxs-lookup"><span data-stu-id="b4cbe-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="b4cbe-104">Os identificadores `__LINE__` `__SOURCE_DIRECTORY__` e`__SOURCE_FILE__` são valores internos que permitem que você acesse o número da linha de origem, o diretório e o nome do arquivo em seu código.</span><span class="sxs-lookup"><span data-stu-id="b4cbe-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="b4cbe-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4cbe-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="b4cbe-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4cbe-106">Remarks</span></span>

<span data-ttu-id="b4cbe-107">Cada um desses valores tem o `string`tipo.</span><span class="sxs-lookup"><span data-stu-id="b4cbe-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="b4cbe-108">A tabela a seguir resume os identificadores de linha de origem, arquivo e caminho que estão disponíveis F#no.</span><span class="sxs-lookup"><span data-stu-id="b4cbe-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="b4cbe-109">Esses identificadores não são macros de pré-processador; Eles são valores internos que são reconhecidos pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="b4cbe-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="b4cbe-110">Identificador predefinido</span><span class="sxs-lookup"><span data-stu-id="b4cbe-110">Predefined identifier</span></span>|<span data-ttu-id="b4cbe-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4cbe-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="b4cbe-112">Avalia o número da linha atual, considerando `#line` as diretivas.</span><span class="sxs-lookup"><span data-stu-id="b4cbe-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="b4cbe-113">Avalia o caminho completo atual do diretório de origem, considerando `#line` as diretivas.</span><span class="sxs-lookup"><span data-stu-id="b4cbe-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="b4cbe-114">Avalia o nome do arquivo de origem atual, sem o caminho, considerando `#line` as diretivas.</span><span class="sxs-lookup"><span data-stu-id="b4cbe-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="b4cbe-115">Para obter mais informações sobre `#line` a diretiva, consulte [diretivas do compilador](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="b4cbe-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4cbe-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4cbe-116">Example</span></span>

<span data-ttu-id="b4cbe-117">O exemplo de código a seguir demonstra o uso desses valores.</span><span class="sxs-lookup"><span data-stu-id="b4cbe-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="b4cbe-118">Saída:</span><span class="sxs-lookup"><span data-stu-id="b4cbe-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="b4cbe-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4cbe-119">See also</span></span>

- [<span data-ttu-id="b4cbe-120">Diretivas de Compilador</span><span class="sxs-lookup"><span data-stu-id="b4cbe-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="b4cbe-121">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="b4cbe-121">F# Language Reference</span></span>](index.md)
