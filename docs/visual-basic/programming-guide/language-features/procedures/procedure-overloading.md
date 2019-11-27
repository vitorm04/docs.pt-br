---
title: Sobrecarga de procedimento
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 41a971896fe726cbe9849fd46334910e7288afe0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352593"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="d10fa-102">Sobrecarga de procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d10fa-102">Procedure Overloading (Visual Basic)</span></span>

<span data-ttu-id="d10fa-103">*Sobrecarregar* um procedimento significa defini-lo em várias versões, usando o mesmo nome, mas listas de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="d10fa-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="d10fa-104">A finalidade do sobrecarregamento é definir várias versões de um procedimento bem relacionadas sem precisar diferenciá-las por nome.</span><span class="sxs-lookup"><span data-stu-id="d10fa-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="d10fa-105">Você faz isso variando a lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d10fa-105">You do this by varying the parameter list.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="d10fa-106">Regras de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="d10fa-106">Overloading Rules</span></span>

<span data-ttu-id="d10fa-107">Quando você sobrecarrega um procedimento, as seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="d10fa-107">When you overload a procedure, the following rules apply:</span></span>

- <span data-ttu-id="d10fa-108">**Mesmo nome**.</span><span class="sxs-lookup"><span data-stu-id="d10fa-108">**Same Name**.</span></span> <span data-ttu-id="d10fa-109">Cada versão sobrecarregada deve usar o mesmo nome de procedimento.</span><span class="sxs-lookup"><span data-stu-id="d10fa-109">Each overloaded version must use the same procedure name.</span></span>

- <span data-ttu-id="d10fa-110">**Assinatura diferente**.</span><span class="sxs-lookup"><span data-stu-id="d10fa-110">**Different Signature**.</span></span> <span data-ttu-id="d10fa-111">Cada versão sobrecarregada deve ser diferente de todas as outras versões sobrecarregadas em pelo menos um dos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="d10fa-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>

  - <span data-ttu-id="d10fa-112">Número de parâmetros</span><span class="sxs-lookup"><span data-stu-id="d10fa-112">Number of parameters</span></span>

  - <span data-ttu-id="d10fa-113">Ordem dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="d10fa-113">Order of the parameters</span></span>

  - <span data-ttu-id="d10fa-114">Tipos de dados dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="d10fa-114">Data types of the parameters</span></span>

  - <span data-ttu-id="d10fa-115">Número de parâmetros de tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="d10fa-115">Number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="d10fa-116">Tipo de retorno (somente para um operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="d10fa-116">Return type (only for a conversion operator)</span></span>

  <span data-ttu-id="d10fa-117">Junto com o nome do procedimento, os itens anteriores são chamados coletivamente da *assinatura* do procedimento.</span><span class="sxs-lookup"><span data-stu-id="d10fa-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="d10fa-118">Quando você chama um procedimento sobrecarregado, o compilador usa a assinatura para verificar se a chamada corresponde corretamente à definição.</span><span class="sxs-lookup"><span data-stu-id="d10fa-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>

- <span data-ttu-id="d10fa-119">**Itens que não fazem parte da assinatura**.</span><span class="sxs-lookup"><span data-stu-id="d10fa-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="d10fa-120">Não é possível sobrecarregar um procedimento sem variar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="d10fa-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="d10fa-121">Em particular, você não pode sobrecarregar um procedimento, variando apenas um ou mais dos seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="d10fa-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>

  - <span data-ttu-id="d10fa-122">Palavras-chave do modificador de procedimento, como `Public`, `Shared`e `Static`</span><span class="sxs-lookup"><span data-stu-id="d10fa-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

  - <span data-ttu-id="d10fa-123">Nomes de parâmetro de tipo ou parâmetro</span><span class="sxs-lookup"><span data-stu-id="d10fa-123">Parameter or type parameter names</span></span>

  - <span data-ttu-id="d10fa-124">Restrições de parâmetro de tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="d10fa-124">Type parameter constraints (for a generic procedure)</span></span>

  - <span data-ttu-id="d10fa-125">Palavras-chave do modificador de parâmetro, como `ByRef` e `Optional`</span><span class="sxs-lookup"><span data-stu-id="d10fa-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

  - <span data-ttu-id="d10fa-126">Se ele retorna um valor</span><span class="sxs-lookup"><span data-stu-id="d10fa-126">Whether it returns a value</span></span>

  - <span data-ttu-id="d10fa-127">O tipo de dados do valor de retorno (exceto para um operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="d10fa-127">The data type of the return value (except for a conversion operator)</span></span>

  <span data-ttu-id="d10fa-128">Os itens na lista anterior não fazem parte da assinatura.</span><span class="sxs-lookup"><span data-stu-id="d10fa-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="d10fa-129">Embora não seja possível usá-los para diferenciar as versões sobrecarregadas, você pode variar entre as versões sobrecarregadas que são diferenciadas corretamente por suas assinaturas.</span><span class="sxs-lookup"><span data-stu-id="d10fa-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>

- <span data-ttu-id="d10fa-130">**Argumentos de associação tardia**.</span><span class="sxs-lookup"><span data-stu-id="d10fa-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="d10fa-131">Se você pretende passar uma variável de objeto de associação tardia para uma versão sobrecarregada, você deve declarar o parâmetro apropriado como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d10fa-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>

## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="d10fa-132">Várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="d10fa-132">Multiple Versions of a Procedure</span></span>

<span data-ttu-id="d10fa-133">Suponha que você esteja escrevendo um procedimento de `Sub` para postar uma transação em relação ao saldo de um cliente e desejar consultar o cliente por nome ou por número de conta.</span><span class="sxs-lookup"><span data-stu-id="d10fa-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="d10fa-134">Para acomodar isso, você pode definir dois procedimentos diferentes de `Sub`, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d10fa-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a><span data-ttu-id="d10fa-135">Versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="d10fa-135">Overloaded Versions</span></span>

<span data-ttu-id="d10fa-136">Uma alternativa é sobrecarregar um único nome de procedimento.</span><span class="sxs-lookup"><span data-stu-id="d10fa-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="d10fa-137">Você pode usar a palavra-chave [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) para definir uma versão do procedimento para cada lista de parâmetros, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d10fa-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a><span data-ttu-id="d10fa-138">Sobrecargas adicionais</span><span class="sxs-lookup"><span data-stu-id="d10fa-138">Additional Overloads</span></span>

<span data-ttu-id="d10fa-139">Se você também quisesse aceitar um valor de transação no `Decimal` ou `Single`, poderá sobrecarregar `post` para permitir essa variação.</span><span class="sxs-lookup"><span data-stu-id="d10fa-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="d10fa-140">Se você fez isso para cada uma das sobrecargas no exemplo anterior, teria quatro procedimentos `Sub`, todos com o mesmo nome, mas com quatro assinaturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="d10fa-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>

## <a name="advantages-of-overloading"></a><span data-ttu-id="d10fa-141">Vantagens da sobrecarga</span><span class="sxs-lookup"><span data-stu-id="d10fa-141">Advantages of Overloading</span></span>

<span data-ttu-id="d10fa-142">A vantagem de sobrecarregar um procedimento é a flexibilidade da chamada.</span><span class="sxs-lookup"><span data-stu-id="d10fa-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="d10fa-143">Para usar o procedimento de `post` declarado no exemplo anterior, o código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, chamar o mesmo procedimento em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="d10fa-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="d10fa-144">O exemplo a seguir ilustra isto:</span><span class="sxs-lookup"><span data-stu-id="d10fa-144">The following example illustrates this:</span></span>

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a><span data-ttu-id="d10fa-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d10fa-145">See also</span></span>

- [<span data-ttu-id="d10fa-146">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="d10fa-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d10fa-147">Como definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="d10fa-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="d10fa-148">Como chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="d10fa-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="d10fa-149">Como sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="d10fa-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="d10fa-150">Como sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="d10fa-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="d10fa-151">Considerações sobre Procedimentos de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="d10fa-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="d10fa-152">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="d10fa-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="d10fa-153">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="d10fa-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="d10fa-154">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d10fa-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
