---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c62eab6b1fb1ba1cc7de83c12d7205cf0bbe46fa
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524726"
---
# <a name="param-visual-basic"></a><span data-ttu-id="e4544-102">> de \<param (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4544-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="e4544-103">Define um nome de parâmetro e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="e4544-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4544-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4544-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4544-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4544-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e4544-106">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="e4544-106">The name of a method parameter.</span></span> <span data-ttu-id="e4544-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="e4544-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="e4544-108">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e4544-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4544-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4544-109">Remarks</span></span>  
 <span data-ttu-id="e4544-110">A marca de `<param>` deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros para o método.</span><span class="sxs-lookup"><span data-stu-id="e4544-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="e4544-111">O texto da marca de `<param>` aparecerá nos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="e4544-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="e4544-112">Informações de parâmetro do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e4544-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="e4544-113">Para obter mais informações, veja [Usando o IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="e4544-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="e4544-114">Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="e4544-114">Object Browser.</span></span> <span data-ttu-id="e4544-115">Para obter mais informações, consulte [Exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="e4544-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="e4544-116">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e4544-116">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4544-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4544-117">Example</span></span>  
 <span data-ttu-id="e4544-118">Este exemplo usa a marca `<param>` para descrever o parâmetro `id`.</span><span class="sxs-lookup"><span data-stu-id="e4544-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e4544-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4544-119">See also</span></span>

- [<span data-ttu-id="e4544-120">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="e4544-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
