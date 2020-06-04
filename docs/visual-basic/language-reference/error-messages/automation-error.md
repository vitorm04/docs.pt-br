---
title: Erro de automação
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: d62ba57db8bffefb2cfebed705251d87fe285602
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409888"
---
# <a name="automation-error"></a><span data-ttu-id="6275d-102">Erro de automação</span><span class="sxs-lookup"><span data-stu-id="6275d-102">Automation error</span></span>

<span data-ttu-id="6275d-103">Ocorreu um erro ao executar um método ou ao obter ou configurar uma propriedade de uma variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="6275d-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="6275d-104">O erro foi relatado pelo aplicativo que criou o objeto.</span><span class="sxs-lookup"><span data-stu-id="6275d-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6275d-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6275d-105">To correct this error</span></span>  
  
1. <span data-ttu-id="6275d-106">Verifique as propriedades do objeto `Err` para determinar a origem e a natureza do erro.</span><span class="sxs-lookup"><span data-stu-id="6275d-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="6275d-107">Use a instrução `On Error Resume Next` imediatamente antes de acessar a instrução e, em seguida, verifique se há erros imediatamente após acessar a instrução.</span><span class="sxs-lookup"><span data-stu-id="6275d-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6275d-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="6275d-108">See also</span></span>

- [<span data-ttu-id="6275d-109">Tipos de erro</span><span class="sxs-lookup"><span data-stu-id="6275d-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="6275d-110">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="6275d-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
