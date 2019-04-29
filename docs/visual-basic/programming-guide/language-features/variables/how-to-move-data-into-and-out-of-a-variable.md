---
title: 'Como: Mover dados dentro e fora de uma variável (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 30d1c0ab91724ac556e59b272782513ee8b8067b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756592"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="0e17c-102">Como: Mover dados dentro e fora de uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e17c-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="0e17c-103">Você pode armazenar um valor em uma variável, colocando o nome da variável no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="0e17c-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="0e17c-104">Colocar dados em uma variável</span><span class="sxs-lookup"><span data-stu-id="0e17c-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="0e17c-105">Para armazenar um valor em uma variável</span><span class="sxs-lookup"><span data-stu-id="0e17c-105">To store a value in a variable</span></span>  
  
- <span data-ttu-id="0e17c-106">Use o nome da variável no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="0e17c-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="0e17c-107">O exemplo a seguir define o valor da variável `alpha`.</span><span class="sxs-lookup"><span data-stu-id="0e17c-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="0e17c-108">O valor gerado no lado direito da instrução de atribuição é armazenado na variável.</span><span class="sxs-lookup"><span data-stu-id="0e17c-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="0e17c-109">Obtendo dados de uma variável</span><span class="sxs-lookup"><span data-stu-id="0e17c-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="0e17c-110">Para recuperar um valor de variável, incluindo o nome da variável em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="0e17c-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="0e17c-111">Para recuperar um valor de uma variável</span><span class="sxs-lookup"><span data-stu-id="0e17c-111">To retrieve a value from a variable</span></span>  
  
- <span data-ttu-id="0e17c-112">Use o nome da variável em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="0e17c-112">Use the variable name in an expression.</span></span> <span data-ttu-id="0e17c-113">Você pode usar uma variável em qualquer lugar você pode usar uma constante ou um literal, exceto em uma expressão que define o valor de uma constante.</span><span class="sxs-lookup"><span data-stu-id="0e17c-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="0e17c-114">- ou -</span><span class="sxs-lookup"><span data-stu-id="0e17c-114">-or-</span></span>  
  
- <span data-ttu-id="0e17c-115">Use o nome da variável igual a seguir (`=`) entrar em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="0e17c-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="0e17c-116">O exemplo a seguir lê o valor da variável `startValue` e, em seguida, usa o valor da variável `counter` em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="0e17c-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="0e17c-117">O valor da variável participa na expressão, assim como seria uma constante e, em seguida, ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="0e17c-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e17c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e17c-118">See also</span></span>

- [<span data-ttu-id="0e17c-119">Variáveis</span><span class="sxs-lookup"><span data-stu-id="0e17c-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="0e17c-120">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="0e17c-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="0e17c-121">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="0e17c-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
