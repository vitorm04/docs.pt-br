---
title: '&lt;incluir&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: da7a6c15c558fc56dbc6a874d4a28c4434f67668
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43876581"
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="21630-102">&lt;incluir&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21630-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="21630-103">Refere-se a outro arquivo que descreve os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="21630-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21630-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21630-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21630-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21630-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="21630-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="21630-106">Required.</span></span> <span data-ttu-id="21630-107">O nome do arquivo que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="21630-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="21630-108">O nome do arquivo pode ser qualificado com um caminho.</span><span class="sxs-lookup"><span data-stu-id="21630-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="21630-109">Coloque `filename` entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="21630-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="21630-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="21630-110">Required.</span></span> <span data-ttu-id="21630-111">O caminho das marcas em `filename` que leva à marca `name`.</span><span class="sxs-lookup"><span data-stu-id="21630-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="21630-112">Coloque o caminho entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="21630-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="21630-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="21630-113">Required.</span></span> <span data-ttu-id="21630-114">O especificador de nome na marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="21630-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="21630-115">`Name` terá um `id`.</span><span class="sxs-lookup"><span data-stu-id="21630-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="21630-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="21630-116">Required.</span></span> <span data-ttu-id="21630-117">A ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="21630-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="21630-118">Coloque a ID entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="21630-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21630-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="21630-119">Remarks</span></span>  
 <span data-ttu-id="21630-120">Use o `<include>` marca para fazer referência a comentários em outro arquivo que descrevem os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="21630-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="21630-121">Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="21630-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="21630-122">O `<include>` marca usa a recomendação do W3C XML Path Language (XPath) versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="21630-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="21630-123">Para obter mais informações de maneiras de personalizar seu `<include>` uso está disponível em http://www.w3.org/TR/xpath.</span><span class="sxs-lookup"><span data-stu-id="21630-123">More information for ways to customize your `<include>` use is available at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21630-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21630-124">Example</span></span>  
 <span data-ttu-id="21630-125">Este exemplo usa o `<include>` marca para importar os comentários de documentação do membro de um arquivo chamado `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="21630-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="21630-126">O formato do `commentFile.xml` é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="21630-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21630-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21630-127">See Also</span></span>  
 [<span data-ttu-id="21630-128">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="21630-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
