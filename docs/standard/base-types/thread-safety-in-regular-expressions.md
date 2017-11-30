---
title: "Acesso thread-safe em expressões regulares"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4cfa24da8083eac01275ad76f5c2db974b39a25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="097e1-102">Acesso thread-safe em expressões regulares</span><span class="sxs-lookup"><span data-stu-id="097e1-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="097e1-103">O <xref:System.Text.RegularExpressions.Regex> própria classe é thread-safe e imutável (somente leitura).</span><span class="sxs-lookup"><span data-stu-id="097e1-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="097e1-104">Ou seja, os objetos de **Regex** podem ser criados em qualquer thread e compartilhados entre os threads. Métodos correspondentes podem ser chamados de qualquer thread e nunca alteram nenhum estado global.</span><span class="sxs-lookup"><span data-stu-id="097e1-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="097e1-105">No entanto, os objetos de resultado (**correspondência** e **MatchCollection**) retornado por **Regex** deve ser usado em um único thread.</span><span class="sxs-lookup"><span data-stu-id="097e1-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="097e1-106">Embora muitos desses objetos sejam logicamente imutáveis, suas implementações poderiam atrasar a computação de alguns resultados para melhorar o desempenho e, como resultado, os chamadores devem serializar o acesso a eles.</span><span class="sxs-lookup"><span data-stu-id="097e1-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="097e1-107">Se houver a necessidade de compartilhar os objetos de resultado da **Regex** em vários threads, esses objetos poderão ser convertidos em instâncias thread-safe chamando seus métodos sincronizados.</span><span class="sxs-lookup"><span data-stu-id="097e1-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="097e1-108">Com exceção dos enumeradores, todas as classes de expressões regulares são thread-safe ou podem ser convertidas em objetos thread-safe por um método sincronizado.</span><span class="sxs-lookup"><span data-stu-id="097e1-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="097e1-109">Os enumeradores são a única exceção.</span><span class="sxs-lookup"><span data-stu-id="097e1-109">Enumerators are the only exception.</span></span> <span data-ttu-id="097e1-110">Um aplicativo precisa serializar as chamadas a enumeradores de coleções.</span><span class="sxs-lookup"><span data-stu-id="097e1-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="097e1-111">A regra é que se uma coleção pode ser enumerada em mais de um thread simultaneamente, você deve sincronizar os métodos do enumerador no objeto raiz da coleção percorrida pelo enumerador.</span><span class="sxs-lookup"><span data-stu-id="097e1-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097e1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="097e1-112">See Also</span></span>  
 [<span data-ttu-id="097e1-113">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="097e1-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
