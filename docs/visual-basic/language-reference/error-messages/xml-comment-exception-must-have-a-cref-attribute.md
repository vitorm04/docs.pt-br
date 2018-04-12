---
title: Exceção de comentário XML deve ter um &#39; cref &#39; atributo
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="66ee0-102">Exceção de comentário XML deve ter um &#39; cref &#39; atributo</span><span class="sxs-lookup"><span data-stu-id="66ee0-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="66ee0-103">O \<exceção > marca fornece uma maneira para documentar as exceções que podem ser acionadas por um método.</span><span class="sxs-lookup"><span data-stu-id="66ee0-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="66ee0-104">Obrigatório `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação.</span><span class="sxs-lookup"><span data-stu-id="66ee0-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="66ee0-105">Se o membro existe, ele é convertido para o nome canônico de elemento no arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="66ee0-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="66ee0-106">**ID do erro:** BC42319</span><span class="sxs-lookup"><span data-stu-id="66ee0-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="66ee0-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="66ee0-107">To correct this error</span></span>  
  
-   <span data-ttu-id="66ee0-108">Adicionar o `cref` atributo à exceção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="66ee0-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="66ee0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66ee0-109">See Also</span></span>  
 [<span data-ttu-id="66ee0-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="66ee0-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="66ee0-111">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="66ee0-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="66ee0-112">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="66ee0-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
