---
title: A exceção de comentário XML deve ter um atributo 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406502"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="5906d-102">A exceção de comentário XML deve ter um atributo 'cref'</span><span class="sxs-lookup"><span data-stu-id="5906d-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="5906d-103">A \<exception> marca fornece uma maneira de documentar as exceções que podem ser geradas por um método.</span><span class="sxs-lookup"><span data-stu-id="5906d-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="5906d-104">O `cref` Atributo Required designa o nome de um membro, que é verificado pelo gerador de documentação.</span><span class="sxs-lookup"><span data-stu-id="5906d-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="5906d-105">Se o membro existir, ele será convertido para o nome do elemento canônico no arquivo de documentação.</span><span class="sxs-lookup"><span data-stu-id="5906d-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="5906d-106">**ID do erro:** BC42319</span><span class="sxs-lookup"><span data-stu-id="5906d-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5906d-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5906d-107">To correct this error</span></span>

<span data-ttu-id="5906d-108">Adicione o `cref` atributo à exceção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5906d-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="5906d-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="5906d-109">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="5906d-110">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="5906d-110">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="5906d-111">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="5906d-111">XML Comment Tags</span></span>](../xmldoc/index.md)
