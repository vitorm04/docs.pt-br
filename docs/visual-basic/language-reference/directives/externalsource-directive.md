---
title: '#<a name="externalsource-directive"></a>Diretiva ExternalSource'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="externalsource-directive"></a><span data-ttu-id="c8798-102">Diretiva #ExternalSource</span><span class="sxs-lookup"><span data-stu-id="c8798-102">#ExternalSource Directive</span></span>
<span data-ttu-id="c8798-103">Indica um mapeamento entre linhas específicas do código-fonte e externo para a fonte do texto.</span><span class="sxs-lookup"><span data-stu-id="c8798-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8798-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8798-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="c8798-105">Partes</span><span class="sxs-lookup"><span data-stu-id="c8798-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="c8798-106">O caminho para a fonte externa.</span><span class="sxs-lookup"><span data-stu-id="c8798-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="c8798-107">O número de linha da primeira linha da fonte externa.</span><span class="sxs-lookup"><span data-stu-id="c8798-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="c8798-108">A linha onde o erro ocorre na origem externa.</span><span class="sxs-lookup"><span data-stu-id="c8798-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="c8798-109">Encerra o `#ExternalSource` bloco.</span><span class="sxs-lookup"><span data-stu-id="c8798-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8798-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8798-110">Remarks</span></span>  
 <span data-ttu-id="c8798-111">Essa diretiva é usada somente pelo compilador e o depurador.</span><span class="sxs-lookup"><span data-stu-id="c8798-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="c8798-112">Um arquivo de origem pode incluir diretivas de fonte externa, que indicam um mapeamento entre linhas específicas do código no arquivo de origem e o texto externo à fonte, como um arquivo. aspx.</span><span class="sxs-lookup"><span data-stu-id="c8798-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="c8798-113">Se forem encontrados erros no código-fonte designado durante a compilação, eles são identificados como provenientes da fonte externa.</span><span class="sxs-lookup"><span data-stu-id="c8798-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="c8798-114">Diretivas de fonte externa não têm nenhum efeito na compilação e não podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="c8798-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="c8798-115">Eles são destinados a uso interno pelo aplicativo somente.</span><span class="sxs-lookup"><span data-stu-id="c8798-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8798-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8798-116">See Also</span></span>  
 [<span data-ttu-id="c8798-117">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="c8798-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
