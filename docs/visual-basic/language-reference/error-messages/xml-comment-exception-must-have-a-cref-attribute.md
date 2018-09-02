---
title: Exceção de comentário XML deve ter um &#39;cref&#39; atributo
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: abe9fe0f6216f81fa223fe83a122b580577e1c32
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404759"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="eef68-102">Exceção de comentário XML deve ter um &#39;cref&#39; atributo</span><span class="sxs-lookup"><span data-stu-id="eef68-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="eef68-103">O \<exceção > marca fornece uma maneira de documentar as exceções que podem ser lançadas por um método.</span><span class="sxs-lookup"><span data-stu-id="eef68-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="eef68-104">Necessário `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação.</span><span class="sxs-lookup"><span data-stu-id="eef68-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="eef68-105">Se o membro existe, ele é convertido para o nome de elemento canônico no arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="eef68-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="eef68-106">**ID do erro:** BC42319</span><span class="sxs-lookup"><span data-stu-id="eef68-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eef68-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="eef68-107">To correct this error</span></span>  
  
-   <span data-ttu-id="eef68-108">Adicionar o `cref` atributo à exceção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="eef68-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="eef68-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eef68-109">See Also</span></span>  
 [<span data-ttu-id="eef68-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="eef68-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="eef68-111">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="eef68-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="eef68-112">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="eef68-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
