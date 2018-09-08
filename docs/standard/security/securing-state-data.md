---
title: Protegendo dados de estado
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c821177ca897e617885425217ac0b6659b5ea6e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44212224"
---
# <a name="securing-state-data"></a><span data-ttu-id="7bde7-102">Protegendo dados de estado</span><span class="sxs-lookup"><span data-stu-id="7bde7-102">Securing State Data</span></span>
<span data-ttu-id="7bde7-103">Aplicativos que lidam com dados confidenciais ou fazer qualquer tipo de decisões de segurança necessário manter esses dados em seu próprio controle e não é possível permitir que outro código potencialmente mal-intencionado acessar os dados diretamente.</span><span class="sxs-lookup"><span data-stu-id="7bde7-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="7bde7-104">A melhor maneira de proteger os dados na memória é declarar os dados como privado ou interno (com escopo limitado ao mesmo assembly) variáveis.</span><span class="sxs-lookup"><span data-stu-id="7bde7-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="7bde7-105">No entanto, até mesmo com esses dados são sujeito ao acesso, que você deve estar atento:</span><span class="sxs-lookup"><span data-stu-id="7bde7-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="7bde7-106">Usando mecanismos de reflexão, código altamente confiável que pode fazer referência a seu objeto pode obter e definir os membros privados.</span><span class="sxs-lookup"><span data-stu-id="7bde7-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="7bde7-107">Usando a serialização, código altamente confiável pode efetivamente obter e definir os membros privados se ele pode acessar os dados correspondentes no formato serializado do objeto.</span><span class="sxs-lookup"><span data-stu-id="7bde7-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="7bde7-108">Na depuração, esses dados podem ser lidos.</span><span class="sxs-lookup"><span data-stu-id="7bde7-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="7bde7-109">Verifique se nenhum dos seus próprios métodos ou propriedades expõe esses valores acidentalmente.</span><span class="sxs-lookup"><span data-stu-id="7bde7-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bde7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bde7-110">See also</span></span>

- [<span data-ttu-id="7bde7-111">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="7bde7-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
