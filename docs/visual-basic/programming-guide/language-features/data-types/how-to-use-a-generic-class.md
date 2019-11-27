---
title: Como usar uma classe genérica
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 87ca0da5095484615666cda505b4f7678d8160de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350053"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="480c6-102">Como usar uma classe genérica (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="480c6-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="480c6-103">Uma classe que usa *parâmetros de tipo* é chamada de *classe genérica*.</span><span class="sxs-lookup"><span data-stu-id="480c6-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="480c6-104">Se você estiver usando uma classe genérica, poderá gerar uma *classe construída* a partir dela fornecendo um argumento de *tipo* para cada um desses parâmetros.</span><span class="sxs-lookup"><span data-stu-id="480c6-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="480c6-105">Você pode então declarar uma variável do tipo de classe construída e pode criar uma instância da classe construída e atribuí-la a essa variável.</span><span class="sxs-lookup"><span data-stu-id="480c6-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="480c6-106">Além das classes, você também pode definir e usar estruturas genéricas, interfaces, procedimentos e delegados.</span><span class="sxs-lookup"><span data-stu-id="480c6-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="480c6-107">O procedimento a seguir usa uma classe genérica definida no .NET Framework e cria uma instância a partir dela.</span><span class="sxs-lookup"><span data-stu-id="480c6-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="480c6-108">Para usar uma classe que usa um parâmetro de tipo</span><span class="sxs-lookup"><span data-stu-id="480c6-108">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="480c6-109">No início do arquivo de origem, inclua uma [instrução Imports (namespace e tipo do .net)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para importar o namespace <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="480c6-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="480c6-110">Isso permite que você consulte a classe <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sem precisar qualificá-la totalmente para diferenciá-la de outras classes de fila, como <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="480c6-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="480c6-111">Crie o objeto da maneira normal, mas adicione `(Of type)` imediatamente após o nome da classe.</span><span class="sxs-lookup"><span data-stu-id="480c6-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="480c6-112">O exemplo a seguir usa a mesma classe (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) para criar dois objetos de fila que contêm itens de tipos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="480c6-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="480c6-113">Ele adiciona itens ao final de cada fila e, em seguida, remove e exibe itens da frente de cada fila.</span><span class="sxs-lookup"><span data-stu-id="480c6-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="480c6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="480c6-114">See also</span></span>

- [<span data-ttu-id="480c6-115">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="480c6-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="480c6-116">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="480c6-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="480c6-117">Componentes de independência de linguagem e componentes independentes da linguagem</span><span class="sxs-lookup"><span data-stu-id="480c6-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="480c6-118">Of</span><span class="sxs-lookup"><span data-stu-id="480c6-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="480c6-119">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="480c6-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="480c6-120">Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes</span><span class="sxs-lookup"><span data-stu-id="480c6-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="480c6-121">Iteradores</span><span class="sxs-lookup"><span data-stu-id="480c6-121">Iterators</span></span>](../../../../visual-basic/programming-guide/concepts/iterators.md)
