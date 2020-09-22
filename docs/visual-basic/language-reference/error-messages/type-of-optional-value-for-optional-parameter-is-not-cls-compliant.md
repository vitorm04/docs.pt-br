---
title: O tipo de valor opcional para o parâmetro opcional <parametername> não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 77d23fff518cb3b0768264ddd07728e3ad6b9f91
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872215"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="7bdec-102">O tipo de valor opcional para o parâmetro opcional \<parametername> não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="7bdec-102">Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>

<span data-ttu-id="7bdec-103">Um procedimento é marcado como `<CLSCompliant(True)>` , mas declara um parâmetro [opcional](../modifiers/optional.md) com o valor padrão de um tipo não compatível.</span><span class="sxs-lookup"><span data-stu-id="7bdec-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="7bdec-104">Para que um procedimento seja compatível com a [independência de linguagem e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos em conformidade com CLS.</span><span class="sxs-lookup"><span data-stu-id="7bdec-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="7bdec-105">Isso se aplica aos tipos de parâmetros, ao tipo de retorno e aos tipos de todas as suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="7bdec-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="7bdec-106">Ele também se aplica aos valores padrão de parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="7bdec-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="7bdec-107">Os tipos de dados a seguir Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="7bdec-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="7bdec-108">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="7bdec-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="7bdec-109">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="7bdec-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="7bdec-110">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="7bdec-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="7bdec-111">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="7bdec-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="7bdec-112">Quando você aplica o <xref:System.CLSCompliantAttribute> atributo a um elemento de programação, você define o parâmetro do atributo `isCompliant` como `True` ou `False` para indicar conformidade ou não conformidade.</span><span class="sxs-lookup"><span data-stu-id="7bdec-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="7bdec-113">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="7bdec-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="7bdec-114">Se você não se aplicar <xref:System.CLSCompliantAttribute> a um elemento, será considerado como não compatível.</span><span class="sxs-lookup"><span data-stu-id="7bdec-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="7bdec-115">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="7bdec-115">By default, this message is a warning.</span></span> <span data-ttu-id="7bdec-116">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7bdec-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="7bdec-117">**ID do erro:** BC40042</span><span class="sxs-lookup"><span data-stu-id="7bdec-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7bdec-118">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7bdec-118">To correct this error</span></span>  
  
- <span data-ttu-id="7bdec-119">Se o parâmetro opcional deve ter um valor padrão desse tipo específico, remova <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="7bdec-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="7bdec-120">O procedimento não pode ser compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="7bdec-120">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="7bdec-121">Se o procedimento deve ser compatível com CLS, altere o tipo desse valor padrão para o tipo em conformidade com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="7bdec-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="7bdec-122">Por exemplo, no lugar de `UInteger` você pode ser capaz de usar `Integer` se não precisar do intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="7bdec-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="7bdec-123">Se você precisar do intervalo estendido, poderá substituir `UInteger` por `Long` .</span><span class="sxs-lookup"><span data-stu-id="7bdec-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="7bdec-124">Se você estiver fazendo a interface com automação ou objetos COM, tenha em mente que alguns tipos têm larguras de dados diferentes das .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7bdec-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="7bdec-125">Por exemplo, `int` geralmente é 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="7bdec-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="7bdec-126">Se você estiver aceitando um inteiro de 16 bits desse componente, declare-o como `Short` em vez de `Integer` em seu código de Visual Basic gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7bdec-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
