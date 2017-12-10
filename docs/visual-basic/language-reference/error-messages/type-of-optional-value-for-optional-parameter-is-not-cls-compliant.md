---
title: "Tipo de valor opcional para parâmetro opcional &lt;parametername&gt; não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords: BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72ec027c397be2a57be5c22b55f6dcce9a5c5f5a
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a><span data-ttu-id="ad301-102">Tipo de valor opcional para parâmetro opcional &lt;parametername&gt; não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="ad301-102">Type of optional value for optional parameter &lt;parametername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="ad301-103">Um procedimento está marcado como `<CLSCompliant(True)>` mas declara um [opcional](../../../visual-basic/language-reference/modifiers/optional.md) parâmetro com valor padrão de um tipo incompatível.</span><span class="sxs-lookup"><span data-stu-id="ad301-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="ad301-104">Para um procedimento para ser compatível com o [independência da linguagem e componentes independentes da linguagem](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="ad301-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="ad301-105">Isso se aplica a tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="ad301-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="ad301-106">Ela também se aplica aos valores padrão de parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="ad301-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="ad301-107">O seguinte [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tipos de dados não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="ad301-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="ad301-108">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="ad301-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="ad301-109">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="ad301-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="ad301-110">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="ad301-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="ad301-111">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="ad301-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="ad301-112">Quando você aplica o <xref:System.CLSCompliantAttribute> atributo a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="ad301-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="ad301-113">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="ad301-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="ad301-114">Se você não aplicar <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="ad301-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="ad301-115">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="ad301-115">By default, this message is a warning.</span></span> <span data-ttu-id="ad301-116">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ad301-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="ad301-117">**ID do erro:** BC40042</span><span class="sxs-lookup"><span data-stu-id="ad301-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ad301-118">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ad301-118">To correct this error</span></span>  
  
-   <span data-ttu-id="ad301-119">Se o parâmetro opcional deve ter um valor padrão desse tipo específico, remova <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ad301-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="ad301-120">O procedimento não pode ser compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="ad301-120">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="ad301-121">Se o procedimento deve ser compatível com CLS, altere o tipo de valor padrão para o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="ad301-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="ad301-122">Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="ad301-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="ad301-123">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="ad301-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="ad301-124">Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad301-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="ad301-125">Por exemplo, `int` é geralmente 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="ad301-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="ad301-126">Se você estiver retornando um inteiro de 16 bits de um componente, declare-o como `Short` em vez de `Integer` em gerenciado [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] código.</span><span class="sxs-lookup"><span data-stu-id="ad301-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad301-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad301-127">See Also</span></span>  
 [<span data-ttu-id="ad301-128">\<PAVE sobre > escrevendo código compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="ad301-128">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
