---
title: Tipo &lt;typename&gt; não é compatível com CLS
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73abc8b055e7eb9d1a4f6917d816cab5b4509f86
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="5777b-102">Tipo &lt;typename&gt; não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="5777b-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="5777b-103">Uma variável, propriedade ou função de retorno é declarada com um tipo de dados que não é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="5777b-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="5777b-104">Para um aplicativo ser compatível com o [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="5777b-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="5777b-105">Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="5777b-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="5777b-106">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="5777b-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="5777b-107">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="5777b-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="5777b-108">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="5777b-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="5777b-109">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="5777b-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="5777b-110">**ID do erro:** BC40041</span><span class="sxs-lookup"><span data-stu-id="5777b-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5777b-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5777b-111">To correct this error</span></span>  
  
-   <span data-ttu-id="5777b-112">Se seu aplicativo precisa para ser compatível com CLS, altere o tipo de dados desse elemento para o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="5777b-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="5777b-113">Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="5777b-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="5777b-114">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="5777b-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="5777b-115">Se seu aplicativo não precisa ser compatível com CLS, você não precisa alterar nada.</span><span class="sxs-lookup"><span data-stu-id="5777b-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="5777b-116">Você deve conhecer sua incompatibilidade, no entanto.</span><span class="sxs-lookup"><span data-stu-id="5777b-116">You should be aware of its noncompliance, however.</span></span>