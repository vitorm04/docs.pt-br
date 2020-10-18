---
title: Referência obrigatória ao assembly '<assemblyname>' que contém a classe base '<classname>'
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: d2fb3498219dfe3318ec418ede250de818874ba9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162330"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="6bdb7-102">BC30007: referência necessária para o assembly ' \<assemblyname> ' que contém a classe base ' \<classname> '</span><span class="sxs-lookup"><span data-stu-id="6bdb7-102">BC30007: Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>

<span data-ttu-id="6bdb7-103">Referência necessária para o assembly ' \<assemblyname> ' que contém a classe base ' \<classname> '.</span><span class="sxs-lookup"><span data-stu-id="6bdb7-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="6bdb7-104">Adicione um ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6bdb7-104">Add one to your project.</span></span>

 <span data-ttu-id="6bdb7-105">A classe é definida em uma DLL (biblioteca de vínculo dinâmico) ou assembly que não é referenciada diretamente em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6bdb7-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="6bdb7-106">O compilador Visual Basic requer uma referência para evitar ambigüidade, caso a classe esteja definida em mais de uma DLL ou assembly.</span><span class="sxs-lookup"><span data-stu-id="6bdb7-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>

 <span data-ttu-id="6bdb7-107">**ID do erro:** BC30007</span><span class="sxs-lookup"><span data-stu-id="6bdb7-107">**Error ID:** BC30007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6bdb7-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6bdb7-108">To correct this error</span></span>

- <span data-ttu-id="6bdb7-109">Inclua o nome da DLL ou assembly não referenciado em suas referências de projeto.</span><span class="sxs-lookup"><span data-stu-id="6bdb7-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bdb7-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="6bdb7-110">See also</span></span>

- [<span data-ttu-id="6bdb7-111">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="6bdb7-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="6bdb7-112">Solução de Problemas de Referências Quebradas</span><span class="sxs-lookup"><span data-stu-id="6bdb7-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
