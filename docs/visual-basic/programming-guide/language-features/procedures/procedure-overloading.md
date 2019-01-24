---
title: Sobrecarga de procedimento (Visual Basic)
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
ms.openlocfilehash: 3cb11079241da4815c6e7bde4a76123965a95514
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712516"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="92393-102">Sobrecarga de procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92393-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="92393-103">*Sobrecarregando* significa que um procedimento definindo-a em várias versões, usando o mesmo nome mas listas de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="92393-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="92393-104">O objetivo de sobrecarga é definir várias versões intimamente relacionadas de um procedimento sem a necessidade para diferenciá-los por nome.</span><span class="sxs-lookup"><span data-stu-id="92393-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="92393-105">Para fazer isso, variando de lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="92393-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="92393-106">Sobrecarga de regras</span><span class="sxs-lookup"><span data-stu-id="92393-106">Overloading Rules</span></span>  
 <span data-ttu-id="92393-107">Ao sobrecarregar um procedimento, as seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="92393-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="92393-108">**Mesmo nome**.</span><span class="sxs-lookup"><span data-stu-id="92393-108">**Same Name**.</span></span> <span data-ttu-id="92393-109">Cada versão sobrecarregada deve usar o mesmo nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="92393-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="92393-110">**Assinatura diferente**.</span><span class="sxs-lookup"><span data-stu-id="92393-110">**Different Signature**.</span></span> <span data-ttu-id="92393-111">Cada versão sobrecarregada deve diferir de todas as outras versões sobrecarregadas em pelo menos um dos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="92393-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="92393-112">Número de parâmetros</span><span class="sxs-lookup"><span data-stu-id="92393-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="92393-113">Ordem dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="92393-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="92393-114">Tipos de dados dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="92393-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="92393-115">Número de parâmetros de tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="92393-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="92393-116">Tipo de retorno (somente para um operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="92393-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="92393-117">Junto com o nome do procedimento, os itens anteriores são coletivamente chamados de *assinatura* do procedimento.</span><span class="sxs-lookup"><span data-stu-id="92393-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="92393-118">Quando você chama um procedimento sobrecarregado, o compilador usa a assinatura para verificar se a chamada corretamente corresponde a definição.</span><span class="sxs-lookup"><span data-stu-id="92393-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="92393-119">**Itens não faz parte da assinatura**.</span><span class="sxs-lookup"><span data-stu-id="92393-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="92393-120">Você não pode sobrecarregar um procedimento sem variando a assinatura.</span><span class="sxs-lookup"><span data-stu-id="92393-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="92393-121">Em particular, você não pode sobrecarregar um procedimento, variando apenas um ou mais dos seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="92393-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="92393-122">Palavras-chave com o modificador de procedimento, como `Public`, `Shared`, e `Static`</span><span class="sxs-lookup"><span data-stu-id="92393-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="92393-123">Nomes de parâmetro de tipo ou parâmetro</span><span class="sxs-lookup"><span data-stu-id="92393-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="92393-124">Restrições de parâmetro de tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="92393-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="92393-125">Palavras-chave com o modificador de parâmetro, como `ByRef` e `Optional`</span><span class="sxs-lookup"><span data-stu-id="92393-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="92393-126">Se ele retorna um valor</span><span class="sxs-lookup"><span data-stu-id="92393-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="92393-127">o tipo de dados do valor de retorno (exceto para um operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="92393-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="92393-128">Os itens na lista anterior não são parte da assinatura.</span><span class="sxs-lookup"><span data-stu-id="92393-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="92393-129">Embora você não pode usá-las para diferenciar entre as versões sobrecarregadas, você pode variá-los entre as versões sobrecarregadas que adequadamente são diferenciadas por suas assinaturas.</span><span class="sxs-lookup"><span data-stu-id="92393-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="92393-130">**Associação tardia argumentos**.</span><span class="sxs-lookup"><span data-stu-id="92393-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="92393-131">Se você pretende passar uma variável de objeto associado tardia para uma versão sobrecarregada, você deve declarar o parâmetro apropriado como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="92393-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="92393-132">Várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="92393-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="92393-133">Suponha que você está escrevendo um `Sub` procedimento para lançar uma transação contra um saldo do cliente e você deseja ser capaz de se referir ao cliente por nome ou por número de conta.</span><span class="sxs-lookup"><span data-stu-id="92393-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="92393-134">Para acomodar isso, você pode definir duas diferentes `Sub` procedimentos, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="92393-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a><span data-ttu-id="92393-135">Versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="92393-135">Overloaded Versions</span></span>  
 <span data-ttu-id="92393-136">Uma alternativa é sobrecarregar um único nome de procedimento.</span><span class="sxs-lookup"><span data-stu-id="92393-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="92393-137">Você pode usar o [sobrecarrega](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave para definir uma versão do procedimento para cada lista de parâmetros, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="92393-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a><span data-ttu-id="92393-138">Sobrecargas adicionais</span><span class="sxs-lookup"><span data-stu-id="92393-138">Additional Overloads</span></span>  
 <span data-ttu-id="92393-139">Se você quiser aceitar o valor de uma transação em um `Decimal` ou `Single`, você pode sobrecarregar ainda mais `post` para permitir essa variação.</span><span class="sxs-lookup"><span data-stu-id="92393-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="92393-140">Se você já fez isso para cada uma das sobrecargas no exemplo anterior, você teria que quatro `Sub` procedimentos, tudo isso com o mesmo nome mas com quatro assinaturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="92393-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="92393-141">Vantagens da sobrecarga</span><span class="sxs-lookup"><span data-stu-id="92393-141">Advantages of Overloading</span></span>  
 <span data-ttu-id="92393-142">A vantagem de sobrecarregar um procedimento é a flexibilidade da chamada.</span><span class="sxs-lookup"><span data-stu-id="92393-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="92393-143">Para usar o `post` procedimento declarada no exemplo anterior, o código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, chamar o mesmo procedimento em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="92393-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="92393-144">O exemplo a seguir ilustra isto:</span><span class="sxs-lookup"><span data-stu-id="92393-144">The following example illustrates this:</span></span>  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="92393-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92393-145">See also</span></span>
- [<span data-ttu-id="92393-146">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="92393-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="92393-147">Como: Definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="92393-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="92393-148">Como: Chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="92393-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="92393-149">Como: Sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="92393-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="92393-150">Como: Sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="92393-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="92393-151">Considerações sobre Procedimentos de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="92393-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="92393-152">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="92393-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="92393-153">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="92393-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="92393-154">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92393-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
