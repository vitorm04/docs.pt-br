---
title: Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 79be695478983055ae1f016cf841d733d3f4c430
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766581"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="3dd8b-102">Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3dd8b-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>
<span data-ttu-id="3dd8b-103">Não há suporte para literais XML e propriedades XML no código inserido dentro do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3dd8b-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="3dd8b-104">Para usar recursos XML, mova o código para code-behind.</span><span class="sxs-lookup"><span data-stu-id="3dd8b-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="3dd8b-105">Um literal XML ou uma propriedade de eixo XML é definida no código inserido (`<%= =>`) em um arquivo do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3dd8b-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="3dd8b-106">**ID do erro:** BC31200</span><span class="sxs-lookup"><span data-stu-id="3dd8b-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3dd8b-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3dd8b-107">To correct this error</span></span>  
  
- <span data-ttu-id="3dd8b-108">Mova o código que inclui a literal XML ou uma propriedade de eixo XML para um arquivo de code-behind do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3dd8b-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd8b-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3dd8b-109">See also</span></span>

- [<span data-ttu-id="3dd8b-110">Literais XML</span><span class="sxs-lookup"><span data-stu-id="3dd8b-110">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="3dd8b-111">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="3dd8b-111">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="3dd8b-112">XML</span><span class="sxs-lookup"><span data-stu-id="3dd8b-112">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
