---
title: Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '<name>'
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6760b931ceb2ad5c2c04169d664da8629badc487
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409407"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="7e135-102">Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '\<name>'</span><span class="sxs-lookup"><span data-stu-id="7e135-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="7e135-103">Os aplicativos de linha de comando devem ter um `Sub Main` definido.</span><span class="sxs-lookup"><span data-stu-id="7e135-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="7e135-104">`Main`deve ser declarado como `Public Shared` se fosse definido em uma classe, ou como `Public` se estiver definido em um módulo.</span><span class="sxs-lookup"><span data-stu-id="7e135-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="7e135-105">**ID do erro:** BC30737</span><span class="sxs-lookup"><span data-stu-id="7e135-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e135-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7e135-106">To correct this error</span></span>  
  
- <span data-ttu-id="7e135-107">Defina um `Public Sub Main` procedimento para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7e135-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="7e135-108">Declare-a como `Shared` If e only se você defini-la dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="7e135-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e135-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e135-109">See also</span></span>

- [<span data-ttu-id="7e135-110">Estrutura de um programa Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7e135-110">Structure of a Visual Basic Program</span></span>](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="7e135-111">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="7e135-111">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
