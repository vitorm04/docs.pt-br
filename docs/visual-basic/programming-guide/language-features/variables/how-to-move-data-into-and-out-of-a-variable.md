---
title: "Como: mover dados dentro e fora de uma variável (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: 14
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
ms.openlocfilehash: e97ea7327e76acc3578e3f3f6dd1260dac39f032
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="58d79-102">Como inserir e remover dados de uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58d79-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="58d79-103">Você pode armazenar um valor em uma variável, colocando o nome da variável no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="58d79-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="58d79-104">Colocar dados em uma variável</span><span class="sxs-lookup"><span data-stu-id="58d79-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="58d79-105">Para armazenar um valor em uma variável</span><span class="sxs-lookup"><span data-stu-id="58d79-105">To store a value in a variable</span></span>  
  
-   <span data-ttu-id="58d79-106">Use o nome da variável no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="58d79-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="58d79-107">O exemplo a seguir define o valor da variável `alpha`.</span><span class="sxs-lookup"><span data-stu-id="58d79-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="58d79-108">O valor gerado no lado direito da instrução de atribuição é armazenado na variável.</span><span class="sxs-lookup"><span data-stu-id="58d79-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="58d79-109">Obtendo dados de uma variável</span><span class="sxs-lookup"><span data-stu-id="58d79-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="58d79-110">Para recuperar um valor de variável, incluindo o nome da variável em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="58d79-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="58d79-111">Para recuperar um valor de uma variável</span><span class="sxs-lookup"><span data-stu-id="58d79-111">To retrieve a value from a variable</span></span>  
  
-   <span data-ttu-id="58d79-112">Use o nome da variável em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="58d79-112">Use the variable name in an expression.</span></span> <span data-ttu-id="58d79-113">Você pode usar uma variável em qualquer lugar você pode usar uma constante ou um literal, exceto em uma expressão que define o valor de uma constante.</span><span class="sxs-lookup"><span data-stu-id="58d79-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="58d79-114">-ou-</span><span class="sxs-lookup"><span data-stu-id="58d79-114">-or-</span></span>  
  
-   <span data-ttu-id="58d79-115">Use o nome de variável seguido de igual (`=`) entrar em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="58d79-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="58d79-116">O exemplo a seguir lê o valor da variável `startValue` e, em seguida, usa o valor da variável `counter` em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="58d79-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="58d79-117">O valor da variável participa na expressão apenas como uma constante participaria, e, em seguida, ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="58d79-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d79-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58d79-118">See Also</span></span>  
 <span data-ttu-id="58d79-119">[Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span><span class="sxs-lookup"><span data-stu-id="58d79-119">[Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span></span>  
<span data-ttu-id="58d79-120"> [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="58d79-120"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="58d79-121"> [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)</span><span class="sxs-lookup"><span data-stu-id="58d79-121"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)</span></span>
