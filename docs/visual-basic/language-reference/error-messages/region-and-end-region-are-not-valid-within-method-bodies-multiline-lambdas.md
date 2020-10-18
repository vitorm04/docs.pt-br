---
title: As instruções '#Region' e '#End Region' não são válidas dentro dos corpos/lambdas de várias linhas do método
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c792fa1a42bde22959ae21439cb2a0a1e4be343f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162278"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="10413-102">BC32025: as instruções ' #Region ' e ' #End Region ' não são válidas em corpos de método/lambdas de várias linhas</span><span class="sxs-lookup"><span data-stu-id="10413-102">BC32025: '#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="10413-103">O `#Region` bloco deve ser declarado em um nível de classe, módulo ou namespace.</span><span class="sxs-lookup"><span data-stu-id="10413-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="10413-104">Uma região recolhível pode incluir um ou mais procedimentos, mas não pode começar ou terminar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="10413-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>

 <span data-ttu-id="10413-105">**ID do erro:** BC32025</span><span class="sxs-lookup"><span data-stu-id="10413-105">**Error ID:** BC32025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="10413-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="10413-106">To correct this error</span></span>

1. <span data-ttu-id="10413-107">Verifique se o procedimento anterior foi encerrado corretamente com `End Function` uma `End Sub` instrução ou.</span><span class="sxs-lookup"><span data-stu-id="10413-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="10413-108">Verifique se as `#Region` `#End Region` diretivas e estão no mesmo bloco de código.</span><span class="sxs-lookup"><span data-stu-id="10413-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>

## <a name="see-also"></a><span data-ttu-id="10413-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="10413-109">See also</span></span>

- [<span data-ttu-id="10413-110">#Region diretiva</span><span class="sxs-lookup"><span data-stu-id="10413-110">#Region Directive</span></span>](../directives/region-directive.md)
