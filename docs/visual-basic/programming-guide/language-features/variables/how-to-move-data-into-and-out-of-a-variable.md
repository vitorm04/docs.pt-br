---
title: "Como inserir e remover dados de uma variável (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fefb1979e35cd7b5fa1917f8f1a57af575e51234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="58986-102">Como inserir e remover dados de uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58986-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="58986-103">Você pode armazenar um valor em uma variável, colocando o nome da variável no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="58986-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="58986-104">Colocar dados em uma variável</span><span class="sxs-lookup"><span data-stu-id="58986-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="58986-105">Para armazenar um valor em uma variável</span><span class="sxs-lookup"><span data-stu-id="58986-105">To store a value in a variable</span></span>  
  
-   <span data-ttu-id="58986-106">Use o nome da variável no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="58986-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="58986-107">O exemplo a seguir define o valor da variável `alpha`.</span><span class="sxs-lookup"><span data-stu-id="58986-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="58986-108">O valor gerado no lado direito da instrução de atribuição é armazenado na variável.</span><span class="sxs-lookup"><span data-stu-id="58986-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="58986-109">Obtendo dados de uma variável</span><span class="sxs-lookup"><span data-stu-id="58986-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="58986-110">Recuperar o valor da variável, incluindo o nome da variável em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="58986-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="58986-111">Para recuperar um valor de uma variável</span><span class="sxs-lookup"><span data-stu-id="58986-111">To retrieve a value from a variable</span></span>  
  
-   <span data-ttu-id="58986-112">Use o nome da variável em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="58986-112">Use the variable name in an expression.</span></span> <span data-ttu-id="58986-113">Você pode usar uma variável em qualquer lugar você pode usar uma constante ou um literal, exceto em uma expressão que define o valor de uma constante.</span><span class="sxs-lookup"><span data-stu-id="58986-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="58986-114">-ou-</span><span class="sxs-lookup"><span data-stu-id="58986-114">-or-</span></span>  
  
-   <span data-ttu-id="58986-115">Use o nome de variável seguido de igual (`=`) entrar em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="58986-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="58986-116">O exemplo a seguir lê o valor da variável `startValue` e, em seguida, usa o valor da variável `counter` em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="58986-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="58986-117">O valor da variável participa na expressão apenas como uma constante seria e, em seguida, ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="58986-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58986-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58986-118">See Also</span></span>  
 [<span data-ttu-id="58986-119">Variáveis</span><span class="sxs-lookup"><span data-stu-id="58986-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="58986-120">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="58986-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="58986-121">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="58986-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
