---
title: "&lt;parâmetro&gt; (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: ddf5baf83816d757edf67cdf1c66dc24e4313b83
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="e3d7d-102">&lt;parâmetro&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3d7d-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="e3d7d-103">Define um nome de parâmetro e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3d7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3d7d-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3d7d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3d7d-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e3d7d-106">O nome de um parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-106">The name of a method parameter.</span></span> <span data-ttu-id="e3d7d-107">Coloque o nome entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="e3d7d-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="e3d7d-108">Uma descrição para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3d7d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3d7d-109">Remarks</span></span>  
 <span data-ttu-id="e3d7d-110">O `<param>` marca deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="e3d7d-111">O texto para o `<param>` marca aparecerão nos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="e3d7d-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="e3d7d-112">Informações de parâmetro do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="e3d7d-113">Para obter mais informações, veja [Usando o IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="e3d7d-113">For more information, see [Using IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="e3d7d-114">Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-114">Object Browser.</span></span> <span data-ttu-id="e3d7d-115">Para obter mais informações, consulte [Exibindo a estrutura do código](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="e3d7d-115">For more information, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="e3d7d-116">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3d7d-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3d7d-117">Example</span></span>  
 <span data-ttu-id="e3d7d-118">Este exemplo usa o `<param>` marca para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 <span data-ttu-id="e3d7d-119">[!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e3d7d-119">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d7d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3d7d-120">See Also</span></span>  
 [<span data-ttu-id="e3d7d-121">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="e3d7d-121">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
