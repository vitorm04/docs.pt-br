---
title: "Tipos de métodos de manipulação de cadeia de caracteres no Visual Basic | Documentos do Microsoft"
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
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c63ad0931ae2f3760576a792795b9fe0ab6a409
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="bc294-102">Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc294-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="bc294-103">Há várias maneiras diferentes de analisar e manipular suas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bc294-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="bc294-104">Alguns dos métodos fazem parte do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] idioma e outros são inerentes a `String` classe.</span><span class="sxs-lookup"><span data-stu-id="bc294-104">Some of the methods are a part of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="bc294-105">Linguagem Visual Basic e o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bc294-105">Visual Basic Language and the .NET Framework</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="bc294-106">métodos são usados como sendo funções inerentes da linguagem.</span><span class="sxs-lookup"><span data-stu-id="bc294-106"> methods are used as inherent functions of the language.</span></span> <span data-ttu-id="bc294-107">Eles podem ser usados sem qualificação no seu código.</span><span class="sxs-lookup"><span data-stu-id="bc294-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="bc294-108">O exemplo a seguir mostra o uso típico de um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] comando de manipulação de cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="bc294-108">The following example shows typical use of a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string-manipulation command:</span></span>  
  
 <span data-ttu-id="bc294-109">[!code-vb[VbVbalrStrings&#44;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc294-109">[!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]</span></span>  
  
 <span data-ttu-id="bc294-110">Neste exemplo, o `Mid` função executa uma operação em `aString` e atribui o valor para `bString`.</span><span class="sxs-lookup"><span data-stu-id="bc294-110">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="bc294-111">Para obter uma lista de métodos de manipulação de cadeia de caracteres do Visual Basic, consulte [resumo de manipulação de cadeia de caracteres](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="bc294-111">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="bc294-112">Métodos compartilhados e métodos de instância</span><span class="sxs-lookup"><span data-stu-id="bc294-112">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="bc294-113">Você também pode manipular cadeias de caracteres com os métodos de `String` classe.</span><span class="sxs-lookup"><span data-stu-id="bc294-113">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="bc294-114">Há dois tipos de métodos em `String`: *compartilhado* métodos e *instância* métodos.</span><span class="sxs-lookup"><span data-stu-id="bc294-114">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="bc294-115">Métodos compartilhados</span><span class="sxs-lookup"><span data-stu-id="bc294-115">Shared Methods</span></span>  
 <span data-ttu-id="bc294-116">Um método compartilhado é um método que deriva de `String` classe em si e não requer uma instância da classe para funcionar.</span><span class="sxs-lookup"><span data-stu-id="bc294-116">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="bc294-117">Esses métodos podem ser qualificados com o nome da classe (`String`) em vez de usar uma instância do `String` classe.</span><span class="sxs-lookup"><span data-stu-id="bc294-117">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="bc294-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bc294-118">For example:</span></span>  
  
 <span data-ttu-id="bc294-119">[!code-vb[45 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc294-119">[!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]</span></span>  
  
 <span data-ttu-id="bc294-120">No exemplo anterior, o <xref:System.String.Copy%2A?displayProperty=fullName>método é um método estático, que age sobre uma expressão fornecida e atribui o valor resultante para `bString`.</xref:System.String.Copy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bc294-120">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=fullName> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="bc294-121">Métodos de instância</span><span class="sxs-lookup"><span data-stu-id="bc294-121">Instance Methods</span></span>  
 <span data-ttu-id="bc294-122">Métodos de instância, por outro lado, derivam de uma determinada instância de `String` e devem ser qualificados com o nome da instância.</span><span class="sxs-lookup"><span data-stu-id="bc294-122">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="bc294-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bc294-123">For example:</span></span>  
  
 <span data-ttu-id="bc294-124">[!code-vb[46 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc294-124">[!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]</span></span>  
  
 <span data-ttu-id="bc294-125">Neste exemplo, o <xref:System.String.Substring%2A?displayProperty=fullName>método é um método de instância de `String` (ou seja, `aString`).</xref:System.String.Substring%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bc294-125">In this example, the <xref:System.String.Substring%2A?displayProperty=fullName> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="bc294-126">Ele realiza uma operação em `aString` e atribui o valor para `bString`.</span><span class="sxs-lookup"><span data-stu-id="bc294-126">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="bc294-127">Para obter mais informações, consulte a documentação para a <xref:System.String>classe.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="bc294-127">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc294-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc294-128">See Also</span></span>  
 [<span data-ttu-id="bc294-129">Introdução a cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc294-129">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
