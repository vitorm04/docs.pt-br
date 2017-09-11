---
title: Sobrecarga de procedimento (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- signatures
- Overloads keyword
- hiding by signature
- Visual Basic code, procedures
- procedures, signatures for
- procedures, overloading
- procedures, multiple versions
- parameters, lists
- signatures, procedure
- parameter lists
- Visual Basic code, parameter lists
- Shadows keyword
- procedure overloading
- procedures, parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
caps.latest.revision: 24
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
ms.openlocfilehash: c6972073c983f68cc217e33ac348ad66a089085b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="53175-102">Sobrecarga de procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53175-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="53175-103">*Sobrecarga* significa que um procedimento definindo-a em várias versões, usando o mesmo nome mas listas de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="53175-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="53175-104">O objetivo de sobrecarga é definir várias versões intimamente relacionadas de um procedimento sem diferenciá-los pelo nome.</span><span class="sxs-lookup"><span data-stu-id="53175-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="53175-105">Você pode fazer isso variando a lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="53175-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="53175-106">Sobrecarga de regras</span><span class="sxs-lookup"><span data-stu-id="53175-106">Overloading Rules</span></span>  
 <span data-ttu-id="53175-107">Quando você sobrecarrega um procedimento, as seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="53175-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="53175-108">**Mesmo nome**.</span><span class="sxs-lookup"><span data-stu-id="53175-108">**Same Name**.</span></span> <span data-ttu-id="53175-109">Cada versão sobrecarregada deve usar o mesmo nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="53175-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="53175-110">**Assinatura diferente**.</span><span class="sxs-lookup"><span data-stu-id="53175-110">**Different Signature**.</span></span> <span data-ttu-id="53175-111">Cada versão sobrecarregada deve diferir de todas as outras versões sobrecarregadas em pelo menos um dos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="53175-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="53175-112">Número de parâmetros</span><span class="sxs-lookup"><span data-stu-id="53175-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="53175-113">Ordem dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="53175-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="53175-114">Tipos de dados dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="53175-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="53175-115">Número de parâmetros de tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="53175-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="53175-116">Tipo de retorno (somente para um operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="53175-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="53175-117">Junto com o nome do procedimento, os itens anteriores são coletivamente chamados de *assinatura* do procedimento.</span><span class="sxs-lookup"><span data-stu-id="53175-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="53175-118">Quando você chamar um procedimento sobrecarregado, o compilador usa a assinatura para verificar se a chamada corretamente corresponde a definição.</span><span class="sxs-lookup"><span data-stu-id="53175-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="53175-119">**Itens não faz parte da assinatura**.</span><span class="sxs-lookup"><span data-stu-id="53175-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="53175-120">Você não pode sobrecarregar um procedimento sem variando a assinatura.</span><span class="sxs-lookup"><span data-stu-id="53175-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="53175-121">Em particular, você não pode sobrecarregar um procedimento, variando apenas um ou mais dos seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="53175-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="53175-122">Palavras-chave modificadores de procedimento, como `Public`, `Shared`, e`Static`</span><span class="sxs-lookup"><span data-stu-id="53175-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="53175-123">Nomes de parâmetro de tipo ou parâmetro</span><span class="sxs-lookup"><span data-stu-id="53175-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="53175-124">Restrições de parâmetro de tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="53175-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="53175-125">Palavras-chave modificador de parâmetro, como `ByRef` e`Optional`</span><span class="sxs-lookup"><span data-stu-id="53175-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="53175-126">Se ele retorna um valor</span><span class="sxs-lookup"><span data-stu-id="53175-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="53175-127">O tipo de dados do valor de retorno (exceto para um operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="53175-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="53175-128">Os itens da lista anterior não são parte da assinatura.</span><span class="sxs-lookup"><span data-stu-id="53175-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="53175-129">Embora você não pode usá-las para diferenciar entre versões sobrecarregadas, você pode variá-los entre versões sobrecarregadas corretamente são diferenciadas por suas assinaturas.</span><span class="sxs-lookup"><span data-stu-id="53175-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="53175-130">**Associação tardia argumentos**.</span><span class="sxs-lookup"><span data-stu-id="53175-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="53175-131">Se você pretende passar uma variável de objeto associado a mais de uma versão sobrecarregada, você deve declarar o parâmetro apropriado como <xref:System.Object>.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="53175-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="53175-132">Várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="53175-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="53175-133">Suponha que você esteja escrevendo um `Sub` procedimento para lançar uma transação contra um saldo do cliente e você deseja ser capaz de se referir ao cliente por nome ou por número de conta.</span><span class="sxs-lookup"><span data-stu-id="53175-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="53175-134">Para acomodar isso, você pode definir duas diferentes `Sub` procedimentos, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="53175-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 <span data-ttu-id="53175-135">[!code-vb[VbVbcnProcedures&#73;](./codesnippet/VisualBasic/procedure-overloading_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="53175-135">[!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]</span></span>  
  
### <a name="overloaded-versions"></a><span data-ttu-id="53175-136">Versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="53175-136">Overloaded Versions</span></span>  
 <span data-ttu-id="53175-137">Uma alternativa é sobrecarregar um único nome de procedimento.</span><span class="sxs-lookup"><span data-stu-id="53175-137">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="53175-138">Você pode usar o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave para definir uma versão do procedimento para cada lista de parâmetros, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="53175-138">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 <span data-ttu-id="53175-139">[!code-vb[VbVbcnProcedures&#72;](./codesnippet/VisualBasic/procedure-overloading_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="53175-139">[!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]</span></span>  
  
#### <a name="additional-overloads"></a><span data-ttu-id="53175-140">Sobrecargas adicionais</span><span class="sxs-lookup"><span data-stu-id="53175-140">Additional Overloads</span></span>  
 <span data-ttu-id="53175-141">Se quiser aceitar o valor de uma transação no `Decimal` ou `Single`, você pode sobrecarregar mais `post` para permitir essa variação.</span><span class="sxs-lookup"><span data-stu-id="53175-141">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="53175-142">Se você já fez isso para cada uma das sobrecargas no exemplo anterior, você teria quatro `Sub` procedimentos, todos com o mesmo nome mas com quatro assinaturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="53175-142">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="53175-143">Vantagens da sobrecarga</span><span class="sxs-lookup"><span data-stu-id="53175-143">Advantages of Overloading</span></span>  
 <span data-ttu-id="53175-144">A vantagem de sobrecarregar um procedimento é na flexibilidade da chamada.</span><span class="sxs-lookup"><span data-stu-id="53175-144">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="53175-145">Para usar o `post` procedimento declarado no exemplo anterior, o código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, chamar o mesmo procedimento em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="53175-145">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="53175-146">O exemplo a seguir ilustra isto:</span><span class="sxs-lookup"><span data-stu-id="53175-146">The following example illustrates this:</span></span>  
  
 <span data-ttu-id="53175-147">[!code-vb[56 VbVbcnProcedures](./codesnippet/VisualBasic/procedure-overloading_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="53175-147">[!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]</span></span>  
  
 <span data-ttu-id="53175-148">[!code-vb[VbVbcnProcedures&#57;](./codesnippet/VisualBasic/procedure-overloading_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="53175-148">[!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53175-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53175-149">See Also</span></span>  
 <span data-ttu-id="53175-150">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="53175-150">[Procedures](./index.md) </span></span>  
<span data-ttu-id="53175-151"> [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="53175-151"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="53175-152"> [Como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="53175-152"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="53175-153"> [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="53175-153"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="53175-154"> [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="53175-154"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="53175-155"> [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="53175-155"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="53175-156"> [Resolução de sobrecarga](./overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="53175-156"> [Overload Resolution](./overload-resolution.md) </span></span>  
<span data-ttu-id="53175-157"> [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) </span><span class="sxs-lookup"><span data-stu-id="53175-157"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) </span></span>  
<span data-ttu-id="53175-158"> [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)</span><span class="sxs-lookup"><span data-stu-id="53175-158"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)</span></span>
