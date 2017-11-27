---
title: "Tipo de retorno de função &#39; &lt;procedurename&gt;&#39; não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords: BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16670521ec09ae9cab28bf6ca4705c131fd84701
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="5675d-102">Tipo de retorno de função &#39; &lt;procedurename&gt;&#39; não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="5675d-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="5675d-103">Um `Function` procedimento está marcado como `<CLSCompliant(True)>` , mas retorna um tipo que está marcado como `<CLSCompliant(False)>`, não é marcada ou não se qualifica porque ele é um tipo incompatível.</span><span class="sxs-lookup"><span data-stu-id="5675d-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="5675d-104">Para um procedimento para ser compatível com o [independência da linguagem e componentes independentes da linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), ele deve usar somente tipos compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="5675d-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="5675d-105">Isso se aplica a tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="5675d-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="5675d-106">O seguinte [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tipos de dados não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="5675d-106">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="5675d-107">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="5675d-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="5675d-108">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="5675d-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="5675d-109">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="5675d-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="5675d-110">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="5675d-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="5675d-111">Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="5675d-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="5675d-112">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="5675d-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="5675d-113">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="5675d-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="5675d-114">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="5675d-114">By default, this message is a warning.</span></span> <span data-ttu-id="5675d-115">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5675d-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5675d-116">**ID do erro:** BC40027</span><span class="sxs-lookup"><span data-stu-id="5675d-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5675d-117">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5675d-117">To correct this error</span></span>  
  
-   <span data-ttu-id="5675d-118">Se o `Function` procedimento deve retornar esse tipo específico, remova o <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5675d-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="5675d-119">O procedimento não pode ser compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="5675d-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="5675d-120">Se o `Function` procedimento deve ser compatível com CLS, altere o tipo de retorno para o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="5675d-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="5675d-121">Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="5675d-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="5675d-122">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="5675d-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="5675d-123">Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5675d-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="5675d-124">Por exemplo, `int` é geralmente 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="5675d-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="5675d-125">Se você estiver retornando um inteiro de 16 bits para tal componente, declare-o como `Short` em vez de `Integer` em gerenciado [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] código.</span><span class="sxs-lookup"><span data-stu-id="5675d-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5675d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5675d-126">See Also</span></span>  
 [<span data-ttu-id="5675d-127">\<PAVE sobre > escrevendo código compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="5675d-127">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
