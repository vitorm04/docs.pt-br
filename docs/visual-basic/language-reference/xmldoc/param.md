---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4405fdf2defbb27aa2146d20083fd406d1f07236
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352293"
---
# <a name="param-visual-basic"></a><span data-ttu-id="99372-101">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99372-101">\<param> (Visual Basic)</span></span>
<span data-ttu-id="99372-102">Defines a parameter name and description.</span><span class="sxs-lookup"><span data-stu-id="99372-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99372-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99372-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="99372-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="99372-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="99372-105">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="99372-105">The name of a method parameter.</span></span> <span data-ttu-id="99372-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="99372-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="99372-107">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="99372-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99372-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="99372-108">Remarks</span></span>  
 <span data-ttu-id="99372-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span><span class="sxs-lookup"><span data-stu-id="99372-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="99372-110">The text for the `<param>` tag will appear in the following locations:</span><span class="sxs-lookup"><span data-stu-id="99372-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="99372-111">Parameter Info of IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="99372-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="99372-112">Para obter mais informações, veja [Usando o IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="99372-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="99372-113">Object Browser.</span><span class="sxs-lookup"><span data-stu-id="99372-113">Object Browser.</span></span> <span data-ttu-id="99372-114">Para obter mais informações, consulte [Exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="99372-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="99372-115">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="99372-115">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99372-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99372-116">Example</span></span>  
 <span data-ttu-id="99372-117">This example uses the `<param>` tag to describe the `id` parameter.</span><span class="sxs-lookup"><span data-stu-id="99372-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="99372-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99372-118">See also</span></span>

- [<span data-ttu-id="99372-119">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="99372-119">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
