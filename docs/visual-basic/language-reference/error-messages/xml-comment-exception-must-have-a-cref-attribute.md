---
title: A exceção de comentário XML deve ter um atributo 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592035"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="ad97e-102">A exceção de comentário XML deve ter um atributo 'cref'</span><span class="sxs-lookup"><span data-stu-id="ad97e-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="ad97e-103">A marca > \<exception fornece uma maneira de documentar as exceções que podem ser geradas por um método.</span><span class="sxs-lookup"><span data-stu-id="ad97e-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="ad97e-104">O atributo `cref` necessário designa o nome de um membro, que é verificado pelo gerador de documentação.</span><span class="sxs-lookup"><span data-stu-id="ad97e-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="ad97e-105">Se o membro existir, ele será convertido para o nome do elemento canônico no arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="ad97e-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="ad97e-106">**ID do erro:** BC42319</span><span class="sxs-lookup"><span data-stu-id="ad97e-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ad97e-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ad97e-107">To correct this error</span></span>  
  
- <span data-ttu-id="ad97e-108">Adicione o atributo `cref` à exceção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ad97e-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    <span data-ttu-id="ad97e-109">xml</span><span class="sxs-lookup"><span data-stu-id="ad97e-109">xml</span></span>  
    <span data-ttu-id="ad97e-110"><exception cref="member">Descrição</exception> de ' ' '</span><span class="sxs-lookup"><span data-stu-id="ad97e-110">'''<exception cref="member">description</exception></span></span>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
