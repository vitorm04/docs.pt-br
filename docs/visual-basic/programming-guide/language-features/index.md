---
title: Funcionalidades da linguagem do Visual Basic
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
- Visual Basic code, elements of
- Visual Basic code
ms.assetid: b0b21730-298c-47e6-9a2f-cc81f628067b
caps.latest.revision: 18
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3594e6622e8bc76839a15739a31ad27d17de8455
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="visual-basic-language-features"></a><span data-ttu-id="13b3e-102">Funcionalidades da linguagem do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13b3e-102">Visual Basic Language Features</span></span>
<span data-ttu-id="13b3e-103">Os tópicos a seguir apresentam e discutem os componentes essenciais do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], uma linguagem de programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="13b3e-103">The following topics introduce and discuss the essential components of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], an object-oriented programming language.</span></span> <span data-ttu-id="13b3e-104">Depois de criar a interface do usuário para o seu aplicativo usando formulários e controles, você precisa escrever o código que define o comportamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13b3e-104">After creating the user interface for your application using forms and controls, you need to write the code that defines the application's behavior.</span></span> <span data-ttu-id="13b3e-105">Como acontece com qualquer linguagem de programação moderna, o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dá suporte a muitos constructos de programação e elementos de linguagem comuns.</span><span class="sxs-lookup"><span data-stu-id="13b3e-105">As with any modern programming language, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supports a number of common programming constructs and language elements.</span></span>  
  
 <span data-ttu-id="13b3e-106">Se você já programou em outras linguagens, grande parte do material abordado nesta seção poderá parecer familiar.</span><span class="sxs-lookup"><span data-stu-id="13b3e-106">If you have programmed in other languages, much of the material covered in this section might seem familiar.</span></span> <span data-ttu-id="13b3e-107">Embora a maioria dos constructos seja semelhante a de outras linguagens, a natureza orientada a eventos do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] apresenta algumas diferenças sutis.</span><span class="sxs-lookup"><span data-stu-id="13b3e-107">While most of the constructs are similar to those in other languages, the event-driven nature of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] introduces some subtle differences.</span></span>  
  
 <span data-ttu-id="13b3e-108">Se você for novo em programação, o material desta seção servirá como uma introdução aos blocos de compilação básicos para escrever código.</span><span class="sxs-lookup"><span data-stu-id="13b3e-108">If you are new to programming, the material in this section serves as an introduction to the basic building blocks for writing code.</span></span> <span data-ttu-id="13b3e-109">Depois de compreender os conceitos básicos, você pode criar aplicativos avançados usando [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="13b3e-109">Once you understand the basics, you can create powerful applications using [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13b3e-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="13b3e-110">In This Section</span></span>  
 [<span data-ttu-id="13b3e-111">Matrizes</span><span class="sxs-lookup"><span data-stu-id="13b3e-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 <span data-ttu-id="13b3e-112">Discute como tornar seu código mais eficiente e compacto declarando e usando matrizes, que contêm vários valores relacionados.</span><span class="sxs-lookup"><span data-stu-id="13b3e-112">Discusses making your code more compact and powerful by declaring and using arrays, which hold multiple related values.</span></span>  
  
 [<span data-ttu-id="13b3e-113">Inicializadores de Coleção</span><span class="sxs-lookup"><span data-stu-id="13b3e-113">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 <span data-ttu-id="13b3e-114">Descreve os inicializadores de coleção, que permitem que você crie e preencha uma coleção com um conjunto inicial de valores.</span><span class="sxs-lookup"><span data-stu-id="13b3e-114">Describes collection initializers, which enable you to create a collection and populate it with an initial set of values.</span></span>  
  
 [<span data-ttu-id="13b3e-115">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="13b3e-115">Constants and Enumerations</span></span>](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 <span data-ttu-id="13b3e-116">Discute o armazenamento de valores sem variação para uso repetido, inclusive conjuntos de valores constantes relacionados.</span><span class="sxs-lookup"><span data-stu-id="13b3e-116">Discusses storing unchanging values for repeated use, including sets of related constant values.</span></span>  
  
 [<span data-ttu-id="13b3e-117">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="13b3e-117">Control Flow</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 <span data-ttu-id="13b3e-118">Mostra como regular o fluxo de execução do programa.</span><span class="sxs-lookup"><span data-stu-id="13b3e-118">Shows how to regulate the flow of your program's execution.</span></span>  
  
 [<span data-ttu-id="13b3e-119">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="13b3e-119">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="13b3e-120">Descreve quais tipos de dados um elemento de programação pode armazenar e como esses dados são armazenados.</span><span class="sxs-lookup"><span data-stu-id="13b3e-120">Describes what kinds of data a programming element can hold and how that data is stored.</span></span>  
  
 [<span data-ttu-id="13b3e-121">Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="13b3e-121">Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 <span data-ttu-id="13b3e-122">Aborda a programação de elementos que você pode declarar, seus nomes e características e como o compilador resolve referências para eles.</span><span class="sxs-lookup"><span data-stu-id="13b3e-122">Covers programming elements you can declare, their names and characteristics, and how the compiler resolves references to them.</span></span>  
  
 [<span data-ttu-id="13b3e-123">Delegados</span><span class="sxs-lookup"><span data-stu-id="13b3e-123">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 <span data-ttu-id="13b3e-124">Fornece uma introdução aos delegados e como eles são usados no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13b3e-124">Provides an introduction to delegates and how they are used in Visual Basic.</span></span>  
  
 [<span data-ttu-id="13b3e-125">Associação Antecipada e Tardia</span><span class="sxs-lookup"><span data-stu-id="13b3e-125">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 <span data-ttu-id="13b3e-126">Descreve a vinculação, que é executada pelo compilador quando um objeto é atribuído a uma variável de objeto e as diferenças entre objetos com associação inicial e tardia.</span><span class="sxs-lookup"><span data-stu-id="13b3e-126">Describes binding, which is performed by the compiler when an object is assigned to an object variable, and the differences between early-bound and late-bound objects.</span></span>  
  
 [<span data-ttu-id="13b3e-127">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="13b3e-127">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 <span data-ttu-id="13b3e-128">Fornece uma visão geral dos erros de sintaxe, erros de tempo de execução e erros lógicos.</span><span class="sxs-lookup"><span data-stu-id="13b3e-128">Provides an overview of syntax errors, run-time errors, and logic errors.</span></span>  
  
 [<span data-ttu-id="13b3e-129">Eventos</span><span class="sxs-lookup"><span data-stu-id="13b3e-129">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)  
 <span data-ttu-id="13b3e-130">Mostra como declarar e usar eventos.</span><span class="sxs-lookup"><span data-stu-id="13b3e-130">Shows how to declare and use events.</span></span>  
  
 [<span data-ttu-id="13b3e-131">Interfaces</span><span class="sxs-lookup"><span data-stu-id="13b3e-131">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 <span data-ttu-id="13b3e-132">Descreve o que são as interfaces e como usá-las em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="13b3e-132">Describes what interfaces are and how you can use them in your applications.</span></span>  
  
 [<span data-ttu-id="13b3e-133">LINQ</span><span class="sxs-lookup"><span data-stu-id="13b3e-133">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="13b3e-134">Fornece links para tópicos que apresentam recursos [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] e programação.</span><span class="sxs-lookup"><span data-stu-id="13b3e-134">Provides links to topics that introduce [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] features and programming.</span></span>  
  
 [<span data-ttu-id="13b3e-135">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="13b3e-135">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 <span data-ttu-id="13b3e-136">Fornece uma visão geral dos objetos e classes, como eles são usados, suas relações entre si e as propriedades, métodos e eventos que expõem.</span><span class="sxs-lookup"><span data-stu-id="13b3e-136">Provides an overview of objects and classes, how they are used, their relationships to each other, and the properties, methods, and events they expose.</span></span>  
  
 [<span data-ttu-id="13b3e-137">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="13b3e-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 <span data-ttu-id="13b3e-138">Descreve os elementos de código que manipulam elementos contendo valores, como usá-los com eficiência e como combiná-los para gerar novos valores.</span><span class="sxs-lookup"><span data-stu-id="13b3e-138">Describes the code elements that manipulate value-holding elements, how to use them efficiently, and how to combine them to yield new values.</span></span>  
  
 [<span data-ttu-id="13b3e-139">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="13b3e-139">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 <span data-ttu-id="13b3e-140">Descreve os procedimentos `Sub`, `Function`, `Property` e `Operator`, bem como tópicos avançados como procedimentos recursivos e sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="13b3e-140">Describes `Sub`, `Function`, `Property`, and `Operator` procedures, as well as advanced topics such as recursive and overloaded procedures.</span></span>  
  
 [<span data-ttu-id="13b3e-141">Instruções</span><span class="sxs-lookup"><span data-stu-id="13b3e-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 <span data-ttu-id="13b3e-142">Descreve as instruções de declaração e executável.</span><span class="sxs-lookup"><span data-stu-id="13b3e-142">Describes declaration and executable statements.</span></span>  
  
 [<span data-ttu-id="13b3e-143">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="13b3e-143">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 <span data-ttu-id="13b3e-144">Fornece links para tópicos que descrevem os conceitos básicos sobre o uso de cadeias de caracteres no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13b3e-144">Provides links to topics that describe the basic concepts about using strings in Visual Basic.</span></span>  
  
 [<span data-ttu-id="13b3e-145">Variáveis</span><span class="sxs-lookup"><span data-stu-id="13b3e-145">Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/index.md)  
 <span data-ttu-id="13b3e-146">Apresenta as variáveis e descreve como usá-las no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13b3e-146">Introduces variables and describes how to use them in Visual Basic.</span></span>  
  
 [<span data-ttu-id="13b3e-147">XML</span><span class="sxs-lookup"><span data-stu-id="13b3e-147">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="13b3e-148">Também fornece links para tópicos que descrevem como usar XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13b3e-148">Provides links to topics that describe how to use XML in Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="13b3e-149">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="13b3e-149">Related Sections</span></span>  
 [<span data-ttu-id="13b3e-150">Coleções</span><span class="sxs-lookup"><span data-stu-id="13b3e-150">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 <span data-ttu-id="13b3e-151">Descreve alguns dos tipos de coleções fornecidas pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13b3e-151">Describes some of the types of collections that are provided by the .NET Framework.</span></span> <span data-ttu-id="13b3e-152">Demonstra como usar coleções simples e coleções de pares chave/valor.</span><span class="sxs-lookup"><span data-stu-id="13b3e-152">Demonstrates how to use simple collections and collections of key/value pairs.</span></span>  
  
 [<span data-ttu-id="13b3e-153">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13b3e-153">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 <span data-ttu-id="13b3e-154">Fornece informações de referência sobre vários aspectos da programação do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="13b3e-154">Provides reference information on various aspects of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming.</span></span>

