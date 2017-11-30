---
title: "Limitações do Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97a2e162b9f1a673fbe805a5d2ef1421cd423a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="b1eb0-102">Limitações do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1eb0-102">Visual Basic Limitations</span></span>
<span data-ttu-id="b1eb0-103">Versões anteriores do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] imposta limites no código, como o comprimento dos nomes de variável, o número de variáveis é permitida em módulos e o tamanho do módulo.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-103">Earlier versions of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="b1eb0-104">No Visual Basic .NET, essas restrições têm foram reduzidas, fornecendo maior liberdade escrever e organizar seu código.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="b1eb0-105">Limites físicos são dependentes mais memória de tempo de execução que sobre considerações de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="b1eb0-106">Se você usa prudentes práticas recomendadas de programação e divide aplicativos grandes em várias classes e módulos, há muito pouca probabilidade de ocorrência interno [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] limitação.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] limitation.</span></span>  
  
 <span data-ttu-id="b1eb0-107">A seguir estão algumas limitações que podem ser encontrados em casos extremos:</span><span class="sxs-lookup"><span data-stu-id="b1eb0-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="b1eb0-108">**Comprimento do nome.**</span><span class="sxs-lookup"><span data-stu-id="b1eb0-108">**Name Length.**</span></span> <span data-ttu-id="b1eb0-109">Há um número máximo de caracteres para o nome de cada elemento de programação declarado.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="b1eb0-110">Esse máximo aplica-se a uma cadeia de caracteres de qualificação inteira se o nome do elemento é qualificado.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="b1eb0-111">Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="b1eb0-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="b1eb0-112">**Comprimento da linha.**</span><span class="sxs-lookup"><span data-stu-id="b1eb0-112">**Line Length.**</span></span> <span data-ttu-id="b1eb0-113">Há um máximo de 65.535 caracteres em uma linha física do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="b1eb0-114">A linha de código fonte lógica pode ser maior se você usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="b1eb0-115">Consulte [como: quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="b1eb0-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="b1eb0-116">**Dimensões de matriz.**</span><span class="sxs-lookup"><span data-stu-id="b1eb0-116">**Array Dimensions.**</span></span> <span data-ttu-id="b1eb0-117">Há um número máximo de dimensões, que você pode declarar uma matriz.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="b1eb0-118">Isso limita quantos índices, você pode usar para especificar um elemento de matriz.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="b1eb0-119">Consulte [matriz dimensões no Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="b1eb0-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="b1eb0-120">**Comprimento da cadeia de caracteres.**</span><span class="sxs-lookup"><span data-stu-id="b1eb0-120">**String Length.**</span></span> <span data-ttu-id="b1eb0-121">Há um número máximo de caracteres Unicode que você pode armazenar em uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="b1eb0-122">Consulte [tipo de dados de cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="b1eb0-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="b1eb0-123">**Comprimento da cadeia de caracteres de ambiente.**</span><span class="sxs-lookup"><span data-stu-id="b1eb0-123">**Environment String Length.**</span></span> <span data-ttu-id="b1eb0-124">Há um máximo de 32768 caracteres para qualquer cadeia de caracteres de ambiente usado como um argumento de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="b1eb0-125">Essa é uma limitação em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="b1eb0-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1eb0-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1eb0-126">See Also</span></span>  
 [<span data-ttu-id="b1eb0-127">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="b1eb0-127">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="b1eb0-128">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1eb0-128">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
