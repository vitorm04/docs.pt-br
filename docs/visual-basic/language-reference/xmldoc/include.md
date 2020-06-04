---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 78a10624107cea349b01f484c641190a945dbd7e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400105"
---
# <a name="include-visual-basic"></a><span data-ttu-id="adcd0-101">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adcd0-101">\<include> (Visual Basic)</span></span>
<span data-ttu-id="adcd0-102">Refere-se a outro arquivo que descreve os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="adcd0-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adcd0-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adcd0-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="adcd0-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="adcd0-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="adcd0-105">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="adcd0-105">Required.</span></span> <span data-ttu-id="adcd0-106">O nome do arquivo que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="adcd0-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="adcd0-107">O nome do arquivo pode ser qualificado com um caminho.</span><span class="sxs-lookup"><span data-stu-id="adcd0-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="adcd0-108">Coloque entre `filename` aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="adcd0-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="adcd0-109">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="adcd0-109">Required.</span></span> <span data-ttu-id="adcd0-110">O caminho das marcas em `filename` que leva à marca `name`.</span><span class="sxs-lookup"><span data-stu-id="adcd0-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="adcd0-111">Coloque o caminho entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="adcd0-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="adcd0-112">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="adcd0-112">Required.</span></span> <span data-ttu-id="adcd0-113">O especificador de nome na marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="adcd0-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="adcd0-114">`Name`terá um `id` .</span><span class="sxs-lookup"><span data-stu-id="adcd0-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="adcd0-115">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="adcd0-115">Required.</span></span> <span data-ttu-id="adcd0-116">A ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="adcd0-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="adcd0-117">Coloque a ID entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="adcd0-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adcd0-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="adcd0-118">Remarks</span></span>  
 <span data-ttu-id="adcd0-119">Use a `<include>` marca para fazer referência a comentários em outro arquivo que descreva os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="adcd0-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="adcd0-120">Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="adcd0-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="adcd0-121">A `<include>` marca usa a recomendação da versão 1,0 do W3C XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="adcd0-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="adcd0-122">Para obter mais informações sobre maneiras de personalizar seu `<include>` uso, consulte <https://www.w3.org/TR/xpath> .</span><span class="sxs-lookup"><span data-stu-id="adcd0-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adcd0-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="adcd0-123">Example</span></span>  
 <span data-ttu-id="adcd0-124">Este exemplo usa a `<include>` marca para importar comentários de documentação de membro de um arquivo chamado `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="adcd0-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="adcd0-125">O formato do `commentFile.xml` é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="adcd0-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adcd0-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="adcd0-126">See also</span></span>

- [<span data-ttu-id="adcd0-127">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="adcd0-127">XML Comment Tags</span></span>](index.md)
