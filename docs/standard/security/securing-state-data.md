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
ms.openlocfilehash: fe941fff7091fb579e41a3c417dbb2129bcf3e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580777"
---
# <a name="securing-state-data"></a><span data-ttu-id="19c0c-102">Protegendo dados de estado</span><span class="sxs-lookup"><span data-stu-id="19c0c-102">Securing State Data</span></span>
<span data-ttu-id="19c0c-103">Aplicativos que lidam com dados confidenciais ou fazer qualquer tipo de decisões de segurança necessário manter esses dados em seu próprio controle e não podem permitir que outros códigos possivelmente mal-intencionados acessem os dados diretamente.</span><span class="sxs-lookup"><span data-stu-id="19c0c-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="19c0c-104">É a melhor maneira de proteger os dados na memória para declarar os dados como privadas ou internas (com escopo limitado ao mesmo assembly) variáveis.</span><span class="sxs-lookup"><span data-stu-id="19c0c-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="19c0c-105">No entanto, até mesmo esses dados são sujeitas a acesso que deve estar atento:</span><span class="sxs-lookup"><span data-stu-id="19c0c-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="19c0c-106">Usando mecanismos de reflexão, código altamente confiável que pode fazer referência o objeto pode obter e definir membros particulares.</span><span class="sxs-lookup"><span data-stu-id="19c0c-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="19c0c-107">Uso de serialização, código altamente confiável pode efetivamente obter e definir membros particulares se ele pode acessar os dados correspondentes no formato serializado do objeto.</span><span class="sxs-lookup"><span data-stu-id="19c0c-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="19c0c-108">Na depuração, esses dados podem ser lidos.</span><span class="sxs-lookup"><span data-stu-id="19c0c-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="19c0c-109">Verifique se que nenhum dos seus próprios métodos ou propriedades expõe esses valores acidentalmente.</span><span class="sxs-lookup"><span data-stu-id="19c0c-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c0c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19c0c-110">See Also</span></span>  
 [<span data-ttu-id="19c0c-111">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="19c0c-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
