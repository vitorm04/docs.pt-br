---
title: O tipo de valor opcional para o parâmetro opcional <parametername> não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: ee7d208f7a579f81690ffbda265bde29316e4ec3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664298"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="0bde9-102">Tipo de valor opcional para o parâmetro opcional \<parametername > não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="0bde9-102">Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>
<span data-ttu-id="0bde9-103">Um procedimento é marcado como `<CLSCompliant(True)>` mas declara um [opcional](../../../visual-basic/language-reference/modifiers/optional.md) parâmetro com valor de padrão de um tipo incompatível.</span><span class="sxs-lookup"><span data-stu-id="0bde9-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="0bde9-104">Para obter um procedimento para estar em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="0bde9-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="0bde9-105">Isso se aplica os tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="0bde9-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="0bde9-106">Ele também se aplica aos valores padrão de parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="0bde9-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="0bde9-107">Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="0bde9-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="0bde9-108">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="0bde9-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="0bde9-109">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="0bde9-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="0bde9-110">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="0bde9-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="0bde9-111">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="0bde9-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="0bde9-112">Quando você aplica a <xref:System.CLSCompliantAttribute> atributo a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="0bde9-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0bde9-113">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="0bde9-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="0bde9-114">Se você não aplicar <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="0bde9-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="0bde9-115">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="0bde9-115">By default, this message is a warning.</span></span> <span data-ttu-id="0bde9-116">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0bde9-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0bde9-117">**ID do erro:** BC40042</span><span class="sxs-lookup"><span data-stu-id="0bde9-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0bde9-118">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0bde9-118">To correct this error</span></span>  
  
- <span data-ttu-id="0bde9-119">Se o parâmetro opcional deve ter um valor padrão desse tipo específico, remova <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0bde9-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="0bde9-120">O procedimento não pode ser compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="0bde9-120">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="0bde9-121">Se o procedimento deve ser compatível com CLS, altere o tipo de valor padrão para o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="0bde9-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="0bde9-122">Por exemplo, no lugar de `UInteger` talvez você possa usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="0bde9-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="0bde9-123">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="0bde9-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="0bde9-124">Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0bde9-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="0bde9-125">Por exemplo, `int` geralmente é 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="0bde9-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="0bde9-126">Se você estiver retornando um inteiro de 16 bits de tal componente, declare-o como `Short` em vez de `Integer` no seu código gerenciado do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0bde9-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>