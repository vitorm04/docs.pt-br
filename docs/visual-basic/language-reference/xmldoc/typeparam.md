---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b654fe6fc93642693730256b523fee999aa55937
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="6e3d9-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e3d9-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="6e3d9-103">Define um nome de parâmetro de tipo e descrição.</span><span class="sxs-lookup"><span data-stu-id="6e3d9-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e3d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e3d9-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e3d9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e3d9-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6e3d9-106">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="6e3d9-106">The name of the type parameter.</span></span> <span data-ttu-id="6e3d9-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="6e3d9-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6e3d9-108">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="6e3d9-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e3d9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e3d9-109">Remarks</span></span>  
 <span data-ttu-id="6e3d9-110">Use o `<typeparam>` marca de comentário para um tipo genérico ou declaração de membro genérico descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="6e3d9-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="6e3d9-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6e3d9-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e3d9-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e3d9-112">Example</span></span>  
 <span data-ttu-id="6e3d9-113">Este exemplo usa o `<typeparam>` marcas para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6e3d9-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6e3d9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e3d9-114">See Also</span></span>  
 [<span data-ttu-id="6e3d9-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="6e3d9-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
