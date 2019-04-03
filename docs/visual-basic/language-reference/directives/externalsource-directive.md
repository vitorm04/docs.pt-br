---
title: '#Diretiva ExternalSource (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 39e6963c97340daab3f0ab7ad6860695f1f6c135
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823422"
---
# <a name="externalsource-directive"></a><span data-ttu-id="64218-102">Diretiva #ExternalSource</span><span class="sxs-lookup"><span data-stu-id="64218-102">#ExternalSource Directive</span></span>
<span data-ttu-id="64218-103">Indica um mapeamento entre linhas específicas do código-fonte e texto externo à origem.</span><span class="sxs-lookup"><span data-stu-id="64218-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64218-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64218-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="64218-105">Partes</span><span class="sxs-lookup"><span data-stu-id="64218-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="64218-106">O caminho para a fonte externa.</span><span class="sxs-lookup"><span data-stu-id="64218-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="64218-107">O número de linha da primeira linha da fonte externa.</span><span class="sxs-lookup"><span data-stu-id="64218-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="64218-108">A linha onde o erro ocorre na fonte externa.</span><span class="sxs-lookup"><span data-stu-id="64218-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="64218-109">Encerra o `#ExternalSource` bloco.</span><span class="sxs-lookup"><span data-stu-id="64218-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64218-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="64218-110">Remarks</span></span>  
 <span data-ttu-id="64218-111">Essa diretiva é usada apenas pelo compilador e o depurador.</span><span class="sxs-lookup"><span data-stu-id="64218-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="64218-112">Um arquivo de origem pode incluir diretivas de fonte externa, que indicam um mapeamento entre linhas específicas do código no arquivo de origem e o texto externo à origem, como um arquivo. aspx.</span><span class="sxs-lookup"><span data-stu-id="64218-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="64218-113">Se forem encontrados erros no código-fonte designado durante a compilação, eles são identificados como proveniente da fonte externa.</span><span class="sxs-lookup"><span data-stu-id="64218-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="64218-114">Diretivas de fonte externa não têm nenhum efeito na compilação e não podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="64218-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="64218-115">Eles são destinados a uso interno por apenas o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64218-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64218-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64218-116">See also</span></span>

- [<span data-ttu-id="64218-117">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="64218-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
