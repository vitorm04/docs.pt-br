---
title: Não é possível carregar informações da classe '<classname>'
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 05c3303db90a396479bc396c5c2395c3afbb59ae
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161602"
---
# <a name="bc30712-unable-to-load-information-for-class-classname"></a><span data-ttu-id="4d983-102">BC30712: não é possível carregar informações para a classe ' \<classname> '</span><span class="sxs-lookup"><span data-stu-id="4d983-102">BC30712: Unable to load information for class '\<classname>'</span></span>

<span data-ttu-id="4d983-103">Foi feita uma referência a uma classe que não está disponível.</span><span class="sxs-lookup"><span data-stu-id="4d983-103">A reference was made to a class that is not available.</span></span>

 <span data-ttu-id="4d983-104">**ID do erro:** BC30712</span><span class="sxs-lookup"><span data-stu-id="4d983-104">**Error ID:** BC30712</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4d983-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4d983-105">To correct this error</span></span>

1. <span data-ttu-id="4d983-106">Verifique se a classe está definida e se você escreveu o nome corretamente.</span><span class="sxs-lookup"><span data-stu-id="4d983-106">Verify that the class is defined and that you spelled the name correctly.</span></span>

2. <span data-ttu-id="4d983-107">Tente acessar um dos membros declarados no módulo.</span><span class="sxs-lookup"><span data-stu-id="4d983-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="4d983-108">Em alguns casos, o ambiente de depuração não pode localizar membros porque os módulos em que eles estão declarados ainda não foram carregados.</span><span class="sxs-lookup"><span data-stu-id="4d983-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d983-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="4d983-109">See also</span></span>

- [<span data-ttu-id="4d983-110">Depurando no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4d983-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
