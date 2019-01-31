---
title: Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: b3aa66416f0cad6a6fb29a20aa0bca5e3486a18e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275425"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="46dad-102">Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '\<nome >'</span><span class="sxs-lookup"><span data-stu-id="46dad-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="46dad-103">Aplicativos de linha de comando devem ter um `Sub Main` definido.</span><span class="sxs-lookup"><span data-stu-id="46dad-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="46dad-104">`Main` deve ser declarado como `Public Shared` se ela é definida em uma classe, ou como `Public` se definida em um módulo.</span><span class="sxs-lookup"><span data-stu-id="46dad-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="46dad-105">**ID do erro:** BC30737</span><span class="sxs-lookup"><span data-stu-id="46dad-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46dad-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="46dad-106">To correct this error</span></span>  
  
-   <span data-ttu-id="46dad-107">Definir um `Public Sub Main` procedimento para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="46dad-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="46dad-108">Declare-o como `Shared` se e somente se você defini-lo dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="46dad-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46dad-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46dad-109">See also</span></span>
- [<span data-ttu-id="46dad-110">Estrutura de um programa Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46dad-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="46dad-111">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="46dad-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
