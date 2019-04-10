---
title: 'Como: Obter um valor de uma propriedade (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302927"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="77722-102">Como: Obter um valor de uma propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77722-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="77722-103">Para recuperar um valor de propriedade, incluindo o nome da propriedade em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="77722-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="77722-104">A propriedade `Get` procedimento recupera o valor, mas você não o chame explicitamente por nome.</span><span class="sxs-lookup"><span data-stu-id="77722-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="77722-105">Você usar a propriedade, assim como você usaria uma variável.</span><span class="sxs-lookup"><span data-stu-id="77722-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="77722-106">O Visual Basic faz as chamadas para procedimentos da propriedade.</span><span class="sxs-lookup"><span data-stu-id="77722-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="77722-107">Para recuperar um valor de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="77722-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="77722-108">Use o nome da propriedade em uma expressão da mesma maneira que você usaria um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="77722-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="77722-109">Você pode usar uma propriedade em qualquer lugar você pode usar uma variável ou uma constante.</span><span class="sxs-lookup"><span data-stu-id="77722-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="77722-110">- ou -</span><span class="sxs-lookup"><span data-stu-id="77722-110">-or-</span></span>  
  
     <span data-ttu-id="77722-111">Use o nome de propriedade seguido de igual (`=`) entrar em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="77722-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="77722-112">O exemplo a seguir lê o valor do Visual Basic `Now` property, implicitamente chamando seu `Get` procedimento.</span><span class="sxs-lookup"><span data-stu-id="77722-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="77722-113">Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="77722-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="77722-114">Se não houver nenhum argumento, você pode, opcionalmente, omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="77722-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="77722-115">Coloque os argumentos na lista de argumentos entre parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="77722-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="77722-116">Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="77722-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="77722-117">O valor da propriedade participa na expressão apenas como uma variável ou constante seria, ou ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="77722-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77722-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77722-118">See also</span></span>

- [<span data-ttu-id="77722-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="77722-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="77722-120">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="77722-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="77722-121">Parâmetros e argumentos de procedimento</span><span class="sxs-lookup"><span data-stu-id="77722-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="77722-122">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="77722-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="77722-123">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77722-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="77722-124">Como: criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="77722-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="77722-125">Como: declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="77722-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="77722-126">Como: chamar um procedimento de propriedade</span><span class="sxs-lookup"><span data-stu-id="77722-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="77722-127">Como: Declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77722-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="77722-128">Como: inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="77722-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
