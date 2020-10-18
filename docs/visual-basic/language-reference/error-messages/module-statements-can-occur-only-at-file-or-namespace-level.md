---
title: Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: b946a527d3de3a030ac03691c77afcf440f518ee
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160308"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="0e083-102">BC30617: instruções ' module ' só podem ocorrer em nível de arquivo ou de namespace</span><span class="sxs-lookup"><span data-stu-id="0e083-102">BC30617: 'Module' statements can occur only at file or namespace level</span></span>

<span data-ttu-id="0e083-103">`Module` as instruções devem aparecer na parte superior do arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="0e083-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>

 <span data-ttu-id="0e083-104">**ID do erro:** BC30617</span><span class="sxs-lookup"><span data-stu-id="0e083-104">**Error ID:** BC30617</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0e083-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0e083-105">To correct this error</span></span>

- <span data-ttu-id="0e083-106">Mova a `Module` instrução para a parte superior da sua declaração de namespace ou arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="0e083-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e083-107">Veja também</span><span class="sxs-lookup"><span data-stu-id="0e083-107">See also</span></span>

- [<span data-ttu-id="0e083-108">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="0e083-108">Module Statement</span></span>](../statements/module-statement.md)
