---
title: Não acessível &#39;principal&#39; método com uma assinatura apropriada foi encontrado em &#39; &lt;nome&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6a60e26a2bd0e31c0f92dbbfb2518c75f304d9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593214"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="fd1bc-102">Não acessível &#39;principal&#39; método com uma assinatura apropriada foi encontrado em &#39; &lt;nome&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="fd1bc-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="fd1bc-103">Aplicativos de linha de comando devem ter um `Sub Main` definido.</span><span class="sxs-lookup"><span data-stu-id="fd1bc-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="fd1bc-104">`Main` deve ser declarado como `Public Shared` se ele é definido em uma classe ou como `Public` se definido em um módulo.</span><span class="sxs-lookup"><span data-stu-id="fd1bc-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="fd1bc-105">**ID do erro:** BC30737</span><span class="sxs-lookup"><span data-stu-id="fd1bc-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd1bc-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="fd1bc-106">To correct this error</span></span>  
  
-   <span data-ttu-id="fd1bc-107">Definir um `Public Sub Main` procedimento para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="fd1bc-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="fd1bc-108">Declare-o como `Shared` somente se você defini-lo dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="fd1bc-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd1bc-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd1bc-109">See Also</span></span>  
 [<span data-ttu-id="fd1bc-110">Estrutura de um programa do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd1bc-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="fd1bc-111">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="fd1bc-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
