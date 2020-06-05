---
title: Padrão
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
ms.openlocfilehash: 0c2808795d6fcbad7892369fd7f460ebf0406093
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372966"
---
# <a name="default-visual-basic"></a><span data-ttu-id="e0437-102">Padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0437-102">Default (Visual Basic)</span></span>
<span data-ttu-id="e0437-103">Identifica uma propriedade como a propriedade padrão de sua classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="e0437-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0437-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0437-104">Remarks</span></span>  
 <span data-ttu-id="e0437-105">Uma classe, estrutura ou interface pode designar, no máximo, uma de suas propriedades como a *propriedade padrão*, desde que a propriedade aceite pelo menos um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e0437-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="e0437-106">Se o código fizer uma referência a uma classe ou estrutura sem especificar um membro, Visual Basic resolverá essa referência à propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="e0437-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="e0437-107">As propriedades padrão podem resultar em uma pequena redução em caracteres de código-fonte, mas podem tornar seu código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="e0437-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="e0437-108">Se o código de chamada não estiver familiarizado com sua classe ou estrutura, quando ele fizer uma referência ao nome da classe ou da estrutura, ele não poderá ter certeza se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="e0437-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="e0437-109">Isso pode levar a erros de compilador ou erros de lógica de tempo de execução sutis.</span><span class="sxs-lookup"><span data-stu-id="e0437-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="e0437-110">Você pode, de certa forma, reduzir a chance de erros de propriedade padrão sempre usando a [instrução Option Strict](../statements/option-strict-statement.md) para definir a verificação de tipo de compilador como `On` .</span><span class="sxs-lookup"><span data-stu-id="e0437-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="e0437-111">Se você estiver planejando usar uma classe ou estrutura predefinida em seu código, você deve determinar se ela tem uma propriedade padrão e, em caso afirmativo, qual é seu nome.</span><span class="sxs-lookup"><span data-stu-id="e0437-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="e0437-112">Devido a essas desvantagens, você deve considerar não definir propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="e0437-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="e0437-113">Para legibilidade de código, você também deve considerar sempre referir-se a todas as propriedades explicitamente, até mesmo propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="e0437-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="e0437-114">O `Default` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="e0437-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="e0437-115">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="e0437-115">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0437-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="e0437-116">See also</span></span>

- [<span data-ttu-id="e0437-117">Como declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e0437-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="e0437-118">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e0437-118">Keywords</span></span>](../keywords/index.md)
