---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 91489ee1664da22cc8897cdf8d12b61d962d1c83
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664166"
---
# <a name="param-visual-basic"></a><span data-ttu-id="974a8-102">\<param > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="974a8-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="974a8-103">Define um nome de parâmetro e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="974a8-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="974a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="974a8-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="974a8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="974a8-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="974a8-106">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="974a8-106">The name of a method parameter.</span></span> <span data-ttu-id="974a8-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="974a8-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="974a8-108">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="974a8-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="974a8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="974a8-109">Remarks</span></span>  
 <span data-ttu-id="974a8-110">O `<param>` marca deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="974a8-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="974a8-111">O texto para o `<param>` marca será exibida nos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="974a8-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="974a8-112">Informações do parâmetro do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="974a8-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="974a8-113">Para obter mais informações, veja [Usando o IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="974a8-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="974a8-114">Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="974a8-114">Object Browser.</span></span> <span data-ttu-id="974a8-115">Para obter mais informações, consulte [Exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="974a8-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="974a8-116">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="974a8-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="974a8-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="974a8-117">Example</span></span>  
 <span data-ttu-id="974a8-118">Este exemplo usa o `<param>` marca para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="974a8-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="974a8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="974a8-119">See also</span></span>

- [<span data-ttu-id="974a8-120">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="974a8-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
