---
title: As propriedades de eixo XML não dão suporte à associação tardia
ms.date: 07/20/2015
f1_keywords:
- bc31168
- vbc31168
helpviewer_keywords:
- BC31168
ms.assetid: 45707363-55e4-4151-892d-d8729106355b
ms.openlocfilehash: 9eef245d6f83770ce26bc9e753711543241d57fb
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163279"
---
# <a name="bc31168-xml-axis-properties-do-not-support-late-binding"></a><span data-ttu-id="c00aa-102">BC31168: as propriedades do eixo XML não dão suporte à associação tardia</span><span class="sxs-lookup"><span data-stu-id="c00aa-102">BC31168: XML axis properties do not support late binding</span></span>

<span data-ttu-id="c00aa-103">Uma propriedade de eixo XML foi referenciada por um objeto não tipado.</span><span class="sxs-lookup"><span data-stu-id="c00aa-103">An XML axis property has been referenced for an untyped object.</span></span>

 <span data-ttu-id="c00aa-104">**ID do erro:** BC31168</span><span class="sxs-lookup"><span data-stu-id="c00aa-104">**Error ID:** BC31168</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c00aa-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c00aa-105">To correct this error</span></span>

- <span data-ttu-id="c00aa-106">Verifique se o objeto é um objeto de tipo forte <xref:System.Xml.Linq.XElement> antes de fazer referência à propriedade do eixo XML.</span><span class="sxs-lookup"><span data-stu-id="c00aa-106">Ensure that the object is a strong-typed <xref:System.Xml.Linq.XElement> object before referencing the XML axis property.</span></span>

## <a name="see-also"></a><span data-ttu-id="c00aa-107">Veja também</span><span class="sxs-lookup"><span data-stu-id="c00aa-107">See also</span></span>

- [<span data-ttu-id="c00aa-108">Propriedades do eixo XML</span><span class="sxs-lookup"><span data-stu-id="c00aa-108">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="c00aa-109">XML</span><span class="sxs-lookup"><span data-stu-id="c00aa-109">XML</span></span>](../../programming-guide/language-features/xml/index.md)
