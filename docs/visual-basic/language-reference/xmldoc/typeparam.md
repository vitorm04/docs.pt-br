---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 2ad54845645172acb5b91935f5347a828510e3aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411480"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="5213b-101">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5213b-101">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="5213b-102">Define um nome de parâmetro de tipo e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="5213b-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5213b-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5213b-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5213b-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5213b-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5213b-105">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="5213b-105">The name of the type parameter.</span></span> <span data-ttu-id="5213b-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="5213b-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="5213b-107">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="5213b-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5213b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5213b-108">Remarks</span></span>  
 <span data-ttu-id="5213b-109">Use a `<typeparam>` marca no comentário para um tipo genérico ou declaração de membro genérico para descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="5213b-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="5213b-110">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="5213b-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5213b-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5213b-111">Example</span></span>  
 <span data-ttu-id="5213b-112">Este exemplo usa a `<typeparam>` marca para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5213b-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="5213b-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="5213b-113">See also</span></span>

- [<span data-ttu-id="5213b-114">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="5213b-114">XML Comment Tags</span></span>](index.md)
