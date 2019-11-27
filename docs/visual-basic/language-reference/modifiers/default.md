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
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351575"
---
# <a name="default-visual-basic"></a><span data-ttu-id="3411a-102">Padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3411a-102">Default (Visual Basic)</span></span>
<span data-ttu-id="3411a-103">Identifica uma propriedade como a propriedade padrão de sua classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="3411a-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3411a-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="3411a-104">Remarks</span></span>  
 <span data-ttu-id="3411a-105">Uma classe, estrutura ou interface pode designar, no máximo, uma de suas propriedades como a *propriedade padrão*, desde que a propriedade aceite pelo menos um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3411a-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="3411a-106">Se o código fizer uma referência a uma classe ou estrutura sem especificar um membro, Visual Basic resolverá essa referência à propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="3411a-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="3411a-107">As propriedades padrão podem resultar em uma pequena redução em caracteres de código-fonte, mas podem tornar seu código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="3411a-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="3411a-108">Se o código de chamada não estiver familiarizado com sua classe ou estrutura, quando ele fizer uma referência ao nome da classe ou da estrutura, ele não poderá ter certeza se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="3411a-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="3411a-109">Isso pode levar a erros de compilador ou erros de lógica de tempo de execução sutis.</span><span class="sxs-lookup"><span data-stu-id="3411a-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="3411a-110">Você pode, de certa forma, reduzir a chance de erros de propriedade padrão sempre usando a [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) para definir a verificação de tipo de compilador para `On`.</span><span class="sxs-lookup"><span data-stu-id="3411a-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="3411a-111">Se você estiver planejando usar uma classe ou estrutura predefinida em seu código, você deve determinar se ela tem uma propriedade padrão e, em caso afirmativo, qual é seu nome.</span><span class="sxs-lookup"><span data-stu-id="3411a-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="3411a-112">Devido a essas desvantagens, você deve considerar não definir propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="3411a-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="3411a-113">Para legibilidade de código, você também deve considerar sempre referir-se a todas as propriedades explicitamente, até mesmo propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="3411a-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="3411a-114">O modificador de `Default` pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="3411a-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="3411a-115">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="3411a-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3411a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3411a-116">See also</span></span>

- [<span data-ttu-id="3411a-117">Como: declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3411a-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="3411a-118">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3411a-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
