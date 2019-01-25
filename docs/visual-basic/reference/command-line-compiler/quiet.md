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
ms.openlocfilehash: dfa85141e791cfcb28cfc6d216781f0cf14c2e4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624139"
---
# <a name="-quiet"></a><span data-ttu-id="263ce-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="263ce-102">-quiet</span></span>
<span data-ttu-id="263ce-103">Impede que o compilador exibindo o código para avisos e erros de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="263ce-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="263ce-104">Syntax</span></span>  
  
```  
-quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="263ce-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="263ce-105">Remarks</span></span>  
 <span data-ttu-id="263ce-106">Por padrão, `-quiet` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="263ce-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="263ce-107">Quando o compilador relatará um erro de sintaxe ou aviso, ele também produz a linha do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="263ce-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="263ce-108">Para aplicativos que analisar a saída do compilador, pode ser mais conveniente para o compilador gerar apenas o texto do diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="263ce-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="263ce-109">No exemplo a seguir `Module1` gera um erro que inclui código-fonte quando compilado sem `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="263ce-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="263ce-110">Saída:</span><span class="sxs-lookup"><span data-stu-id="263ce-110">Output:</span></span>  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 <span data-ttu-id="263ce-111">Compilado com `-quiet`, o compilador gera apenas o seguinte:</span><span class="sxs-lookup"><span data-stu-id="263ce-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="263ce-112">O `-quiet` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="263ce-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="263ce-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="263ce-113">Example</span></span>  
 <span data-ttu-id="263ce-114">O seguinte código compila `T2.vb` e não exibe o código para o diagnóstico de compilador relacionados com a sintaxe:</span><span class="sxs-lookup"><span data-stu-id="263ce-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="263ce-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="263ce-115">See also</span></span>
- [<span data-ttu-id="263ce-116">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="263ce-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="263ce-117">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="263ce-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
