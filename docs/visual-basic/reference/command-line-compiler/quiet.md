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
ms.openlocfilehash: a22773e2e37eb60ab6f1e88305266f41764311e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788837"
---
# <a name="-quiet"></a><span data-ttu-id="0cbb9-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="0cbb9-102">-quiet</span></span>

<span data-ttu-id="0cbb9-103">Impede que o compilador exibindo o código para avisos e erros de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="0cbb9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0cbb9-104">Syntax</span></span>

```
-quiet
```

## <a name="remarks"></a><span data-ttu-id="0cbb9-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="0cbb9-105">Remarks</span></span>

<span data-ttu-id="0cbb9-106">Por padrão, `-quiet` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="0cbb9-107">Quando o compilador relatará um erro de sintaxe ou aviso, ele também produz a linha do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="0cbb9-108">Para aplicativos que analisar a saída do compilador, pode ser mais conveniente para o compilador gerar apenas o texto do diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="0cbb9-109">No exemplo a seguir `Module1` gera um erro que inclui código-fonte quando compilado sem `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="0cbb9-110">Saída:</span><span class="sxs-lookup"><span data-stu-id="0cbb9-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="0cbb9-111">Compilado com `-quiet`, o compilador gera apenas o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0cbb9-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="0cbb9-112">O `-quiet` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="0cbb9-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="0cbb9-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0cbb9-113">Example</span></span>

<span data-ttu-id="0cbb9-114">O seguinte código compila `T2.vb` e não exibe o código para o diagnóstico de compilador relacionados com a sintaxe:</span><span class="sxs-lookup"><span data-stu-id="0cbb9-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="0cbb9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cbb9-115">See also</span></span>

- [<span data-ttu-id="0cbb9-116">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cbb9-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0cbb9-117">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="0cbb9-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
