---
title: "Construtor &quot;&lt;nome&gt;&quot; não pode chamar a mesmo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
dev_langs:
- VB
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: eb1aa1631775b9bf7c416891a05cd61ea19e9d7e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a><span data-ttu-id="ab08b-102">Construtor '&lt;nome&gt;' não pode chamar a mesmo</span><span class="sxs-lookup"><span data-stu-id="ab08b-102">Constructor &#39;&lt;name&gt;&#39; cannot call itself</span></span>
<span data-ttu-id="ab08b-103">Um `Sub New` procedimento em uma classe ou estrutura chama a mesmo.</span><span class="sxs-lookup"><span data-stu-id="ab08b-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="ab08b-104">A finalidade de um construtor é inicializar uma instância de uma classe ou estrutura quando ela é primeiro criado.</span><span class="sxs-lookup"><span data-stu-id="ab08b-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="ab08b-105">Uma classe ou estrutura pode ter vários construtores, desde que todos eles têm diferentes listas de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ab08b-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="ab08b-106">Um construtor pode chamar outro construtor para executar sua funcionalidade além de seu próprio.</span><span class="sxs-lookup"><span data-stu-id="ab08b-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="ab08b-107">Mas não faz sentido um construtor chamar a próprio e, de fato resultaria em recursão infinita se permitido.</span><span class="sxs-lookup"><span data-stu-id="ab08b-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="ab08b-108">**ID do erro:** BC30298</span><span class="sxs-lookup"><span data-stu-id="ab08b-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab08b-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ab08b-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="ab08b-110">Verifique a lista de parâmetro do construtor sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="ab08b-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="ab08b-111">Ele deve ser diferente do construtor fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="ab08b-111">It should be different from that of the constructor making the call.</span></span>  
  
2.  <span data-ttu-id="ab08b-112">Se você não pretende chamar um construtor diferente, remova o `Sub New` chamar inteiramente.</span><span class="sxs-lookup"><span data-stu-id="ab08b-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab08b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab08b-113">See Also</span></span>  
 [<span data-ttu-id="ab08b-114">Tempo de vida do objeto: como os objetos são criados e destruídos</span><span class="sxs-lookup"><span data-stu-id="ab08b-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
