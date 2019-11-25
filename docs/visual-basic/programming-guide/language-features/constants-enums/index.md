---
title: Constantes e enumerações
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants [Visual Basic]
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants [Visual Basic], enumerations
- naming conventions [Visual Basic], constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
ms.openlocfilehash: 858f22df26d44f47848921ee862c1d4c1ca1fc60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353981"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="13047-102">Constantes e enumerações no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13047-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="13047-103">Constantes são uma maneira de usar nomes significativos no lugar de um valor que não é alterado.</span><span class="sxs-lookup"><span data-stu-id="13047-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="13047-104">Constantes armazenam valores que, como o nome implica, permanecem constantes durante a execução de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13047-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="13047-105">Você pode usar constantes para fornecer nomes significativos, em vez de números, tornando o código mais legível.</span><span class="sxs-lookup"><span data-stu-id="13047-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="13047-106">Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante a nomes.</span><span class="sxs-lookup"><span data-stu-id="13047-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="13047-107">Por exemplo, é possível declarar uma enumeração de um conjunto de constantes de inteiros associados aos dias da semana e, em seguida, usar os nomes de dias em vez de seus valores de inteiros em seu código.</span><span class="sxs-lookup"><span data-stu-id="13047-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13047-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="13047-108">In This Section</span></span>  
  
|<span data-ttu-id="13047-109">Termo</span><span class="sxs-lookup"><span data-stu-id="13047-109">Term</span></span>|<span data-ttu-id="13047-110">Definição</span><span class="sxs-lookup"><span data-stu-id="13047-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="13047-111">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="13047-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="13047-112">Os tópicos nesta seção descrevem as constantes e seus usos.</span><span class="sxs-lookup"><span data-stu-id="13047-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="13047-113">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="13047-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="13047-114">Os tópicos nesta seção descrevem as enumerações e seus usos.</span><span class="sxs-lookup"><span data-stu-id="13047-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="13047-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="13047-115">Related Sections</span></span>  
  
|<span data-ttu-id="13047-116">Termo</span><span class="sxs-lookup"><span data-stu-id="13047-116">Term</span></span>|<span data-ttu-id="13047-117">Definição</span><span class="sxs-lookup"><span data-stu-id="13047-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="13047-118">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="13047-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="13047-119">Descreve a instrução `Const`, que é usada para declarar constantes.</span><span class="sxs-lookup"><span data-stu-id="13047-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="13047-120">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="13047-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="13047-121">Descreve a instrução `Enum`, que é usada para criar enumerações.</span><span class="sxs-lookup"><span data-stu-id="13047-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="13047-122">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="13047-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="13047-123">Descreve a instrução `Option Explicit`, que é usada no nível de módulo para forçar a declaração explícita de todas as variáveis nesse módulo.</span><span class="sxs-lookup"><span data-stu-id="13047-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="13047-124">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="13047-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="13047-125">Descreve a instrução `Option Infer`, que permite o uso de inferência de tipo de variável local ao declarar variáveis.</span><span class="sxs-lookup"><span data-stu-id="13047-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="13047-126">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="13047-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="13047-127">Descreve a instrução `Option Strict`, que restringe conversões de tipo de dados implícitas para somente conversões de expansão, não permite associação tardia e não permite digitação implícita que resulta em um tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="13047-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
