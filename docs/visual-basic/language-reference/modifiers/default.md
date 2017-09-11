---
title: "Padrão (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Default
dev_langs:
- VB
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2fd5d2eac0e53f662bd44c4d5a55df4769d30c65
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="default-visual-basic"></a><span data-ttu-id="4efb7-102">Padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4efb7-102">Default (Visual Basic)</span></span>
<span data-ttu-id="4efb7-103">Identifica uma propriedade como a propriedade padrão da sua classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="4efb7-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4efb7-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="4efb7-104">Remarks</span></span>  
 <span data-ttu-id="4efb7-105">Uma classe, estrutura ou interface pode designar no máximo uma de suas propriedades como o *propriedade padrão*, desde que a propriedade aceite pelo menos um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4efb7-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="4efb7-106">Se o código faz referência a uma classe ou estrutura sem especificar um membro, Visual Basic toma essa referência para a propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="4efb7-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="4efb7-107">Propriedades padrão podem resultar em uma pequena redução nos caracteres de código fonte, mas eles podem tornar seu código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="4efb7-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="4efb7-108">Se o código de chamada não está familiarizado com sua classe ou estrutura, quando ele faz referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="4efb7-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="4efb7-109">Isso pode levar a erros de compilador ou lógica de tempo de execução sutis.</span><span class="sxs-lookup"><span data-stu-id="4efb7-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="4efb7-110">Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando o [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) para definir o tipo do compilador para `On`.</span><span class="sxs-lookup"><span data-stu-id="4efb7-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="4efb7-111">Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ele tem uma propriedade padrão e, nesse caso, o que seu nome é.</span><span class="sxs-lookup"><span data-stu-id="4efb7-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="4efb7-112">Por causa dessas desvantagens, você deve considerar não definir as propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="4efb7-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="4efb7-113">Para fins de legibilidade de código, você deve também considerar sempre referir-se a todas as propriedades explicitamente, mesmo propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="4efb7-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="4efb7-114">O `Default` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="4efb7-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="4efb7-115">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="4efb7-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4efb7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4efb7-116">See Also</span></span>  
 <span data-ttu-id="4efb7-117">[Como: declarar e chamar uma propriedade padrão no Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="4efb7-117">[How to: Declare and Call a Default Property in Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="4efb7-118"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)</span><span class="sxs-lookup"><span data-stu-id="4efb7-118"> [Keywords](../../../visual-basic/language-reference/keywords/index.md)</span></span>
