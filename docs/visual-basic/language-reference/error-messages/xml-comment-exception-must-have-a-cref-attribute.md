---
title: Exceção de comentário XML deve ter um &#39;cref&#39; atributo
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: ee91513ef94e2abbe01d3ac09796b7fdf8e129ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="0f22f-102">Exceção de comentário XML deve ter um &#39;cref&#39; atributo</span><span class="sxs-lookup"><span data-stu-id="0f22f-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="0f22f-103">O \<exceção > marca fornece uma maneira para documentar as exceções que podem ser acionadas por um método.</span><span class="sxs-lookup"><span data-stu-id="0f22f-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="0f22f-104">Obrigatório `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação.</span><span class="sxs-lookup"><span data-stu-id="0f22f-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="0f22f-105">Se o membro existe, ele é convertido para o nome canônico de elemento no arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="0f22f-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="0f22f-106">**ID do erro:** BC42319</span><span class="sxs-lookup"><span data-stu-id="0f22f-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f22f-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0f22f-107">To correct this error</span></span>  
  
-   <span data-ttu-id="0f22f-108">Adicionar o `cref` atributo à exceção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0f22f-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0f22f-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f22f-109">See Also</span></span>  
 [<span data-ttu-id="0f22f-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="0f22f-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="0f22f-111">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="0f22f-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="0f22f-112">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="0f22f-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
