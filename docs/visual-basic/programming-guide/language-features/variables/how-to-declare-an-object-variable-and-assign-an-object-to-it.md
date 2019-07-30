---
title: 'Como: Declare uma variável de objeto e atribua um objeto a ela no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630875"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="e7ac5-102">Como: Declare uma variável de objeto e atribua um objeto a ela no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7ac5-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="e7ac5-103">Você declara uma variável do [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) especificando `As Object` em uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e7ac5-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="e7ac5-104">Você atribui um objeto a tal variável colocando o objeto após o sinal de igual (`=`) em uma instrução de atribuição ou uma cláusula de inicialização.</span><span class="sxs-lookup"><span data-stu-id="e7ac5-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="e7ac5-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7ac5-105">Example</span></span>

<span data-ttu-id="e7ac5-106">O exemplo a seguir declara uma `Object` variável e atribui a instância atual a ela.</span><span class="sxs-lookup"><span data-stu-id="e7ac5-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="e7ac5-107">Você pode combinar a declaração e a atribuição inicializando a variável como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="e7ac5-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="e7ac5-108">O exemplo a seguir é equivalente ao exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="e7ac5-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a><span data-ttu-id="e7ac5-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e7ac5-109">Compiling the Code</span></span>

<span data-ttu-id="e7ac5-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e7ac5-110">This example requires:</span></span>

- <span data-ttu-id="e7ac5-111">Uma referência ao <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="e7ac5-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="e7ac5-112">Uma classe, estrutura ou módulo no qual colocar a `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="e7ac5-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="e7ac5-113">Um procedimento no qual colocar a instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="e7ac5-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7ac5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7ac5-114">See also</span></span>

- [<span data-ttu-id="e7ac5-115">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="e7ac5-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="e7ac5-116">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="e7ac5-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="e7ac5-117">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="e7ac5-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="e7ac5-118">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="e7ac5-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="e7ac5-119">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="e7ac5-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="e7ac5-120">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="e7ac5-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="e7ac5-121">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="e7ac5-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
