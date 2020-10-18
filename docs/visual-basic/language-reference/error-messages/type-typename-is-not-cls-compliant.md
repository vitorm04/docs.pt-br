---
title: O tipo <typename> não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: c50e721e9170a402724a11f3aab573c7e8abf4c1
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161160"
---
# <a name="bc40041-type-typename-is-not-cls-compliant"></a><span data-ttu-id="401f8-102">BC40041: tipo \<typename> não tem conformidade com CLS</span><span class="sxs-lookup"><span data-stu-id="401f8-102">BC40041: Type \<typename> is not CLS-compliant</span></span>

<span data-ttu-id="401f8-103">Uma variável, propriedade ou retorno de função é declarada com um tipo de dados que não tem conformidade com CLS.</span><span class="sxs-lookup"><span data-stu-id="401f8-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>

 <span data-ttu-id="401f8-104">Para que um aplicativo seja compatível com a [independência de idioma e](../../../standard/language-independence-and-language-independent-components.md) com os componentes de Language-Independent (CLS), ele deve usar somente tipos em conformidade com CLS.</span><span class="sxs-lookup"><span data-stu-id="401f8-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>

 <span data-ttu-id="401f8-105">Os tipos de dados a seguir Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="401f8-105">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="401f8-106">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="401f8-106">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="401f8-107">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="401f8-107">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="401f8-108">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="401f8-108">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="401f8-109">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="401f8-109">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="401f8-110">**ID do erro:** BC40041</span><span class="sxs-lookup"><span data-stu-id="401f8-110">**Error ID:** BC40041</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="401f8-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="401f8-111">To correct this error</span></span>

- <span data-ttu-id="401f8-112">Se seu aplicativo precisar ser compatível com CLS, altere o tipo de dados desse elemento para o tipo mais próximo em conformidade com CLS.</span><span class="sxs-lookup"><span data-stu-id="401f8-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="401f8-113">Por exemplo, no lugar de `UInteger` você pode ser capaz de usar `Integer` se não precisar do intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="401f8-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="401f8-114">Se você precisar do intervalo estendido, poderá substituir `UInteger` por `Long` .</span><span class="sxs-lookup"><span data-stu-id="401f8-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="401f8-115">Se seu aplicativo não precisar ser compatível com CLS, você não precisará alterar nada.</span><span class="sxs-lookup"><span data-stu-id="401f8-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="401f8-116">No entanto, você deve estar ciente de sua não conformidade.</span><span class="sxs-lookup"><span data-stu-id="401f8-116">You should be aware of its noncompliance, however.</span></span>
