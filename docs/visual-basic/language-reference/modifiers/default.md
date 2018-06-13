---
title: Padrão (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: 555e15110c7af501de05d1f395a72ca4b7800054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595129"
---
# <a name="default-visual-basic"></a><span data-ttu-id="815ae-102">Padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="815ae-102">Default (Visual Basic)</span></span>
<span data-ttu-id="815ae-103">Identifica uma propriedade como a propriedade padrão de sua classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="815ae-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="815ae-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="815ae-104">Remarks</span></span>  
 <span data-ttu-id="815ae-105">Uma classe, estrutura ou interface pode designar no máximo uma de suas propriedades como o *propriedade padrão*, desde que a propriedade tem pelo menos um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="815ae-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="815ae-106">Se o código faz referência a uma classe ou estrutura sem especificar um membro, Visual Basic toma essa referência para a propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="815ae-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="815ae-107">Propriedades padrão podem resultar em uma pequena redução nos caracteres de código fonte, mas eles podem tornar o seu código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="815ae-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="815ae-108">Se o código de chamada não está familiarizado com sua classe ou estrutura, quando ele faz referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="815ae-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="815ae-109">Isso pode levar a erros de compilador ou erros de lógica de tempo de execução sutis.</span><span class="sxs-lookup"><span data-stu-id="815ae-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="815ae-110">Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando o [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) para definir o tipo de compilador verificação `On`.</span><span class="sxs-lookup"><span data-stu-id="815ae-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="815ae-111">Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ela tem uma propriedade padrão e nesse caso, o que seu nome é.</span><span class="sxs-lookup"><span data-stu-id="815ae-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="815ae-112">Devido a essas desvantagens, você deve considerar não definir as propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="815ae-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="815ae-113">Para a legibilidade do código, você deve também considerar sempre referir-se a todas as propriedades explicitamente, mesmo propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="815ae-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="815ae-114">O `Default` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="815ae-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="815ae-115">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="815ae-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="815ae-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="815ae-116">See Also</span></span>  
 [<span data-ttu-id="815ae-117">Como: declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="815ae-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="815ae-118">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="815ae-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
