---
title: Limitações
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: abe4acd5850aa6065bf4f6fd41bc610ede7ad13f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097950"
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="62f64-102">Limitações do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62f64-102">Visual Basic Limitations</span></span>

<span data-ttu-id="62f64-103">Versões anteriores do Visual Basic limites impostos no código, como o comprimento de nomes de variáveis, o número de variáveis permitidas em módulos e o tamanho do módulo.</span><span class="sxs-lookup"><span data-stu-id="62f64-103">Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="62f64-104">No Visual Basic .NET, essas restrições foram reduzidas, dando a você maior liberdade de escrever e organizar seu código.</span><span class="sxs-lookup"><span data-stu-id="62f64-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="62f64-105">Os limites físicos são dependentes mais da memória em tempo de execução do que nas considerações de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="62f64-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="62f64-106">Se você usar práticas de programação prudentes e dividir aplicativos grandes em várias classes e módulos, haverá uma pequena chance de encontrar uma limitação de Visual Basic interno.</span><span class="sxs-lookup"><span data-stu-id="62f64-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.</span></span>  
  
 <span data-ttu-id="62f64-107">A seguir estão algumas limitações que você pode encontrar em casos extremos:</span><span class="sxs-lookup"><span data-stu-id="62f64-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
- <span data-ttu-id="62f64-108">**Comprimento do nome.**</span><span class="sxs-lookup"><span data-stu-id="62f64-108">**Name Length.**</span></span> <span data-ttu-id="62f64-109">Há um número máximo de caracteres para o nome de cada elemento de programação declarado.</span><span class="sxs-lookup"><span data-stu-id="62f64-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="62f64-110">Esse máximo se aplica a uma cadeia de caracteres de qualificação inteira se o nome do elemento for qualificado.</span><span class="sxs-lookup"><span data-stu-id="62f64-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="62f64-111">Consulte [nomes de elementos declarados](../language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="62f64-111">See [Declared Element Names](../language-features/declared-elements/declared-element-names.md).</span></span>  
  
- <span data-ttu-id="62f64-112">**Comprimento da linha.**</span><span class="sxs-lookup"><span data-stu-id="62f64-112">**Line Length.**</span></span> <span data-ttu-id="62f64-113">Há um máximo de 65535 caracteres em uma linha física de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="62f64-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="62f64-114">A linha de código-fonte lógica pode ser maior se você usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="62f64-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="62f64-115">Consulte [como: quebrar e combinar instruções no código](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="62f64-115">See [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
- <span data-ttu-id="62f64-116">**Dimensões de matriz.**</span><span class="sxs-lookup"><span data-stu-id="62f64-116">**Array Dimensions.**</span></span> <span data-ttu-id="62f64-117">Há um número máximo de dimensões que você pode declarar para uma matriz.</span><span class="sxs-lookup"><span data-stu-id="62f64-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="62f64-118">Isso limita quantos índices você pode usar para especificar um elemento de matriz.</span><span class="sxs-lookup"><span data-stu-id="62f64-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="62f64-119">Consulte [dimensões de matriz em Visual Basic](../language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="62f64-119">See [Array Dimensions in Visual Basic](../language-features/arrays/array-dimensions.md).</span></span>  
  
- <span data-ttu-id="62f64-120">**Comprimento da cadeia de caracteres.**</span><span class="sxs-lookup"><span data-stu-id="62f64-120">**String Length.**</span></span> <span data-ttu-id="62f64-121">Há um número máximo de caracteres Unicode que você pode armazenar em uma única cadeia de caractere.</span><span class="sxs-lookup"><span data-stu-id="62f64-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="62f64-122">Consulte [tipo de dados de cadeia de caracteres](../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="62f64-122">See [String Data Type](../../language-reference/data-types/string-data-type.md).</span></span>  
  
- <span data-ttu-id="62f64-123">**Comprimento da cadeia de caracteres do ambiente.**</span><span class="sxs-lookup"><span data-stu-id="62f64-123">**Environment String Length.**</span></span> <span data-ttu-id="62f64-124">Há um máximo de 32768 caracteres para qualquer cadeia de caracteres de ambiente usada como um argumento de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="62f64-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="62f64-125">Essa é uma limitação em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="62f64-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f64-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="62f64-126">See also</span></span>

- [<span data-ttu-id="62f64-127">Estrutura do programa e convenções de código</span><span class="sxs-lookup"><span data-stu-id="62f64-127">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="62f64-128">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62f64-128">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
