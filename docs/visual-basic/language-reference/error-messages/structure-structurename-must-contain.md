---
title: A estrutura '<structurename>' deve conter pelos menos uma variável membro da instância ou pelo menos uma declaração de evento da instância não marcada como 'Personalizada'
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 4e7ef82659c43be08ee444eaf3f4df663f7aaa53
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159645"
---
# <a name="bc30941-structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="ab27a-102">BC30941: a estrutura ' \<structurename> ' deve conter pelo menos uma variável de membro de instância ou pelo menos uma declaração de evento de instância não marcada como ' Custom '</span><span class="sxs-lookup"><span data-stu-id="ab27a-102">BC30941: Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>

<span data-ttu-id="ab27a-103">Uma definição de estrutura não inclui nenhuma variável não compartilhada ou eventos não compartilhados não-personalizados.</span><span class="sxs-lookup"><span data-stu-id="ab27a-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>

 <span data-ttu-id="ab27a-104">Cada estrutura deve ter uma variável ou um evento que se aplica a cada instância específica (não compartilhada), em vez de a todas as instâncias coletivamente ([compartilhado](../modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="ab27a-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../modifiers/shared.md)).</span></span> <span data-ttu-id="ab27a-105">As constantes, as propriedades e os procedimentos não compartilhados não atendem a esse requisito.</span><span class="sxs-lookup"><span data-stu-id="ab27a-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="ab27a-106">Além disso, se não houver nenhuma variável não compartilhada e apenas um evento não compartilhado, esse evento não poderá ser um `Custom` evento.</span><span class="sxs-lookup"><span data-stu-id="ab27a-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>

 <span data-ttu-id="ab27a-107">**ID do erro:** BC30941</span><span class="sxs-lookup"><span data-stu-id="ab27a-107">**Error ID:** BC30941</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ab27a-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ab27a-108">To correct this error</span></span>

- <span data-ttu-id="ab27a-109">Defina pelo menos uma variável ou evento que não seja `Shared` .</span><span class="sxs-lookup"><span data-stu-id="ab27a-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="ab27a-110">Se você definir apenas um evento, ele deverá ser não personalizado, bem como não compartilhado.</span><span class="sxs-lookup"><span data-stu-id="ab27a-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab27a-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="ab27a-111">See also</span></span>

- [<span data-ttu-id="ab27a-112">Estruturas</span><span class="sxs-lookup"><span data-stu-id="ab27a-112">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ab27a-113">Como: Declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="ab27a-113">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="ab27a-114">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="ab27a-114">Structure Statement</span></span>](../statements/structure-statement.md)
