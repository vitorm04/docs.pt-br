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
ms.openlocfilehash: c30bd2fe9e1ed371be2db60739d3b329fea788c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705893"
---
# <a name="securing-state-data"></a><span data-ttu-id="4f0b7-102">Protegendo dados de estado</span><span class="sxs-lookup"><span data-stu-id="4f0b7-102">Securing State Data</span></span>
<span data-ttu-id="4f0b7-103">Os aplicativos que lidam com dados confidenciais ou que fazem qualquer tipo de decisões de segurança precisam manter esses dados sob seu próprio controle e não podem permitir que outros códigos potencialmente mal-intencionados acessem os dados diretamente.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="4f0b7-104">A melhor maneira de proteger os dados na memória é declarar os dados como privados ou internos (com escopo limitado às variáveis do mesmo assembly).</span><span class="sxs-lookup"><span data-stu-id="4f0b7-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="4f0b7-105">No entanto, mesmo esses dados estão sujeitos ao acesso que você deve estar ciente:</span><span class="sxs-lookup"><span data-stu-id="4f0b7-105">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="4f0b7-106">Usando mecanismos de reflexão, um código altamente confiável que pode fazer referência a seu objeto pode obter e definir membros privados.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="4f0b7-107">Usar o código de serialização e altamente confiável pode efetivamente obter e definir membros privados se puder acessar os dados correspondentes na forma serializada do objeto.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="4f0b7-108">Em depuração, esses dados podem ser lidos.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="4f0b7-109">Certifique-se de que nenhum de seus próprios métodos ou Propriedades exponha esses valores involuntariamente.</span><span class="sxs-lookup"><span data-stu-id="4f0b7-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f0b7-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="4f0b7-110">See also</span></span>

- [<span data-ttu-id="4f0b7-111">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="4f0b7-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
