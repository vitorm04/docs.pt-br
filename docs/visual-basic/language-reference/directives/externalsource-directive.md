---
title: '#Diretiva ExternalSource | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
dev_langs:
- VB
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
caps.latest.revision: 160
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 45de46e1a30848c87a691a10c2255eff7f798975
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="externalsource-directive"></a>#<span data-ttu-id="8ccdf-102">Diretiva ExternalSource</span><span class="sxs-lookup"><span data-stu-id="8ccdf-102">ExternalSource Directive</span></span>
<span data-ttu-id="8ccdf-103">Indica um mapeamento entre linhas específicas do código-fonte e texto externo a fonte.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ccdf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ccdf-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="8ccdf-105">Partes</span><span class="sxs-lookup"><span data-stu-id="8ccdf-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="8ccdf-106">O caminho para a fonte externa.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="8ccdf-107">O número de linha da primeira linha da fonte externa.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="8ccdf-108">A linha onde o erro ocorre na fonte externa.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="8ccdf-109">Encerra o `#ExternalSource` bloco.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ccdf-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ccdf-110">Remarks</span></span>  
 <span data-ttu-id="8ccdf-111">Essa diretiva é usada somente pelo compilador e o depurador.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="8ccdf-112">Um arquivo de origem pode incluir diretivas de fonte externa, que indicam um mapeamento entre linhas específicas do código no arquivo de origem e o texto externo à fonte, como um arquivo. aspx.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="8ccdf-113">Se forem encontrados erros no código-fonte designado durante a compilação, eles são identificados como provenientes de fonte externa.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="8ccdf-114">Diretivas de fonte externa não têm efeito na compilação e não podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="8ccdf-115">Eles são destinados a uso interno pelo aplicativo somente.</span><span class="sxs-lookup"><span data-stu-id="8ccdf-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccdf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ccdf-116">See Also</span></span>  
 [<span data-ttu-id="8ccdf-117">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="8ccdf-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
