---
title: "Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b437be4a6f4a0cc9d5a4d21291a80c9cb8fffcd3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="61de8-102">Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61de8-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="61de8-103">Há várias maneiras diferentes de analisar e manipular suas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="61de8-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="61de8-104">Alguns dos métodos fazem parte do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] idioma e outros são inerentes a `String` classe.</span><span class="sxs-lookup"><span data-stu-id="61de8-104">Some of the methods are a part of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="61de8-105">Linguagem Visual Basic e o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="61de8-105">Visual Basic Language and the .NET Framework</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="61de8-106">métodos são usados como sendo funções inerentes da linguagem.</span><span class="sxs-lookup"><span data-stu-id="61de8-106"> methods are used as inherent functions of the language.</span></span> <span data-ttu-id="61de8-107">Eles podem ser usados sem qualificação no seu código.</span><span class="sxs-lookup"><span data-stu-id="61de8-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="61de8-108">O exemplo a seguir mostra o uso típico de um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] comando de manipulação de cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="61de8-108">The following example shows typical use of a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 <span data-ttu-id="61de8-109">Neste exemplo, o `Mid` função executa uma operação em `aString` e atribui o valor a ser `bString`.</span><span class="sxs-lookup"><span data-stu-id="61de8-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="61de8-110">Para obter uma lista de métodos de manipulação de cadeia de caracteres do Visual Basic, consulte [resumo de manipulação de cadeia de caracteres](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="61de8-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="61de8-111">Métodos compartilhados e métodos de instância</span><span class="sxs-lookup"><span data-stu-id="61de8-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="61de8-112">Você também pode manipular cadeias de caracteres com os métodos do `String` classe.</span><span class="sxs-lookup"><span data-stu-id="61de8-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="61de8-113">Há dois tipos de métodos em `String`: *compartilhado* métodos e *instância* métodos.</span><span class="sxs-lookup"><span data-stu-id="61de8-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="61de8-114">Métodos compartilhados</span><span class="sxs-lookup"><span data-stu-id="61de8-114">Shared Methods</span></span>  
 <span data-ttu-id="61de8-115">Um método compartilhado é um método que deriva de `String` classe em si e não requer uma instância da classe para funcionar.</span><span class="sxs-lookup"><span data-stu-id="61de8-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="61de8-116">Esses métodos podem ser qualificados com o nome da classe (`String`) em vez de com uma instância do `String` classe.</span><span class="sxs-lookup"><span data-stu-id="61de8-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="61de8-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="61de8-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 <span data-ttu-id="61de8-118">No exemplo anterior, o <xref:System.String.Copy%2A?displayProperty=nameWithType> é um método estático, que age sobre uma expressão fornecida e atribui o valor resultante para `bString`.</span><span class="sxs-lookup"><span data-stu-id="61de8-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="61de8-119">Métodos de instância</span><span class="sxs-lookup"><span data-stu-id="61de8-119">Instance Methods</span></span>  
 <span data-ttu-id="61de8-120">Métodos de instância, por outro lado, derivam de uma determinada instância de `String` e devem ser qualificados com o nome da instância.</span><span class="sxs-lookup"><span data-stu-id="61de8-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="61de8-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="61de8-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 <span data-ttu-id="61de8-122">Neste exemplo, o <xref:System.String.Substring%2A?displayProperty=nameWithType> é um método de instância de `String` (ou seja, `aString`).</span><span class="sxs-lookup"><span data-stu-id="61de8-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="61de8-123">Ele executa uma operação em `aString` e atribui o valor para `bString`.</span><span class="sxs-lookup"><span data-stu-id="61de8-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="61de8-124">Para obter mais informações, consulte a documentação para o <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="61de8-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61de8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61de8-125">See Also</span></span>  
 [<span data-ttu-id="61de8-126">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61de8-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
