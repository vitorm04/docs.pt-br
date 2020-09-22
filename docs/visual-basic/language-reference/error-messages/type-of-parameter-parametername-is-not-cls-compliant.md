---
title: O tipo de parâmetro '<parametername>' não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: a4617d3550cfb48f32a19a4c70809141173c6147
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875125"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="6a514-102">O tipo de parâmetro '\<parametername>' não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="6a514-102">Type of parameter '\<parametername>' is not CLS-compliant</span></span>

<span data-ttu-id="6a514-103">Um procedimento é marcado como, `<CLSCompliant(True)>` mas declara um parâmetro com um tipo marcado como `<CLSCompliant(False)>` , não está marcado ou não está qualificado porque é um tipo não compatível.</span><span class="sxs-lookup"><span data-stu-id="6a514-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="6a514-104">Para que um procedimento seja compatível com a [independência de linguagem e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos em conformidade com CLS.</span><span class="sxs-lookup"><span data-stu-id="6a514-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="6a514-105">Isso se aplica aos tipos de parâmetros, ao tipo de retorno e aos tipos de todas as suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="6a514-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="6a514-106">Os tipos de dados a seguir Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="6a514-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="6a514-107">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="6a514-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="6a514-108">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="6a514-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="6a514-109">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="6a514-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="6a514-110">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="6a514-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="6a514-111">Quando você aplica o a <xref:System.CLSCompliantAttribute> um elemento de programação, você define o parâmetro do atributo `isCompliant` como `True` ou `False` para indicar conformidade ou não conformidade.</span><span class="sxs-lookup"><span data-stu-id="6a514-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="6a514-112">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="6a514-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="6a514-113">Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, será considerado como não compatível.</span><span class="sxs-lookup"><span data-stu-id="6a514-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="6a514-114">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="6a514-114">By default, this message is a warning.</span></span> <span data-ttu-id="6a514-115">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6a514-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6a514-116">**ID do erro:** BC40028</span><span class="sxs-lookup"><span data-stu-id="6a514-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a514-117">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6a514-117">To correct this error</span></span>  
  
- <span data-ttu-id="6a514-118">Se o procedimento precisar usar um parâmetro desse tipo específico, remova o <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="6a514-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="6a514-119">O procedimento não pode ser compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="6a514-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="6a514-120">Se o procedimento deve ser compatível com CLS, altere o tipo desse parâmetro para o tipo em conformidade com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="6a514-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="6a514-121">Por exemplo, no lugar de `UInteger` você pode ser capaz de usar `Integer` se não precisar do intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="6a514-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="6a514-122">Se você precisar do intervalo estendido, poderá substituir `UInteger` por `Long` .</span><span class="sxs-lookup"><span data-stu-id="6a514-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="6a514-123">Se você estiver fazendo a interface com automação ou objetos COM, tenha em mente que alguns tipos têm larguras de dados diferentes das .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a514-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="6a514-124">Por exemplo, `int` geralmente é 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="6a514-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="6a514-125">Se você estiver aceitando um inteiro de 16 bits desse componente, declare-o como `Short` em vez de `Integer` em seu código de Visual Basic gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6a514-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
