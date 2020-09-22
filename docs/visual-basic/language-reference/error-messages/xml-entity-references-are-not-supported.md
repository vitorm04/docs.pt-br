---
title: As referências de entidade XML não são suportadas
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 470e5577654ce8b6bbc2732a41c130a85ddc96e5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874987"
---
# <a name="xml-entity-references-are-not-supported"></a><span data-ttu-id="9b623-102">As referências de entidade XML não são suportadas</span><span class="sxs-lookup"><span data-stu-id="9b623-102">XML entity references are not supported</span></span>

<span data-ttu-id="9b623-103">Uma referência de entidade (por exemplo, `©` ) que não está definida na especificação XML 1,0 é incluída como um valor para um literal XML.</span><span class="sxs-lookup"><span data-stu-id="9b623-103">An entity reference (for example, `©`) that is not defined in the XML 1.0 specification is included as a value for an XML literal.</span></span> <span data-ttu-id="9b623-104">Somente `&` as `"` `<` referências de entidade XML,,, `>` e `'` são suportadas em literais XML.</span><span class="sxs-lookup"><span data-stu-id="9b623-104">Only `&`, `"`, `<`, `>`, and `'` XML entity references are supported in XML literals.</span></span>  
  
 <span data-ttu-id="9b623-105">**ID do erro:** BC31180</span><span class="sxs-lookup"><span data-stu-id="9b623-105">**Error ID:** BC31180</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9b623-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9b623-106">To correct this error</span></span>  
  
- <span data-ttu-id="9b623-107">Remova a referência de entidade sem suporte.</span><span class="sxs-lookup"><span data-stu-id="9b623-107">Remove the unsupported entity reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b623-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="9b623-108">See also</span></span>

- [<span data-ttu-id="9b623-109">Especificação dos literais XML e do XML 1.0</span><span class="sxs-lookup"><span data-stu-id="9b623-109">XML Literals and the XML 1.0 Specification</span></span>](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [<span data-ttu-id="9b623-110">Literais XML</span><span class="sxs-lookup"><span data-stu-id="9b623-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="9b623-111">XML</span><span class="sxs-lookup"><span data-stu-id="9b623-111">XML</span></span>](../../programming-guide/language-features/xml/index.md)
