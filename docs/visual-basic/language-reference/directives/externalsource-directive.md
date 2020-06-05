---
title: '#Diretiva ExternalSource'
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
ms.openlocfilehash: e4c7704c32c3a6c73e069d0b7129d5386696b438
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402986"
---
# <a name="externalsource-directive"></a><span data-ttu-id="61489-102">Diretiva #ExternalSource</span><span class="sxs-lookup"><span data-stu-id="61489-102">#ExternalSource Directive</span></span>

<span data-ttu-id="61489-103">Indica um mapeamento entre linhas específicas de código-fonte e texto externo à origem.</span><span class="sxs-lookup"><span data-stu-id="61489-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61489-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61489-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="61489-105">Partes</span><span class="sxs-lookup"><span data-stu-id="61489-105">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="61489-106">O caminho para a fonte externa.</span><span class="sxs-lookup"><span data-stu-id="61489-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="61489-107">O número de linha da primeira linha da fonte externa.</span><span class="sxs-lookup"><span data-stu-id="61489-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="61489-108">A linha em que o erro ocorre na fonte externa.</span><span class="sxs-lookup"><span data-stu-id="61489-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="61489-109">Encerra o `#ExternalSource` bloco.</span><span class="sxs-lookup"><span data-stu-id="61489-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61489-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="61489-110">Remarks</span></span>  

 <span data-ttu-id="61489-111">Essa diretiva é usada somente pelo compilador e pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="61489-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="61489-112">Um arquivo de origem pode incluir diretivas de origem externas, que indicam um mapeamento entre linhas específicas de código no arquivo de origem e o texto externo à fonte, como um arquivo. aspx.</span><span class="sxs-lookup"><span data-stu-id="61489-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="61489-113">Se forem encontrados erros no código-fonte designado durante a compilação, eles serão identificados como provenientes da fonte externa.</span><span class="sxs-lookup"><span data-stu-id="61489-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="61489-114">As diretivas de origem externa não têm nenhum efeito na compilação e não podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="61489-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="61489-115">Eles são destinados ao uso interno somente pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61489-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61489-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="61489-116">See also</span></span>

- [<span data-ttu-id="61489-117">Compilação condicional</span><span class="sxs-lookup"><span data-stu-id="61489-117">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
