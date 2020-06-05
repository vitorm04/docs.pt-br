---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: f894ed6a778e026ffd3976a63fe3b677eb6a9557
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400520"
---
# <a name="-quiet"></a><span data-ttu-id="b57fe-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="b57fe-102">-quiet</span></span>

<span data-ttu-id="b57fe-103">Impede que o compilador exiba código para erros e avisos relacionados à sintaxe.</span><span class="sxs-lookup"><span data-stu-id="b57fe-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="b57fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b57fe-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="b57fe-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b57fe-105">Remarks</span></span>

<span data-ttu-id="b57fe-106">Por padrão, `-quiet` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="b57fe-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="b57fe-107">Quando o compilador relata um erro ou aviso relacionado à sintaxe, ele também gera a linha do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b57fe-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="b57fe-108">Para aplicativos que analisam a saída do compilador, pode ser mais conveniente para o compilador gerar somente o texto do diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="b57fe-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="b57fe-109">No exemplo a seguir, `Module1` gera um erro que inclui o código-fonte quando compilado sem `-quiet` .</span><span class="sxs-lookup"><span data-stu-id="b57fe-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="b57fe-110">Saída:</span><span class="sxs-lookup"><span data-stu-id="b57fe-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="b57fe-111">Compilado com `-quiet` , o compilador gera apenas o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b57fe-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="b57fe-112">A `-quiet` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b57fe-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="b57fe-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b57fe-113">Example</span></span>

<span data-ttu-id="b57fe-114">O código a seguir compila `T2.vb` e não exibe código para diagnósticos de compilador relacionados à sintaxe:</span><span class="sxs-lookup"><span data-stu-id="b57fe-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="b57fe-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="b57fe-115">See also</span></span>

- [<span data-ttu-id="b57fe-116">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b57fe-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b57fe-117">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="b57fe-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
