---
title: Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 44eb101ebdfeb316958a659107190ef1fc84df44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938262"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="48605-102">Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48605-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="48605-103">Há várias maneiras diferentes de analisar e manipular suas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="48605-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="48605-104">Alguns dos métodos fazem parte da linguagem Visual Basic, e outros são inerentes a `String` classe.</span><span class="sxs-lookup"><span data-stu-id="48605-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="48605-105">Linguagem Visual Basic e o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48605-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="48605-106">Métodos de Visual Basic são usados como funções inerentes da linguagem.</span><span class="sxs-lookup"><span data-stu-id="48605-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="48605-107">Eles podem ser usados sem qualificação no seu código.</span><span class="sxs-lookup"><span data-stu-id="48605-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="48605-108">O exemplo a seguir mostra um uso típico de um comando de manipulação de cadeia de caracteres do Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="48605-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="48605-109">Neste exemplo, o `Mid` função executa uma operação no `aString` e atribui o valor a ser `bString`.</span><span class="sxs-lookup"><span data-stu-id="48605-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="48605-110">Para obter uma lista de métodos de manipulação de cadeia de caracteres do Visual Basic, consulte [resumo de manipulação de cadeia de caracteres](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="48605-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="48605-111">Métodos compartilhados e métodos de instância</span><span class="sxs-lookup"><span data-stu-id="48605-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="48605-112">Você também pode manipular cadeias de caracteres com os métodos do `String` classe.</span><span class="sxs-lookup"><span data-stu-id="48605-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="48605-113">Há dois tipos de métodos em `String`: *compartilhada* métodos e *instância* métodos.</span><span class="sxs-lookup"><span data-stu-id="48605-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="48605-114">Métodos compartilhados</span><span class="sxs-lookup"><span data-stu-id="48605-114">Shared Methods</span></span>  
 <span data-ttu-id="48605-115">Um método compartilhado é um método que deriva de `String` própria classe e não requer uma instância da classe para funcionar.</span><span class="sxs-lookup"><span data-stu-id="48605-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="48605-116">Esses métodos podem ser qualificados com o nome da classe (`String`) em vez de usar uma instância da `String` classe.</span><span class="sxs-lookup"><span data-stu-id="48605-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="48605-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="48605-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="48605-118">No exemplo anterior, o <xref:System.String.Copy%2A?displayProperty=nameWithType> método é um método estático, que age sobre uma expressão fornecida e atribui o valor resultante para `bString`.</span><span class="sxs-lookup"><span data-stu-id="48605-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="48605-119">Métodos de instância</span><span class="sxs-lookup"><span data-stu-id="48605-119">Instance Methods</span></span>  
 <span data-ttu-id="48605-120">Métodos de instância, por outro lado, derivam de uma determinada instância de `String` e devem ser qualificados com o nome da instância.</span><span class="sxs-lookup"><span data-stu-id="48605-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="48605-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="48605-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="48605-122">Neste exemplo, o <xref:System.String.Substring%2A?displayProperty=nameWithType> é um método da instância do `String` (ou seja, `aString`).</span><span class="sxs-lookup"><span data-stu-id="48605-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="48605-123">Ele executa uma operação em `aString` e atribui o valor para `bString`.</span><span class="sxs-lookup"><span data-stu-id="48605-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="48605-124">Para obter mais informações, consulte a documentação para o <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="48605-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48605-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48605-125">See also</span></span>

- [<span data-ttu-id="48605-126">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48605-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
