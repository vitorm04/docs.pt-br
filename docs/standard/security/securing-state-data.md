---
title: Protegendo dados de estado
description: Declare os dados de estado como variáveis privadas ou internas para limitar o acesso a ele. Esses dados ainda podem ser acessados por meio de reflexão, serialização e depuração.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: b7fcb520fe6fa28cc098c4e1cbb56ce7da759c11
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291039"
---
# <a name="securing-state-data"></a><span data-ttu-id="65458-104">Protegendo dados de estado</span><span class="sxs-lookup"><span data-stu-id="65458-104">Securing State Data</span></span>
<span data-ttu-id="65458-105">Os aplicativos que lidam com dados confidenciais ou que fazem qualquer tipo de decisões de segurança precisam manter esses dados sob seu próprio controle e não podem permitir que outros códigos potencialmente mal-intencionados acessem os dados diretamente.</span><span class="sxs-lookup"><span data-stu-id="65458-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="65458-106">A melhor maneira de proteger os dados na memória é declarar os dados como privados ou internos (com escopo limitado às variáveis do mesmo assembly).</span><span class="sxs-lookup"><span data-stu-id="65458-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="65458-107">No entanto, mesmo esses dados estão sujeitos ao acesso que você deve estar ciente:</span><span class="sxs-lookup"><span data-stu-id="65458-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="65458-108">Usando mecanismos de reflexão, um código altamente confiável que pode fazer referência a seu objeto pode obter e definir membros privados.</span><span class="sxs-lookup"><span data-stu-id="65458-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="65458-109">Usar o código de serialização e altamente confiável pode efetivamente obter e definir membros privados se puder acessar os dados correspondentes na forma serializada do objeto.</span><span class="sxs-lookup"><span data-stu-id="65458-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="65458-110">Em depuração, esses dados podem ser lidos.</span><span class="sxs-lookup"><span data-stu-id="65458-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="65458-111">Certifique-se de que nenhum de seus próprios métodos ou Propriedades exponha esses valores involuntariamente.</span><span class="sxs-lookup"><span data-stu-id="65458-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65458-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="65458-112">See also</span></span>

- [<span data-ttu-id="65458-113">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="65458-113">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
