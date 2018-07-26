---
title: Tipo de retorno da função &#39; &lt;procedurename&gt; &#39; não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: b7704ee63031c38f708a2243e84b880c25fcf819
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243775"
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="2accf-102">Tipo de retorno da função &#39; &lt;procedurename&gt; &#39; não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="2accf-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="2accf-103">Um `Function` procedimento está marcado como `<CLSCompliant(True)>` , mas retorna um tipo que está marcado como `<CLSCompliant(False)>`, não está marcada ou não se qualifica porque ele é um tipo incompatível.</span><span class="sxs-lookup"><span data-stu-id="2accf-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="2accf-104">Para obter um procedimento para estar em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="2accf-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="2accf-105">Isso se aplica os tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="2accf-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="2accf-106">Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="2accf-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="2accf-107">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="2accf-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="2accf-108">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="2accf-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="2accf-109">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="2accf-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="2accf-110">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="2accf-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="2accf-111">Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="2accf-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="2accf-112">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="2accf-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="2accf-113">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="2accf-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="2accf-114">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="2accf-114">By default, this message is a warning.</span></span> <span data-ttu-id="2accf-115">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2accf-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2accf-116">**ID do erro:** BC40027</span><span class="sxs-lookup"><span data-stu-id="2accf-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2accf-117">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2accf-117">To correct this error</span></span>  
  
-   <span data-ttu-id="2accf-118">Se o `Function` procedimento deve retornar esse tipo específico, remova o <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2accf-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="2accf-119">O procedimento não pode ser compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="2accf-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="2accf-120">Se o `Function` procedimento deve ser compatível com CLS, altere o tipo de retorno para o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="2accf-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="2accf-121">Por exemplo, no lugar de `UInteger` talvez você possa usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="2accf-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="2accf-122">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="2accf-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="2accf-123">Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2accf-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="2accf-124">Por exemplo, `int` geralmente é 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="2accf-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="2accf-125">Se você estiver retornando um inteiro de 16 bits para tal componente, declare-o como `Short` em vez de `Integer` no seu código gerenciado do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2accf-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>