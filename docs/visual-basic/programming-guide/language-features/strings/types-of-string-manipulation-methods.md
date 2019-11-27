---
title: Tipos de métodos de manipulação de cadeia de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a02278abfb71efb2f31f239a89a22ad1c8ee7a18
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346279"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="510ca-102">Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="510ca-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="510ca-103">Há várias maneiras diferentes de analisar e manipular suas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="510ca-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="510ca-104">Alguns dos métodos fazem parte da linguagem de Visual Basic e outros são inerentes à classe `String`.</span><span class="sxs-lookup"><span data-stu-id="510ca-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="510ca-105">Visual Basic idioma e o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="510ca-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="510ca-106">Visual Basic métodos são usados como funções inerentes do idioma.</span><span class="sxs-lookup"><span data-stu-id="510ca-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="510ca-107">Eles podem ser usados sem qualificação em seu código.</span><span class="sxs-lookup"><span data-stu-id="510ca-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="510ca-108">O exemplo a seguir mostra o uso típico de um comando de manipulação de cadeia de caracteres Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="510ca-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="510ca-109">Neste exemplo, a função `Mid` executa uma operação direta em `aString` e atribui o valor a `bString`.</span><span class="sxs-lookup"><span data-stu-id="510ca-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="510ca-110">Para obter uma lista de métodos de manipulação de cadeia de caracteres Visual Basic, consulte [Resumo de manipulação de cadeia de caracteres](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="510ca-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="510ca-111">Métodos compartilhados e métodos de instância</span><span class="sxs-lookup"><span data-stu-id="510ca-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="510ca-112">Você também pode manipular cadeias de caracteres com os métodos da classe `String`.</span><span class="sxs-lookup"><span data-stu-id="510ca-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="510ca-113">Há dois tipos de métodos em `String`: métodos *compartilhados* e métodos de *instância* .</span><span class="sxs-lookup"><span data-stu-id="510ca-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="510ca-114">Métodos compartilhados</span><span class="sxs-lookup"><span data-stu-id="510ca-114">Shared Methods</span></span>  
 <span data-ttu-id="510ca-115">Um método compartilhado é um método que deriva da própria classe `String` e não requer uma instância dessa classe para funcionar.</span><span class="sxs-lookup"><span data-stu-id="510ca-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="510ca-116">Esses métodos podem ser qualificados com o nome da classe (`String`) em vez de uma instância da classe `String`.</span><span class="sxs-lookup"><span data-stu-id="510ca-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="510ca-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="510ca-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="510ca-118">No exemplo anterior, o método <xref:System.String.Copy%2A?displayProperty=nameWithType> é um método estático, que atua em uma expressão que é fornecida e atribui o valor resultante a `bString`.</span><span class="sxs-lookup"><span data-stu-id="510ca-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="510ca-119">Métodos de instância</span><span class="sxs-lookup"><span data-stu-id="510ca-119">Instance Methods</span></span>  
 <span data-ttu-id="510ca-120">Os métodos de instância, por outro lado, são provenientes de uma instância específica do `String` e devem ser qualificados com o nome da instância.</span><span class="sxs-lookup"><span data-stu-id="510ca-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="510ca-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="510ca-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="510ca-122">Neste exemplo, o método <xref:System.String.Substring%2A?displayProperty=nameWithType> é um método da instância de `String` (ou seja, `aString`).</span><span class="sxs-lookup"><span data-stu-id="510ca-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="510ca-123">Ele executa uma operação em `aString` e atribui esse valor a `bString`.</span><span class="sxs-lookup"><span data-stu-id="510ca-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="510ca-124">Para obter mais informações, consulte a documentação da classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="510ca-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510ca-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="510ca-125">See also</span></span>

- [<span data-ttu-id="510ca-126">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="510ca-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
