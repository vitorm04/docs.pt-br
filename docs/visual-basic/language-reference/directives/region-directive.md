---
title: "#Diretiva de região | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 86b8e9ce99a8c12e290f5efdc5a5c4da57f350d9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="region-directive"></a>#<span data-ttu-id="1ba23-102">Diretiva de região</span><span class="sxs-lookup"><span data-stu-id="1ba23-102">Region Directive</span></span>
<span data-ttu-id="1ba23-103">Recolhe e oculta seções de código em arquivos do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1ba23-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ba23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ba23-104">Syntax</span></span>  
  
```  
  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="1ba23-105">Partes</span><span class="sxs-lookup"><span data-stu-id="1ba23-105">Parts</span></span>  
  
|<span data-ttu-id="1ba23-106">Termo</span><span class="sxs-lookup"><span data-stu-id="1ba23-106">Term</span></span>|<span data-ttu-id="1ba23-107">Definição</span><span class="sxs-lookup"><span data-stu-id="1ba23-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="1ba23-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1ba23-108">Required.</span></span> <span data-ttu-id="1ba23-109">Cadeia de caracteres que atua como o título de uma região quando ele estiver recolhido.</span><span class="sxs-lookup"><span data-stu-id="1ba23-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="1ba23-110">Regiões estão recolhidas por padrão.</span><span class="sxs-lookup"><span data-stu-id="1ba23-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="1ba23-111">Encerra o `#Region` bloco.</span><span class="sxs-lookup"><span data-stu-id="1ba23-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ba23-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ba23-112">Remarks</span></span>  
 <span data-ttu-id="1ba23-113">Use o `#Region` diretiva para especificar um bloco de código para expandir ou recolher ao usar o recurso de estruturação do Editor de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ba23-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="1ba23-114">Você pode colocar, ou *aninhar*, regiões em outras regiões para agrupar regiões semelhantes.</span><span class="sxs-lookup"><span data-stu-id="1ba23-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ba23-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ba23-115">Example</span></span>  
 <span data-ttu-id="1ba23-116">Este exemplo usa a `#Region` diretiva.</span><span class="sxs-lookup"><span data-stu-id="1ba23-116">This example uses the `#Region` directive.</span></span>  
  
 <span data-ttu-id="1ba23-117">[!code-vb[VbVbalrConditionalComp n º&4;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ba23-117">[!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba23-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ba23-118">See Also</span></span>  
 <span data-ttu-id="1ba23-119">[#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="1ba23-119">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="1ba23-120"> [Estrutura de tópicos](https://docs.microsoft.com/visualstudio/ide/outlining) </span><span class="sxs-lookup"><span data-stu-id="1ba23-120"> [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining) </span></span>  
<span data-ttu-id="1ba23-121"> [Como recolher e ocultar seções do código](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)</span><span class="sxs-lookup"><span data-stu-id="1ba23-121"> [How to: Collapse and Hide Sections of Code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)</span></span>
