---
title: "Limitações do Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- limits
- limitations, Visual Basic
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
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
ms.openlocfilehash: a3bd551ade2f0c55cd943cfbd353b09dfede4063
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-limitations"></a><span data-ttu-id="f76fd-102">Limitações do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f76fd-102">Visual Basic Limitations</span></span>
<span data-ttu-id="f76fd-103">Versões anteriores do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] imposta limites no código, como o comprimento de nomes de variável, o número de variáveis é permitida em módulos e o tamanho do módulo.</span><span class="sxs-lookup"><span data-stu-id="f76fd-103">Earlier versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="f76fd-104">Em [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], essas restrições foi abrandadas, oferecendo maior liberdade escrever e organizar seu código.</span><span class="sxs-lookup"><span data-stu-id="f76fd-104">In [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="f76fd-105">Limites físicos são dependentes mais memória de tempo de execução que nas considerações de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="f76fd-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="f76fd-106">Se você usa prudentes práticas de programação e divide aplicativos grandes em várias classes e módulos, há pouca probabilidade de encontrar interno [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] limitação.</span><span class="sxs-lookup"><span data-stu-id="f76fd-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] limitation.</span></span>  
  
 <span data-ttu-id="f76fd-107">A seguir estão algumas limitações que podem ser encontrados em casos extremos:</span><span class="sxs-lookup"><span data-stu-id="f76fd-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="f76fd-108">**Comprimento do nome.**</span><span class="sxs-lookup"><span data-stu-id="f76fd-108">**Name Length.**</span></span> <span data-ttu-id="f76fd-109">Há um número máximo de caracteres para o nome de cada elemento de programação declarado.</span><span class="sxs-lookup"><span data-stu-id="f76fd-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="f76fd-110">Esse máximo aplica-se a uma cadeia de caracteres de qualificação inteira se o nome do elemento é qualificado.</span><span class="sxs-lookup"><span data-stu-id="f76fd-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="f76fd-111">Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="f76fd-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="f76fd-112">**Comprimento da linha.**</span><span class="sxs-lookup"><span data-stu-id="f76fd-112">**Line Length.**</span></span> <span data-ttu-id="f76fd-113">Há no máximo 65535 caracteres em uma linha física do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="f76fd-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="f76fd-114">A linha de código fonte lógica pode ser maior se você usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="f76fd-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="f76fd-115">Consulte [como: quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="f76fd-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="f76fd-116">**Dimensões de matriz.**</span><span class="sxs-lookup"><span data-stu-id="f76fd-116">**Array Dimensions.**</span></span> <span data-ttu-id="f76fd-117">Há um número máximo de dimensões, que você pode declarar uma matriz.</span><span class="sxs-lookup"><span data-stu-id="f76fd-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="f76fd-118">Isso limita quantos índices, você pode usar para especificar um elemento de matriz.</span><span class="sxs-lookup"><span data-stu-id="f76fd-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="f76fd-119">Consulte [matriz dimensões no Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="f76fd-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="f76fd-120">**Comprimento da cadeia de caracteres.**</span><span class="sxs-lookup"><span data-stu-id="f76fd-120">**String Length.**</span></span> <span data-ttu-id="f76fd-121">Há um número máximo de caracteres Unicode que você pode armazenar em uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f76fd-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="f76fd-122">Consulte [tipo de dados de cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="f76fd-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="f76fd-123">**Comprimento da cadeia de caracteres de ambiente.**</span><span class="sxs-lookup"><span data-stu-id="f76fd-123">**Environment String Length.**</span></span> <span data-ttu-id="f76fd-124">Há um máximo de 32768 caracteres para qualquer ambiente de cadeia de caracteres usada como um argumento de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f76fd-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="f76fd-125">Esta é uma limitação em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="f76fd-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f76fd-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f76fd-126">See Also</span></span>  
 <span data-ttu-id="f76fd-127">[Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="f76fd-127">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="f76fd-128"> [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span><span class="sxs-lookup"><span data-stu-id="f76fd-128"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span></span>
