---
title: Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 559c905d1e2e2de4500771a93d6116f9630011ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591990"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="9c14f-102">Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '\<nome >'</span><span class="sxs-lookup"><span data-stu-id="9c14f-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="9c14f-103">Aplicativos de linha de comando devem ter um `Sub Main` definido.</span><span class="sxs-lookup"><span data-stu-id="9c14f-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="9c14f-104">`Main` deve ser declarado como `Public Shared` se ela é definida em uma classe, ou como `Public` se definida em um módulo.</span><span class="sxs-lookup"><span data-stu-id="9c14f-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="9c14f-105">**ID do erro:** BC30737</span><span class="sxs-lookup"><span data-stu-id="9c14f-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c14f-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9c14f-106">To correct this error</span></span>  
  
- <span data-ttu-id="9c14f-107">Definir um `Public Sub Main` procedimento para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="9c14f-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="9c14f-108">Declare-o como `Shared` se e somente se você defini-lo dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="9c14f-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c14f-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c14f-109">See also</span></span>

- [<span data-ttu-id="9c14f-110">Estrutura de um programa Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c14f-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="9c14f-111">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="9c14f-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
