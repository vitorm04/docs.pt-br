---
title: "O comentário XML exceção deve ter um atributo &quot;cref&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
dev_langs:
- VB
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 13
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
ms.openlocfilehash: bacec69ce62ad77186ff25060306204159c2b7f0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="59476-102">Exceção de comentário XML deve ter um atributo 'cref'</span><span class="sxs-lookup"><span data-stu-id="59476-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="59476-103">O \<exceção > marca fornece uma maneira para documentar as exceções que podem ser lançadas por um método.</span><span class="sxs-lookup"><span data-stu-id="59476-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="59476-104">Necessário `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação.</span><span class="sxs-lookup"><span data-stu-id="59476-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="59476-105">Se o membro existe, ele é convertido para o nome canônico de elemento no arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="59476-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="59476-106">**ID do erro:** BC42319</span><span class="sxs-lookup"><span data-stu-id="59476-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="59476-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="59476-107">To correct this error</span></span>  
  
-   <span data-ttu-id="59476-108">Adicionar o `cref` atributo à exceção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="59476-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="59476-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59476-109">See Also</span></span>  
 <span data-ttu-id="59476-110">[\<exceção >](../../../visual-basic/language-reference/xmldoc/exception.md) </span><span class="sxs-lookup"><span data-stu-id="59476-110">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) </span></span>  
<span data-ttu-id="59476-111"> [Como: criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="59476-111"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span></span>  
<span data-ttu-id="59476-112"> [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)</span><span class="sxs-lookup"><span data-stu-id="59476-112"> [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)</span></span>
