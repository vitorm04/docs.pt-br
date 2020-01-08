---
title: Como converter um objeto em outro tipo
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 6d16e0eafc3fa9233037abe0c92dcb1945ca8da9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341583"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="a0b0e-102">Como converter um objeto em outro tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0b0e-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="a0b0e-103">Você converte uma variável `Object` para outro tipo de dados usando uma palavra-chave de conversão, como a [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="a0b0e-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0b0e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0b0e-104">Example</span></span>  
 <span data-ttu-id="a0b0e-105">O exemplo a seguir converte uma variável `Object` em um `Integer` e um `String`.</span><span class="sxs-lookup"><span data-stu-id="a0b0e-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="a0b0e-106">Se você souber que o conteúdo de uma variável de `Object` é de um tipo de dados específico, é melhor converter a variável para esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a0b0e-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="a0b0e-107">Se você continuar usando a variável `Object`, você incorrerá em *Boxing* e *unboxing* (para um tipo de valor) ou *associação tardia* (para um tipo de referência).</span><span class="sxs-lookup"><span data-stu-id="a0b0e-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="a0b0e-108">Todas essas operações têm tempo de execução extra e tornam o desempenho mais lento.</span><span class="sxs-lookup"><span data-stu-id="a0b0e-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="a0b0e-109">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="a0b0e-109">Compile the code</span></span>  
 <span data-ttu-id="a0b0e-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a0b0e-110">This example requires:</span></span>  
  
- <span data-ttu-id="a0b0e-111">Uma referência ao namespace <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0b0e-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b0e-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="a0b0e-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="a0b0e-113">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0b0e-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="a0b0e-114">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="a0b0e-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="a0b0e-115">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="a0b0e-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="a0b0e-116">Conversões entre Cadeias de Caracteres e Outros Tipos</span><span class="sxs-lookup"><span data-stu-id="a0b0e-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="a0b0e-117">Conversões de Matriz</span><span class="sxs-lookup"><span data-stu-id="a0b0e-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="a0b0e-118">Estruturas</span><span class="sxs-lookup"><span data-stu-id="a0b0e-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a0b0e-119">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="a0b0e-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a0b0e-120">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="a0b0e-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
