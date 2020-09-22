---
title: A classe não dá suporte à automação ou à interface esperada
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: aa97ae420a0a289979fe86db373c635361dc6475
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874639"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="035d1-102">A classe não dá suporte à automação ou à interface esperada</span><span class="sxs-lookup"><span data-stu-id="035d1-102">Class does not support Automation or does not support expected interface</span></span>

<span data-ttu-id="035d1-103">A classe especificada na chamada de função `GetObject` ou `CreateObject` não expôs uma interface de programação ou você alterou um projeto de .dll para .exe, ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="035d1-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="035d1-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="035d1-104">To correct this error</span></span>  
  
1. <span data-ttu-id="035d1-105">Verifique a documentação do aplicativo que criou o objeto para obter as limitações sobre o uso de automação com esta classe de objeto.</span><span class="sxs-lookup"><span data-stu-id="035d1-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="035d1-106">Se você alterou um projeto de .dll para .exe, ou vice-versa, deverá cancelar o registro manualmente do .dll ou do .exe antigo.</span><span class="sxs-lookup"><span data-stu-id="035d1-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035d1-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="035d1-107">See also</span></span>

- [<span data-ttu-id="035d1-108">Tipos de erro</span><span class="sxs-lookup"><span data-stu-id="035d1-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="035d1-109">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="035d1-109">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
