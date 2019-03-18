---
title: Expressões lambda tipadas implicitamente
description: Saiba porque você não pode usar uma declaração de variável tipada implicitamente para declarar uma expressão lambda.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 9b798f40676afaad2075806d6dc512f279bc7065
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58126091"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="e5da2-103">Expressões lambda tipadas implicitamente</span><span class="sxs-lookup"><span data-stu-id="e5da2-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="e5da2-104">Você não pode usar uma declaração de variável tipada implicitamente para declarar uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="e5da2-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="e5da2-105">Isso cria um problema de lógica circular para o compilador.</span><span class="sxs-lookup"><span data-stu-id="e5da2-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="e5da2-106">A declaração `var` diz ao compilador para descobrir o tipo da variável de acordo com o tipo da expressão no lado direito do operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="e5da2-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="e5da2-107">Uma expressão lambda não tem um tipo de tempo de compilação, mas pode ser convertida em qualquer tipo de delegado ou expressão correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5da2-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="e5da2-108">Quando atribui uma expressão lambda a uma variável de um tipo de delegado ou expressão, você diz ao compilador para tentar converter a expressão lambda em uma expressão ou delegado que corresponda à assinatura da variável "atribuída".</span><span class="sxs-lookup"><span data-stu-id="e5da2-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="e5da2-109">O compilador deve tentar fazer o item do lado direito da atribuição corresponder ao tipo do lado esquerdo da atribuição.</span><span class="sxs-lookup"><span data-stu-id="e5da2-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="e5da2-110">Os dois lados da atribuição não podem estar dizendo ao compilador para examinar o objeto do outro lado do operador de atribuição para ver se meu tipo é correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5da2-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="e5da2-111">Você pode obter mais detalhes sobre por quê a linguagem C# especifica esse comportamento lendo [este artigo](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (download do PDF)</span><span class="sxs-lookup"><span data-stu-id="e5da2-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>
