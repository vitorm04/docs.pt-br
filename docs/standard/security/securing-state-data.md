---
title: Protegendo dados de estado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd41f5174f426e723ea7e069eaee8f2d367625a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="securing-state-data"></a><span data-ttu-id="f116d-102">Protegendo dados de estado</span><span class="sxs-lookup"><span data-stu-id="f116d-102">Securing State Data</span></span>
<span data-ttu-id="f116d-103">Aplicativos que lidam com dados confidenciais ou fazer qualquer tipo de decisões de segurança necessário manter esses dados em seu próprio controle e não podem permitir que outros códigos possivelmente mal-intencionados acessem os dados diretamente.</span><span class="sxs-lookup"><span data-stu-id="f116d-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="f116d-104">É a melhor maneira de proteger os dados na memória para declarar os dados como privadas ou internas (com escopo limitado ao mesmo assembly) variáveis.</span><span class="sxs-lookup"><span data-stu-id="f116d-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="f116d-105">No entanto, até mesmo esses dados são sujeitas a acesso que deve estar atento:</span><span class="sxs-lookup"><span data-stu-id="f116d-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="f116d-106">Usando mecanismos de reflexão, código altamente confiável que pode fazer referência o objeto pode obter e definir membros particulares.</span><span class="sxs-lookup"><span data-stu-id="f116d-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="f116d-107">Uso de serialização, código altamente confiável pode efetivamente obter e definir membros particulares se ele pode acessar os dados correspondentes no formato serializado do objeto.</span><span class="sxs-lookup"><span data-stu-id="f116d-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="f116d-108">Na depuração, esses dados podem ser lidos.</span><span class="sxs-lookup"><span data-stu-id="f116d-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="f116d-109">Verifique se que nenhum dos seus próprios métodos ou propriedades expõe esses valores acidentalmente.</span><span class="sxs-lookup"><span data-stu-id="f116d-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f116d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f116d-110">See Also</span></span>  
 [<span data-ttu-id="f116d-111">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="f116d-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
