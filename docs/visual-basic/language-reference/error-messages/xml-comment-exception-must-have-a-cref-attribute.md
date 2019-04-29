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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766590"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="c0c02-102">A exceção de comentário XML deve ter um atributo 'cref'</span><span class="sxs-lookup"><span data-stu-id="c0c02-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="c0c02-103">O \<exceção > marca fornece uma maneira de documentar as exceções que podem ser lançadas por um método.</span><span class="sxs-lookup"><span data-stu-id="c0c02-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="c0c02-104">Necessário `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação.</span><span class="sxs-lookup"><span data-stu-id="c0c02-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="c0c02-105">Se o membro existe, ele é convertido para o nome de elemento canônico no arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="c0c02-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="c0c02-106">**ID do erro:** BC42319</span><span class="sxs-lookup"><span data-stu-id="c0c02-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c0c02-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c0c02-107">To correct this error</span></span>  
  
- <span data-ttu-id="c0c02-108">Adicionar o `cref` atributo à exceção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c0c02-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c0c02-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0c02-109">See also</span></span>

- [<span data-ttu-id="c0c02-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="c0c02-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="c0c02-111">Como: Criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="c0c02-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="c0c02-112">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="c0c02-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
