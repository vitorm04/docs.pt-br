---
title: "Tipo de &lt;typename&gt; não é compatível com CLS | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
dev_langs:
- VB
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 7
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
ms.openlocfilehash: a8d65568e862c941d5b927582833dff803219bf9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="bb8c1-102">Tipo de &lt;typename&gt; não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="bb8c1-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="bb8c1-103">Uma variável, propriedade ou função de retorno é declarada com um tipo de dados que não é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="bb8c1-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="bb8c1-104">Para um aplicativo ser compatível com o [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), ele deve usar somente tipos compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="bb8c1-104">For an application to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="bb8c1-105">O seguinte [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="bb8c1-105">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="bb8c1-106">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="bb8c1-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="bb8c1-107">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="bb8c1-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="bb8c1-108">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="bb8c1-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="bb8c1-109">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="bb8c1-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="bb8c1-110">**ID do erro:** BC40041</span><span class="sxs-lookup"><span data-stu-id="bb8c1-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb8c1-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bb8c1-111">To correct this error</span></span>  
  
-   <span data-ttu-id="bb8c1-112">Se seu aplicativo precisar ser compatível com CLS, altere o tipo de dados desse elemento para o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="bb8c1-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="bb8c1-113">Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar do intervalo de valor acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="bb8c1-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="bb8c1-114">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="bb8c1-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="bb8c1-115">Se seu aplicativo não precisa ser compatível com CLS, você não precisa alterar nada.</span><span class="sxs-lookup"><span data-stu-id="bb8c1-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="bb8c1-116">Você deve conhecer sua incompatibilidade, no entanto.</span><span class="sxs-lookup"><span data-stu-id="bb8c1-116">You should be aware of its noncompliance, however.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8c1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb8c1-117">See Also</span></span>  
 [<span data-ttu-id="bb8c1-118">\<PAVE em > escrevendo código compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="bb8c1-118">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
