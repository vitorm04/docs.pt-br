---
title: Protegendo dados de estado
description: Declare os dados estatais como variáveis privadas ou internas para limitar o acesso a eles. Esses dados ainda podem ser acessados através de reflexão, serialização e depuração.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: f95bf409f7eef8c2636d3c180d2bbd95fbc689c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186818"
---
# <a name="securing-state-data"></a><span data-ttu-id="87766-104">Protegendo dados de estado</span><span class="sxs-lookup"><span data-stu-id="87766-104">Securing State Data</span></span>
<span data-ttu-id="87766-105">Aplicativos que lidam com dados confidenciais ou tomam qualquer tipo de decisão de segurança precisam manter esses dados seu próprio controle e não podem permitir que outro código potencialmente malicioso acesse os dados diretamente.</span><span class="sxs-lookup"><span data-stu-id="87766-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="87766-106">A melhor maneira de proteger dados na memória é declarar os dados como variáveis privadas ou internas (com escopo limitado ao mesmo conjunto).</span><span class="sxs-lookup"><span data-stu-id="87766-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="87766-107">No entanto, mesmo esses dados estão sujeitos ao acesso que você deve estar ciente:</span><span class="sxs-lookup"><span data-stu-id="87766-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="87766-108">Usando mecanismos de reflexão, um código altamente confiável que pode referenciar seu objeto pode obter e definir membros privados.</span><span class="sxs-lookup"><span data-stu-id="87766-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="87766-109">Usando serialização, o código altamente confiável pode efetivamente obter e definir membros privados se ele puder acessar os dados correspondentes na forma serializada do objeto.</span><span class="sxs-lookup"><span data-stu-id="87766-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="87766-110">depuração, esses dados podem ser lidos.</span><span class="sxs-lookup"><span data-stu-id="87766-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="87766-111">Certifique-se de que nenhum de seus próprios métodos ou propriedades exponha esses valores involuntariamente.</span><span class="sxs-lookup"><span data-stu-id="87766-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87766-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="87766-112">See also</span></span>

- [<span data-ttu-id="87766-113">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="87766-113">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
