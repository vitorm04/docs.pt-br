---
title: Tipo de parâmetro &#39; &lt;parametername&gt; &#39; não é compatível com CLS
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d34de9e5914b02a0e878b87e786b81a5940a6d85
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a><span data-ttu-id="a0c1a-102">Tipo de parâmetro &#39; &lt;parametername&gt; &#39; não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="a0c1a-102">Type of parameter &#39;&lt;parametername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="a0c1a-103">Um procedimento está marcado como `<CLSCompliant(True)>` mas declara um parâmetro com um tipo que está marcado como `<CLSCompliant(False)>`, não é marcada ou não se qualifica porque ele é um tipo incompatível.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="a0c1a-104">Para um procedimento para ser compatível com o [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="a0c1a-105">Isso se aplica a tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="a0c1a-106">Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="a0c1a-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="a0c1a-107">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="a0c1a-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="a0c1a-108">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="a0c1a-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="a0c1a-109">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="a0c1a-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="a0c1a-110">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="a0c1a-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="a0c1a-111">Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="a0c1a-112">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="a0c1a-113">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="a0c1a-114">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-114">By default, this message is a warning.</span></span> <span data-ttu-id="a0c1a-115">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a0c1a-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a0c1a-116">**ID do erro:** BC40028</span><span class="sxs-lookup"><span data-stu-id="a0c1a-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0c1a-117">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a0c1a-117">To correct this error</span></span>  
  
-   <span data-ttu-id="a0c1a-118">Se o procedimento deve ter um parâmetro deste tipo específico, remova o <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="a0c1a-119">O procedimento não pode ser compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="a0c1a-120">Se o procedimento deve ser compatível com CLS, altere o tipo do parâmetro para o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="a0c1a-121">Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="a0c1a-122">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="a0c1a-123">Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0c1a-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="a0c1a-124">Por exemplo, `int` é geralmente 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="a0c1a-125">Se você estiver retornando um inteiro de 16 bits de um componente, declare-o como `Short` em vez de `Integer` no seu código Visual Basic gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a0c1a-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>