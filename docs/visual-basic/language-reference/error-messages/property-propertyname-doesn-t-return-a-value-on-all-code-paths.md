---
title: A propriedade '<propertyname>' não retorna um valor em todos os caminhos de código
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 1788d06aa5236d4cfc33999df86ad72c420b41df
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268997"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="d501e-102">Propriedade '\<propertyname >' não retorna um valor em todos os caminhos de código</span><span class="sxs-lookup"><span data-stu-id="d501e-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="d501e-103">Propriedade '\<propertyname >' não retorna um valor em todos os caminhos de código.</span><span class="sxs-lookup"><span data-stu-id="d501e-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="d501e-104">Uma exceção de referência nula pode ocorrer em tempo de execução quando o resultado é usado.</span><span class="sxs-lookup"><span data-stu-id="d501e-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="d501e-105">Uma propriedade `Get` procedimento tem pelo menos um caminho possível pelo seu código que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="d501e-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="d501e-106">Você pode retornar um valor de uma propriedade `Get` procedimento em qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="d501e-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="d501e-107">Atribua o valor para o nome da propriedade e, em seguida, executar um `Exit Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="d501e-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="d501e-108">Atribua o valor para o nome da propriedade e, em seguida, execute o `End Get` instrução.</span><span class="sxs-lookup"><span data-stu-id="d501e-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="d501e-109">Incluir o valor em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d501e-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="d501e-110">Se o controle passa para `Exit Property` ou `End Get` e você não tiver atribuído qualquer valor para o nome da propriedade, o `Get` procedimento retorna o valor padrão da propriedade tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d501e-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="d501e-111">Para obter mais informações, consulte "Comportamento" em [instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d501e-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="d501e-112">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="d501e-112">By default, this message is a warning.</span></span> <span data-ttu-id="d501e-113">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d501e-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d501e-114">**ID do erro:** BC42107</span><span class="sxs-lookup"><span data-stu-id="d501e-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d501e-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d501e-115">To correct this error</span></span>  
  
-   <span data-ttu-id="d501e-116">Verifique sua lógica de fluxo de controle e verifique se que você atribuir um valor antes de cada instrução que faz com que um retorno.</span><span class="sxs-lookup"><span data-stu-id="d501e-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="d501e-117">É mais fácil garantir que cada retorno do procedimento retorna um valor se você usar sempre o `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="d501e-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="d501e-118">Se você fizer isso, a última instrução antes `End Get` deve ser um `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="d501e-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d501e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d501e-119">See also</span></span>
- [<span data-ttu-id="d501e-120">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="d501e-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="d501e-121">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="d501e-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="d501e-122">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="d501e-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
