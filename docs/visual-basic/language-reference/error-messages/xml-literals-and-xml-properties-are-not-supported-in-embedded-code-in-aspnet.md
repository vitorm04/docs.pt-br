---
title: Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 861677636f9a73015b26efec30df728d07fbdf72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870211"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="2fa57-102">Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2fa57-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>

<span data-ttu-id="2fa57-103">Não há suporte para literais XML e propriedades XML no código inserido dentro de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2fa57-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="2fa57-104">Para usar recursos XML, mova o código para code-behind.</span><span class="sxs-lookup"><span data-stu-id="2fa57-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="2fa57-105">Uma propriedade XML literal ou XML Axis é definida no código inserido ( `<%= =>` ) em um arquivo ASP.net.</span><span class="sxs-lookup"><span data-stu-id="2fa57-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="2fa57-106">**ID do erro:** BC31200</span><span class="sxs-lookup"><span data-stu-id="2fa57-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2fa57-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2fa57-107">To correct this error</span></span>  
  
- <span data-ttu-id="2fa57-108">Mova o código que inclui o literal XML ou a propriedade de eixo XML para um arquivo code-behind ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2fa57-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa57-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="2fa57-109">See also</span></span>

- [<span data-ttu-id="2fa57-110">Literais XML</span><span class="sxs-lookup"><span data-stu-id="2fa57-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="2fa57-111">Propriedades do eixo XML</span><span class="sxs-lookup"><span data-stu-id="2fa57-111">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="2fa57-112">XML</span><span class="sxs-lookup"><span data-stu-id="2fa57-112">XML</span></span>](../../programming-guide/language-features/xml/index.md)
