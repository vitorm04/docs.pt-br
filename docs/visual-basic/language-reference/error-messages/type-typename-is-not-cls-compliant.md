---
title: O tipo <typename> não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 243f51b3e6c798c82fdbe7b28557c4f96c728bf2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281717"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="efd47-102">Tipo \<typename > não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="efd47-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="efd47-103">Uma variável, propriedade ou função de retorno é declarada com um tipo de dados que não é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="efd47-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="efd47-104">Para um aplicativo esteja em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="efd47-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="efd47-105">Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="efd47-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="efd47-106">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="efd47-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="efd47-107">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="efd47-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="efd47-108">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="efd47-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="efd47-109">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="efd47-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="efd47-110">**ID do erro:** BC40041</span><span class="sxs-lookup"><span data-stu-id="efd47-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="efd47-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="efd47-111">To correct this error</span></span>  
  
-   <span data-ttu-id="efd47-112">Se seu aplicativo precisa ser compatível com CLS, altere o tipo de dados desse elemento para o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="efd47-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="efd47-113">Por exemplo, no lugar de `UInteger` talvez você possa usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="efd47-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="efd47-114">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="efd47-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="efd47-115">Se seu aplicativo não precisa ser compatível com CLS, você não precisará alterar nada.</span><span class="sxs-lookup"><span data-stu-id="efd47-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="efd47-116">Você deve estar atento a sua falta de conformidade, no entanto.</span><span class="sxs-lookup"><span data-stu-id="efd47-116">You should be aware of its noncompliance, however.</span></span>