---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 2f2bebfd06d4614f05cb66834cc5bef40524ce3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348455"
---
# <a name="include-visual-basic"></a><span data-ttu-id="61698-101">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61698-101">\<include> (Visual Basic)</span></span>
<span data-ttu-id="61698-102">Refers to another file that describes the types and members in your source code.</span><span class="sxs-lookup"><span data-stu-id="61698-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61698-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61698-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="61698-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61698-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="61698-105">Necessário.</span><span class="sxs-lookup"><span data-stu-id="61698-105">Required.</span></span> <span data-ttu-id="61698-106">O nome do arquivo que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="61698-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="61698-107">O nome do arquivo pode ser qualificado com um caminho.</span><span class="sxs-lookup"><span data-stu-id="61698-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="61698-108">Enclose `filename` in double quotation marks (" ").</span><span class="sxs-lookup"><span data-stu-id="61698-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="61698-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="61698-109">Required.</span></span> <span data-ttu-id="61698-110">O caminho das marcas em `filename` que leva à marca `name`.</span><span class="sxs-lookup"><span data-stu-id="61698-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="61698-111">Enclose the path in double quotation marks (" ").</span><span class="sxs-lookup"><span data-stu-id="61698-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="61698-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="61698-112">Required.</span></span> <span data-ttu-id="61698-113">The name specifier in the tag that precedes the comments.</span><span class="sxs-lookup"><span data-stu-id="61698-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="61698-114">`Name` will have an `id`.</span><span class="sxs-lookup"><span data-stu-id="61698-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="61698-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="61698-115">Required.</span></span> <span data-ttu-id="61698-116">A ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="61698-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="61698-117">Enclose the ID in single quotation marks (' ').</span><span class="sxs-lookup"><span data-stu-id="61698-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61698-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="61698-118">Remarks</span></span>  
 <span data-ttu-id="61698-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span><span class="sxs-lookup"><span data-stu-id="61698-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="61698-120">Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="61698-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="61698-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span><span class="sxs-lookup"><span data-stu-id="61698-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="61698-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span><span class="sxs-lookup"><span data-stu-id="61698-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61698-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61698-123">Example</span></span>  
 <span data-ttu-id="61698-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="61698-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="61698-125">The format of the `commentFile.xml` is as follows.</span><span class="sxs-lookup"><span data-stu-id="61698-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61698-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61698-126">See also</span></span>

- [<span data-ttu-id="61698-127">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="61698-127">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
