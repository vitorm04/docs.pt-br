---
title: 'Como: Inserir um valor em uma propriedade (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: e6aee5ea36c0315d5b01ae2734d17c9e7dab8e93
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341849"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="0eefa-102">Como: Inserir um valor em uma propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0eefa-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="0eefa-103">Você pode armazenar um valor em uma propriedade, colocando o nome da propriedade no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="0eefa-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="0eefa-104">A propriedade `Set` procedimento armazena um valor, mas você não o chame explicitamente por nome.</span><span class="sxs-lookup"><span data-stu-id="0eefa-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="0eefa-105">Você usar a propriedade, assim como você usaria uma variável.</span><span class="sxs-lookup"><span data-stu-id="0eefa-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="0eefa-106">O Visual Basic faz as chamadas para procedimentos da propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eefa-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="0eefa-107">Para armazenar um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="0eefa-107">To store a value in a property</span></span>  
  
1. <span data-ttu-id="0eefa-108">Use o nome da propriedade no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="0eefa-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="0eefa-109">O exemplo a seguir define o valor do Visual Basic `TimeOfDay` propriedade para o meio-dia, implicitamente chamando seu `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="0eefa-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="0eefa-110">Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="0eefa-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0eefa-111">Se não houver nenhum argumento, você pode, opcionalmente, omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="0eefa-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="0eefa-112">Coloque os argumentos na lista de argumentos entre parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="0eefa-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0eefa-113">Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="0eefa-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="0eefa-114">O valor gerado no lado direito da instrução de atribuição é armazenado na propriedade.</span><span class="sxs-lookup"><span data-stu-id="0eefa-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eefa-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0eefa-115">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="0eefa-116">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="0eefa-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0eefa-117">Parâmetros e argumentos de procedimento</span><span class="sxs-lookup"><span data-stu-id="0eefa-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0eefa-118">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="0eefa-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="0eefa-119">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0eefa-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="0eefa-120">Como: criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="0eefa-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="0eefa-121">Como: declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="0eefa-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="0eefa-122">Como: chamar um procedimento de propriedade</span><span class="sxs-lookup"><span data-stu-id="0eefa-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="0eefa-123">Como: Declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0eefa-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="0eefa-124">Como: obter um valor de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="0eefa-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
