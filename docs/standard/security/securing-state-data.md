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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018548"
---
# <a name="securing-state-data"></a><span data-ttu-id="43bd4-102">Protegendo dados de estado</span><span class="sxs-lookup"><span data-stu-id="43bd4-102">Securing State Data</span></span>
<span data-ttu-id="43bd4-103">Aplicativos que lidam com dados confidenciais ou fazer qualquer tipo de decisões de segurança necessário manter esses dados em seu próprio controle e não é possível permitir que outro código potencialmente mal-intencionado acessar os dados diretamente.</span><span class="sxs-lookup"><span data-stu-id="43bd4-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="43bd4-104">A melhor maneira de proteger os dados na memória é declarar os dados como privado ou interno (com escopo limitado ao mesmo assembly) variáveis.</span><span class="sxs-lookup"><span data-stu-id="43bd4-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="43bd4-105">No entanto, até mesmo com esses dados são sujeito ao acesso, que você deve estar atento:</span><span class="sxs-lookup"><span data-stu-id="43bd4-105">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="43bd4-106">Usando mecanismos de reflexão, código altamente confiável que pode fazer referência a seu objeto pode obter e definir os membros privados.</span><span class="sxs-lookup"><span data-stu-id="43bd4-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="43bd4-107">Usando a serialização, código altamente confiável pode efetivamente obter e definir os membros privados se ele pode acessar os dados correspondentes no formato serializado do objeto.</span><span class="sxs-lookup"><span data-stu-id="43bd4-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="43bd4-108">Na depuração, esses dados podem ser lidos.</span><span class="sxs-lookup"><span data-stu-id="43bd4-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="43bd4-109">Verifique se nenhum dos seus próprios métodos ou propriedades expõe esses valores acidentalmente.</span><span class="sxs-lookup"><span data-stu-id="43bd4-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43bd4-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43bd4-110">See also</span></span>

- [<span data-ttu-id="43bd4-111">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="43bd4-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
