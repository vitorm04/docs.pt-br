---
title: '&lt;incluir&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22eebaa8da8ef082e132cfdf8cb68498bfe16d73
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="f0f79-102">&lt;incluir&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0f79-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="f0f79-103">Refere-se a outro arquivo que descreve os tipos e membros no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="f0f79-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f79-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0f79-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0f79-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0f79-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="f0f79-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f0f79-106">Required.</span></span> <span data-ttu-id="f0f79-107">O nome do arquivo que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="f0f79-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="f0f79-108">O nome do arquivo pode ser qualificado com um caminho.</span><span class="sxs-lookup"><span data-stu-id="f0f79-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="f0f79-109">Coloque `filename` entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="f0f79-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="f0f79-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f0f79-110">Required.</span></span> <span data-ttu-id="f0f79-111">O caminho das marcas em `filename` que leva à marca `name`.</span><span class="sxs-lookup"><span data-stu-id="f0f79-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="f0f79-112">Coloque o caminho entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="f0f79-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="f0f79-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f0f79-113">Required.</span></span> <span data-ttu-id="f0f79-114">O especificador de nome na marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="f0f79-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="f0f79-115">`Name`será necessário um `id`.</span><span class="sxs-lookup"><span data-stu-id="f0f79-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="f0f79-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f0f79-116">Required.</span></span> <span data-ttu-id="f0f79-117">A ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="f0f79-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="f0f79-118">Coloque a ID entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="f0f79-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0f79-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="f0f79-119">Remarks</span></span>  
 <span data-ttu-id="f0f79-120">Use o `<include>` marca Consulte comentários em outro arquivo que descrevem os tipos e membros no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="f0f79-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="f0f79-121">Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="f0f79-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="f0f79-122">O `<include>` marca usa a recomendação do W3C XML Path Language (XPath) versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="f0f79-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="f0f79-123">Para obter mais informações sobre como personalizar o `<include>` uso está disponível em http://www.w3.org/TR/xpath.</span><span class="sxs-lookup"><span data-stu-id="f0f79-123">More information for ways to customize your `<include>` use is available at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0f79-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0f79-124">Example</span></span>  
 <span data-ttu-id="f0f79-125">Este exemplo usa o `<include>` marca para importar os comentários de documentação do membro de um arquivo chamado `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="f0f79-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="f0f79-126">O formato da `commentFile.xml` é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="f0f79-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f0f79-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0f79-127">See Also</span></span>  
 [<span data-ttu-id="f0f79-128">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="f0f79-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
