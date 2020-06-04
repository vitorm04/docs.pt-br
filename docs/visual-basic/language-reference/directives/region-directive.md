---
title: '#Diretiva Region'
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
ms.openlocfilehash: cd53a6079c1564a8c73a0a1a6273fc166d18d3e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409928"
---
# <a name="region-directive"></a><span data-ttu-id="60019-102">Diretiva #Region</span><span class="sxs-lookup"><span data-stu-id="60019-102">#Region Directive</span></span>

<span data-ttu-id="60019-103">Recolhe e oculta seções de código em Visual Basic arquivos.</span><span class="sxs-lookup"><span data-stu-id="60019-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60019-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60019-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="60019-105">Partes</span><span class="sxs-lookup"><span data-stu-id="60019-105">Parts</span></span>  
  
|<span data-ttu-id="60019-106">Termo</span><span class="sxs-lookup"><span data-stu-id="60019-106">Term</span></span>|<span data-ttu-id="60019-107">Definição</span><span class="sxs-lookup"><span data-stu-id="60019-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="60019-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="60019-108">Required.</span></span> <span data-ttu-id="60019-109">Cadeia de caracteres que atua como o título de uma região quando ela é recolhida.</span><span class="sxs-lookup"><span data-stu-id="60019-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="60019-110">As regiões são recolhidas por padrão.</span><span class="sxs-lookup"><span data-stu-id="60019-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="60019-111">Encerra o `#Region` bloco.</span><span class="sxs-lookup"><span data-stu-id="60019-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60019-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="60019-112">Remarks</span></span>  

 <span data-ttu-id="60019-113">Use a `#Region` diretiva para especificar um bloco de código para expandir ou recolher ao usar o recurso de estrutura de tópicos do editor de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="60019-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="60019-114">Você pode posicionar ou *aninhar*regiões em outras regiões para agrupar regiões semelhantes.</span><span class="sxs-lookup"><span data-stu-id="60019-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60019-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60019-115">Example</span></span>  

 <span data-ttu-id="60019-116">Este exemplo usa a `#Region` diretiva.</span><span class="sxs-lookup"><span data-stu-id="60019-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="60019-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="60019-117">See also</span></span>

- [<span data-ttu-id="60019-118">#If... Diretivas then... #Else</span><span class="sxs-lookup"><span data-stu-id="60019-118">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="60019-119">Estrutura de tópicos</span><span class="sxs-lookup"><span data-stu-id="60019-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="60019-120">Como: Recolher e ocultar seções do código</span><span class="sxs-lookup"><span data-stu-id="60019-120">How to: Collapse and Hide Sections of Code</span></span>](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
