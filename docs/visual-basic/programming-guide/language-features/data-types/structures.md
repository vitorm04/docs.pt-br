---
title: Estruturas (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic]
- user-defined data types [Visual Basic], structures
- user-defined types [Visual Basic], about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
ms.openlocfilehash: ebfc82665bb18d96c83db8f29a6c206a9a71fd7f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925780"
---
# <a name="structures-visual-basic"></a><span data-ttu-id="a7fa4-102">Estruturas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7fa4-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="a7fa4-103">Um *estrutura* é uma generalização do que o tipo definido pelo usuário (UDT) compatível com versões anteriores do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of Visual Basic.</span></span> <span data-ttu-id="a7fa4-104">Além dos campos, estruturas podem expor propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="a7fa4-105">Uma estrutura pode implementar uma ou mais interfaces, e você pode declarar os níveis de acesso individual para cada campo.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="a7fa4-106">Você pode combinar itens de dados de diferentes tipos para criar uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="a7fa4-107">Uma estrutura associa um ou mais *elementos* entre si e com a estrutura em si.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="a7fa4-108">Quando você declara uma estrutura, ele se torna uma *tipo de dados composto*, e você pode declarar variáveis desse tipo.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="a7fa4-109">Estruturas são úteis quando você deseja que uma única variável para conter várias partes de informação relacionadas.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="a7fa4-110">Por exemplo, você talvez queira manter o nome, extensão de telefone e salário do funcionário.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="a7fa4-111">Você pode usar diversas variáveis para obter essas informações, ou você poderia definir uma estrutura e usá-lo para uma única variável funcionário.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="a7fa4-112">A vantagem da estrutura se torna aparente quando você tem muitos funcionários e, portanto, muitas instâncias da variável.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7fa4-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a7fa4-113">In This Section</span></span>  
 [<span data-ttu-id="a7fa4-114">Como declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="a7fa4-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="a7fa4-115">Mostra como declarar uma estrutura e seus elementos.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="a7fa4-116">Variáveis de Estrutura</span><span class="sxs-lookup"><span data-stu-id="a7fa4-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="a7fa4-117">Bastidores atribuir uma estrutura para uma variável e acessar seus elementos.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="a7fa4-118">Estruturas e Outros Elementos de Programação</span><span class="sxs-lookup"><span data-stu-id="a7fa4-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="a7fa4-119">Resume como estruturas interagem com matrizes, objetos, procedimentos e uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="a7fa4-120">Estruturas e Classes</span><span class="sxs-lookup"><span data-stu-id="a7fa4-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="a7fa4-121">Descreve as semelhanças e diferenças entre as estruturas e classes.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a7fa4-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a7fa4-122">Related Sections</span></span>  
 [<span data-ttu-id="a7fa4-123">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="a7fa4-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="a7fa4-124">Apresenta os tipos de dados do Visual Basic e descreve como usá-los.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-124">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="a7fa4-125">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="a7fa4-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="a7fa4-126">Lista os tipos de dados elementares fornecidos pelo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-126">Lists the elementary data types supplied by Visual Basic.</span></span>
