---
title: <include> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: d9c1c1a50f0e3530c842a6058e288b8d2be15f95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940901"
---
# <a name="include-visual-basic"></a><span data-ttu-id="b4192-102">\<incluir > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4192-102">\<include> (Visual Basic)</span></span>
<span data-ttu-id="b4192-103">Refere-se a outro arquivo que descreve os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b4192-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4192-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4192-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4192-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4192-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="b4192-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b4192-106">Required.</span></span> <span data-ttu-id="b4192-107">O nome do arquivo que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="b4192-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="b4192-108">O nome do arquivo pode ser qualificado com um caminho.</span><span class="sxs-lookup"><span data-stu-id="b4192-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="b4192-109">Coloque `filename` entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="b4192-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="b4192-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b4192-110">Required.</span></span> <span data-ttu-id="b4192-111">O caminho das marcas em `filename` que leva à marca `name`.</span><span class="sxs-lookup"><span data-stu-id="b4192-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="b4192-112">Coloque o caminho entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="b4192-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="b4192-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b4192-113">Required.</span></span> <span data-ttu-id="b4192-114">O especificador de nome na marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="b4192-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="b4192-115">`Name` terá um `id`.</span><span class="sxs-lookup"><span data-stu-id="b4192-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="b4192-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b4192-116">Required.</span></span> <span data-ttu-id="b4192-117">A ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="b4192-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="b4192-118">Coloque a ID entre aspas simples (' ').</span><span class="sxs-lookup"><span data-stu-id="b4192-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4192-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4192-119">Remarks</span></span>  
 <span data-ttu-id="b4192-120">Use o `<include>` marca para fazer referência a comentários em outro arquivo que descrevem os tipos e membros em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b4192-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="b4192-121">Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b4192-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="b4192-122">O `<include>` marca usa a recomendação do W3C XML Path Language (XPath) versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="b4192-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="b4192-123">Para obter mais informações sobre como personalizar suas `<include>` usar, consulte <https://www.w3.org/TR/xpath>.</span><span class="sxs-lookup"><span data-stu-id="b4192-123">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4192-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4192-124">Example</span></span>  
 <span data-ttu-id="b4192-125">Este exemplo usa o `<include>` marca para importar os comentários de documentação do membro de um arquivo chamado `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="b4192-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="b4192-126">O formato do `commentFile.xml` é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="b4192-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b4192-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4192-127">See also</span></span>

- [<span data-ttu-id="b4192-128">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="b4192-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
