---
title: A propriedade '<propertyname>' não retorna um valor em todos os caminhos de código
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 0736e2cbcdea1422d40161c88f898d487f72e3bc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162382"
---
# <a name="bc42107-property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="72e4f-102">BC42107: a propriedade ' \<propertyname> ' não retorna um valor em todos os caminhos de código</span><span class="sxs-lookup"><span data-stu-id="72e4f-102">BC42107: Property '\<propertyname>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="72e4f-103">A propriedade ' \<propertyname> ' não retorna um valor em todos os caminhos de código.</span><span class="sxs-lookup"><span data-stu-id="72e4f-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="72e4f-104">Uma exceção de referência nula pode ocorrer em tempo de execução quando o resultado é usado.</span><span class="sxs-lookup"><span data-stu-id="72e4f-104">A null reference exception could occur at run time when the result is used.</span></span>

<span data-ttu-id="72e4f-105">Um procedimento de propriedade `Get` tem pelo menos um caminho possível por meio de seu código que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="72e4f-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="72e4f-106">Você pode retornar um valor de um procedimento de propriedade de `Get` qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="72e4f-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>

- <span data-ttu-id="72e4f-107">Atribua o valor ao nome da propriedade e, em seguida, execute uma `Exit Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="72e4f-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>

- <span data-ttu-id="72e4f-108">Atribua o valor ao nome da propriedade e, em seguida, execute a `End Get` instrução.</span><span class="sxs-lookup"><span data-stu-id="72e4f-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>

- <span data-ttu-id="72e4f-109">Inclua o valor em uma [instrução return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="72e4f-109">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

<span data-ttu-id="72e4f-110">Se o controle passar para `Exit Property` ou `End Get` e você não tiver atribuído nenhum valor ao nome da propriedade, o `Get` procedimento retornará o valor padrão do tipo de dados da propriedade.</span><span class="sxs-lookup"><span data-stu-id="72e4f-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="72e4f-111">Para obter mais informações, consulte "Behavior" na [instrução function](../statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="72e4f-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

<span data-ttu-id="72e4f-112">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="72e4f-112">By default, this message is a warning.</span></span> <span data-ttu-id="72e4f-113">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="72e4f-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="72e4f-114">**ID do erro:** BC42107</span><span class="sxs-lookup"><span data-stu-id="72e4f-114">**Error ID:** BC42107</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="72e4f-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="72e4f-115">To correct this error</span></span>

- <span data-ttu-id="72e4f-116">Verifique sua lógica de fluxo de controle e certifique-se de atribuir um valor antes de cada instrução que causa um retorno.</span><span class="sxs-lookup"><span data-stu-id="72e4f-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

  <span data-ttu-id="72e4f-117">É mais fácil garantir que cada retorno do procedimento retorne um valor se você sempre usar a `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="72e4f-117">It's easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="72e4f-118">Se você fizer isso, a última instrução antes `End Get` deve ser uma `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="72e4f-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="72e4f-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="72e4f-119">See also</span></span>

- [<span data-ttu-id="72e4f-120">Procedimentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="72e4f-120">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="72e4f-121">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="72e4f-121">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="72e4f-122">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="72e4f-122">Get Statement</span></span>](../statements/get-statement.md)
