---
title: 'Como: Converter um objeto em outro tipo'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: cdb78bc66867ce27076d7b7e42de6a2880cb3a8c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393955"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="d133f-102">Como converter um objeto em outro tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d133f-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="d133f-103">Você converte uma `Object` variável em outro tipo de dados usando uma palavra-chave de conversão, como a [função CType](../../../language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="d133f-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d133f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d133f-104">Example</span></span>  
 <span data-ttu-id="d133f-105">O exemplo a seguir converte uma `Object` variável em um `Integer` e um `String` .</span><span class="sxs-lookup"><span data-stu-id="d133f-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="d133f-106">Se você souber que o conteúdo de uma `Object` variável é de um tipo de dados específico, será melhor converter a variável para esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d133f-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="d133f-107">Se você continuar usando a `Object` variável, você incorrerá em *Boxing* e *unboxing* (para um tipo de valor) ou *associação tardia* (para um tipo de referência).</span><span class="sxs-lookup"><span data-stu-id="d133f-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="d133f-108">Todas essas operações têm tempo de execução extra e tornam o desempenho mais lento.</span><span class="sxs-lookup"><span data-stu-id="d133f-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="d133f-109">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="d133f-109">Compile the code</span></span>  
 <span data-ttu-id="d133f-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d133f-110">This example requires:</span></span>  
  
- <span data-ttu-id="d133f-111">Uma referência ao <xref:System?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="d133f-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d133f-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="d133f-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="d133f-113">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d133f-113">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="d133f-114">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="d133f-114">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="d133f-115">Conversões implícitas e explícitas</span><span class="sxs-lookup"><span data-stu-id="d133f-115">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="d133f-116">Conversões entre cadeias de caracteres e outros tipos</span><span class="sxs-lookup"><span data-stu-id="d133f-116">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="d133f-117">Conversões de matriz</span><span class="sxs-lookup"><span data-stu-id="d133f-117">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="d133f-118">Estruturas</span><span class="sxs-lookup"><span data-stu-id="d133f-118">Structures</span></span>](structures.md)
- [<span data-ttu-id="d133f-119">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="d133f-119">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="d133f-120">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="d133f-120">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
