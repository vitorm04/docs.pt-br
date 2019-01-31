---
title: A exceção de comentário XML deve ter um atributo 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: a11bfe261ffb8ded95f2e513aaddf00aa00f702e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266631"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="cfa98-102">A exceção de comentário XML deve ter um atributo 'cref'</span><span class="sxs-lookup"><span data-stu-id="cfa98-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="cfa98-103">O \<exceção > marca fornece uma maneira de documentar as exceções que podem ser lançadas por um método.</span><span class="sxs-lookup"><span data-stu-id="cfa98-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="cfa98-104">Necessário `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação.</span><span class="sxs-lookup"><span data-stu-id="cfa98-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="cfa98-105">Se o membro existe, ele é convertido para o nome de elemento canônico no arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="cfa98-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="cfa98-106">**ID do erro:** BC42319</span><span class="sxs-lookup"><span data-stu-id="cfa98-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cfa98-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cfa98-107">To correct this error</span></span>  
  
-   <span data-ttu-id="cfa98-108">Adicionar o `cref` atributo à exceção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cfa98-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cfa98-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfa98-109">See also</span></span>
- [<span data-ttu-id="cfa98-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="cfa98-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="cfa98-111">Como: Criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="cfa98-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="cfa98-112">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="cfa98-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
