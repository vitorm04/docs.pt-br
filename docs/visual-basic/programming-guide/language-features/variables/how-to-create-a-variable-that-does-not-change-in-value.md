---
title: "Como: criar uma variável que não se altera em valor (Visual Basic) | Documentos do Microsoft"
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
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: 15
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 6ffcff3536bc36e2269c2b7f9e0d33ebadbcba26
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="e69da-102">Como criar uma variável que não se altera no valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e69da-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>
<span data-ttu-id="e69da-103">A noção de uma variável que não altera seu valor pode parecer contraditório.</span><span class="sxs-lookup"><span data-stu-id="e69da-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="e69da-104">Mas há situações quando uma constante não é viável e é útil ter uma variável com um valor fixo.</span><span class="sxs-lookup"><span data-stu-id="e69da-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="e69da-105">Nesse caso, você pode definir uma variável de membro com o [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e69da-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
 <span data-ttu-id="e69da-106">Não é possível usar o [instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md) para declarar e atribua um valor constante nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="e69da-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>  
  
-   <span data-ttu-id="e69da-107">O `Const` instrução não aceita o tipo de dados que você deseja usar</span><span class="sxs-lookup"><span data-stu-id="e69da-107">The `Const` statement does not accept the data type you want to use</span></span>  
  
-   <span data-ttu-id="e69da-108">Você não sabe o valor em tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="e69da-108">You do not know the value at compile time</span></span>  
  
-   <span data-ttu-id="e69da-109">Não for possível computar o valor da constante em tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="e69da-109">You are unable to compute the constant value at compile time</span></span>  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="e69da-110">Para criar uma variável que não se altera em valor</span><span class="sxs-lookup"><span data-stu-id="e69da-110">To create a variable that does not change in value</span></span>  
  
1.  <span data-ttu-id="e69da-111">No nível de módulo, declare uma variável de membro com o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)e incluem o [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e69da-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     <span data-ttu-id="e69da-112">Você pode especificar `ReadOnly` apenas em um variável de membro.</span><span class="sxs-lookup"><span data-stu-id="e69da-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="e69da-113">Isso significa que você deve definir a variável no nível de módulo, fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="e69da-113">This means you must define the variable at module level, outside of any procedure.</span></span>  
  
2.  <span data-ttu-id="e69da-114">Se você pode calcular o valor em uma única instrução em tempo de compilação, use uma cláusula de inicialização no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="e69da-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="e69da-115">Execute o [como](../../../../visual-basic/language-reference/statements/as-clause.md) cláusula com um sinal de igual (`=`), seguido por uma expressão.</span><span class="sxs-lookup"><span data-stu-id="e69da-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="e69da-116">Certifique-se de que o compilador pode avaliar esta expressão para um valor constante.</span><span class="sxs-lookup"><span data-stu-id="e69da-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     <span data-ttu-id="e69da-117">Você pode atribuir um valor para um `ReadOnly` variável somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="e69da-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="e69da-118">Quando você fizer isso, nenhum código pode alterar seu valor.</span><span class="sxs-lookup"><span data-stu-id="e69da-118">Once you do so, no code can ever change its value.</span></span>  
  
     <span data-ttu-id="e69da-119">Se você não sabe o valor em tempo de compilação, ou não é possível calcular em tempo de compilação em uma única instrução, você ainda pode atribui-lo em tempo de execução em um construtor.</span><span class="sxs-lookup"><span data-stu-id="e69da-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="e69da-120">Para fazer isso, você deve declarar o `ReadOnly` variável no nível de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e69da-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="e69da-121">No construtor de classe ou estrutura, calcular o valor da variável fixa e atribuí-la à variável antes de retornar do construtor.</span><span class="sxs-lookup"><span data-stu-id="e69da-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e69da-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e69da-122">See Also</span></span>  
 <span data-ttu-id="e69da-123">[WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md) </span><span class="sxs-lookup"><span data-stu-id="e69da-123">[WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md) </span></span>  
<span data-ttu-id="e69da-124"> [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)</span><span class="sxs-lookup"><span data-stu-id="e69da-124"> [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)</span></span>

