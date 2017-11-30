---
title: "Construtor &#39; &lt;nome&gt;&#39; não é possível chamar a mesmo"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords: BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2361d6f4d710e17a4f4e29ac03bfde523191fa83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a><span data-ttu-id="c8a9b-102">Construtor &#39; &lt;nome&gt;&#39; não é possível chamar a mesmo</span><span class="sxs-lookup"><span data-stu-id="c8a9b-102">Constructor &#39;&lt;name&gt;&#39; cannot call itself</span></span>
<span data-ttu-id="c8a9b-103">Um `Sub New` procedimento em uma classe ou estrutura chama a mesmo.</span><span class="sxs-lookup"><span data-stu-id="c8a9b-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="c8a9b-104">A finalidade de um construtor é inicializar uma instância de uma classe ou estrutura quando ele é o primeiro criado.</span><span class="sxs-lookup"><span data-stu-id="c8a9b-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="c8a9b-105">Uma classe ou estrutura pode ter vários construtores, contanto que todos tenham listas de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="c8a9b-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="c8a9b-106">Um construtor pode chamar outro construtor para executar sua funcionalidade além de seu próprio.</span><span class="sxs-lookup"><span data-stu-id="c8a9b-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="c8a9b-107">Mas não faz sentido um construtor chamar a mesmo e de fato resultaria em recursão infinita se permitido.</span><span class="sxs-lookup"><span data-stu-id="c8a9b-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="c8a9b-108">**ID do erro:** BC30298</span><span class="sxs-lookup"><span data-stu-id="c8a9b-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8a9b-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c8a9b-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="c8a9b-110">Verifique a lista de parâmetro do construtor sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="c8a9b-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="c8a9b-111">Ele deve ser diferente do construtor fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="c8a9b-111">It should be different from that of the constructor making the call.</span></span>  
  
2.  <span data-ttu-id="c8a9b-112">Se você não pretende chamar um construtor diferente, remova o `Sub New` chamar inteiramente.</span><span class="sxs-lookup"><span data-stu-id="c8a9b-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a9b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8a9b-113">See Also</span></span>  
 [<span data-ttu-id="c8a9b-114">Tempo de vida do objeto: como os objetos são criados e destruídos</span><span class="sxs-lookup"><span data-stu-id="c8a9b-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
