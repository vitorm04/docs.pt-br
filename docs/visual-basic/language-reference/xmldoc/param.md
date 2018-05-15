---
title: '&lt;param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c992c96303eb1441eaf667693b7aefb5361b196c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="bdd96-102">&lt;param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdd96-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="bdd96-103">Define um nome de parâmetro e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="bdd96-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdd96-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdd96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bdd96-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="bdd96-106">O nome do parâmetro de um método.</span><span class="sxs-lookup"><span data-stu-id="bdd96-106">The name of a method parameter.</span></span> <span data-ttu-id="bdd96-107">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="bdd96-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="bdd96-108">Uma descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bdd96-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdd96-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bdd96-109">Remarks</span></span>  
 <span data-ttu-id="bdd96-110">O `<param>` marca deve ser usada no comentário de uma declaração de método para descrever um dos parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="bdd96-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="bdd96-111">O texto para o `<param>` marca será exibida nos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="bdd96-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="bdd96-112">Informações de parâmetro do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="bdd96-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="bdd96-113">Para obter mais informações, veja [Usando o IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="bdd96-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="bdd96-114">Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="bdd96-114">Object Browser.</span></span> <span data-ttu-id="bdd96-115">Para obter mais informações, consulte [Exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="bdd96-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="bdd96-116">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="bdd96-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdd96-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bdd96-117">Example</span></span>  
 <span data-ttu-id="bdd96-118">Este exemplo usa o `<param>` marcas para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bdd96-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bdd96-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdd96-119">See Also</span></span>  
 [<span data-ttu-id="bdd96-120">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="bdd96-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
