---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: d325d5f9fbfd132630cf280653be214a267a7a80
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400054"
---
# <a name="param-visual-basic"></a><span data-ttu-id="332d1-101">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="332d1-101">\<param> (Visual Basic)</span></span>
<span data-ttu-id="332d1-102">Define um nome de parâmetro e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="332d1-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="332d1-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="332d1-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="332d1-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="332d1-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="332d1-105">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="332d1-105">The name of a method parameter.</span></span> <span data-ttu-id="332d1-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="332d1-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="332d1-107">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="332d1-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="332d1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="332d1-108">Remarks</span></span>  
 <span data-ttu-id="332d1-109">A `<param>` marca deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros para o método.</span><span class="sxs-lookup"><span data-stu-id="332d1-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="332d1-110">O texto da `<param>` marca aparecerá nos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="332d1-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="332d1-111">Informações de parâmetro do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="332d1-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="332d1-112">Para obter mais informações, veja [Usando o IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="332d1-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="332d1-113">Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="332d1-113">Object Browser.</span></span> <span data-ttu-id="332d1-114">Para obter mais informações, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="332d1-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="332d1-115">Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="332d1-115">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="332d1-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="332d1-116">Example</span></span>  
 <span data-ttu-id="332d1-117">Este exemplo usa a `<param>` marca para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="332d1-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="332d1-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="332d1-118">See also</span></span>

- [<span data-ttu-id="332d1-119">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="332d1-119">XML Comment Tags</span></span>](index.md)
