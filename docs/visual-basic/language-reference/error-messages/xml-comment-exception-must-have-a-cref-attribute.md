---
title: A exceção de comentário XML deve ter um atributo 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: a974df5d2305b88946981d0d258a8088b23d3fc3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813282"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="01b76-102">A exceção de comentário XML deve ter um atributo 'cref'</span><span class="sxs-lookup"><span data-stu-id="01b76-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="01b76-103">O \<exceção > marca fornece uma maneira de documentar as exceções que podem ser lançadas por um método.</span><span class="sxs-lookup"><span data-stu-id="01b76-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="01b76-104">Necessário `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação.</span><span class="sxs-lookup"><span data-stu-id="01b76-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="01b76-105">Se o membro existe, ele é convertido para o nome de elemento canônico no arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="01b76-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="01b76-106">**ID do erro:** BC42319</span><span class="sxs-lookup"><span data-stu-id="01b76-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="01b76-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="01b76-107">To correct this error</span></span>  
  
-   <span data-ttu-id="01b76-108">Adicionar o `cref` atributo à exceção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="01b76-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="01b76-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01b76-109">See also</span></span>

- [<span data-ttu-id="01b76-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="01b76-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="01b76-111">Como: Criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="01b76-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="01b76-112">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="01b76-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
