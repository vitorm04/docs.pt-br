---
title: '#Diretiva de região (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: eaaf0f8279ec905767be3f364a88357f0d393bba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818860"
---
# <a name="region-directive"></a><span data-ttu-id="c1f31-102">Diretiva #Region</span><span class="sxs-lookup"><span data-stu-id="c1f31-102">#Region Directive</span></span>
<span data-ttu-id="c1f31-103">Recolhe e oculta seções de código em arquivos do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1f31-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f31-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1f31-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="c1f31-105">Partes</span><span class="sxs-lookup"><span data-stu-id="c1f31-105">Parts</span></span>  
  
|<span data-ttu-id="c1f31-106">Termo</span><span class="sxs-lookup"><span data-stu-id="c1f31-106">Term</span></span>|<span data-ttu-id="c1f31-107">Definição</span><span class="sxs-lookup"><span data-stu-id="c1f31-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="c1f31-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c1f31-108">Required.</span></span> <span data-ttu-id="c1f31-109">Cadeia de caracteres que atua como o título de uma região quando ele estiver recolhido.</span><span class="sxs-lookup"><span data-stu-id="c1f31-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="c1f31-110">Regiões recolhidas por padrão.</span><span class="sxs-lookup"><span data-stu-id="c1f31-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="c1f31-111">Encerra o `#Region` bloco.</span><span class="sxs-lookup"><span data-stu-id="c1f31-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f31-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1f31-112">Remarks</span></span>  
 <span data-ttu-id="c1f31-113">Use o `#Region` diretiva para especificar um bloco de código para expandir ou recolher ao usar o recurso de estrutura de tópicos do Editor de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1f31-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="c1f31-114">Você pode colocar, ou *aninhar*, regiões em outras regiões para agrupar regiões semelhantes.</span><span class="sxs-lookup"><span data-stu-id="c1f31-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1f31-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1f31-115">Example</span></span>  
 <span data-ttu-id="c1f31-116">Este exemplo usa o `#Region` diretiva.</span><span class="sxs-lookup"><span data-stu-id="c1f31-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c1f31-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1f31-117">See also</span></span>

- [<span data-ttu-id="c1f31-118">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="c1f31-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="c1f31-119">Estrutura de tópicos</span><span class="sxs-lookup"><span data-stu-id="c1f31-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="c1f31-120">Como: recolher e ocultar seções do código</span><span class="sxs-lookup"><span data-stu-id="c1f31-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
