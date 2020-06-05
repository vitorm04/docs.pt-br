---
title: O tipo de retorno da função '<procedurename>' não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 9cc7e25ef1be21ff2f6a71dcb61bc29ec92da30f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400351"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="84da4-102">O tipo de retorno da função '\<procedurename>' não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="84da4-102">Return type of function '\<procedurename>' is not CLS-compliant</span></span>
<span data-ttu-id="84da4-103">Um `Function` procedimento é marcado como, `<CLSCompliant(True)>` mas retorna um tipo marcado como `<CLSCompliant(False)>` , não está marcado ou não está qualificado porque é um tipo não compatível.</span><span class="sxs-lookup"><span data-stu-id="84da4-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="84da4-104">Para que um procedimento seja compatível com a [independência de linguagem e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos em conformidade com CLS.</span><span class="sxs-lookup"><span data-stu-id="84da4-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="84da4-105">Isso se aplica aos tipos de parâmetros, ao tipo de retorno e aos tipos de todas as suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="84da4-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="84da4-106">Os tipos de dados a seguir Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="84da4-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="84da4-107">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="84da4-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="84da4-108">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="84da4-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="84da4-109">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="84da4-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="84da4-110">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="84da4-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="84da4-111">Quando você aplica o a <xref:System.CLSCompliantAttribute> um elemento de programação, você define o parâmetro do atributo `isCompliant` como `True` ou `False` para indicar conformidade ou não conformidade.</span><span class="sxs-lookup"><span data-stu-id="84da4-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="84da4-112">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="84da4-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="84da4-113">Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, será considerado como não compatível.</span><span class="sxs-lookup"><span data-stu-id="84da4-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="84da4-114">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="84da4-114">By default, this message is a warning.</span></span> <span data-ttu-id="84da4-115">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="84da4-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="84da4-116">**ID do erro:** BC40027</span><span class="sxs-lookup"><span data-stu-id="84da4-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84da4-117">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="84da4-117">To correct this error</span></span>  
  
- <span data-ttu-id="84da4-118">Se o `Function` procedimento deve retornar esse tipo específico, remova o <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="84da4-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="84da4-119">O procedimento não pode ser compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="84da4-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="84da4-120">Se o `Function` procedimento deve ser compatível com CLS, altere o tipo de retorno para o tipo em conformidade com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="84da4-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="84da4-121">Por exemplo, no lugar de `UInteger` você pode ser capaz de usar `Integer` se não precisar do intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="84da4-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="84da4-122">Se você precisar do intervalo estendido, poderá substituir `UInteger` por `Long` .</span><span class="sxs-lookup"><span data-stu-id="84da4-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="84da4-123">Se você estiver fazendo a interface com automação ou objetos COM, tenha em mente que alguns tipos têm larguras de dados diferentes das .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84da4-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="84da4-124">Por exemplo, `int` geralmente é 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="84da4-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="84da4-125">Se você estiver retornando um inteiro de 16 bits para esse componente, declare-o como `Short` em vez de `Integer` em seu código de Visual Basic gerenciado.</span><span class="sxs-lookup"><span data-stu-id="84da4-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
