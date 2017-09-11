---
title: "Como modificar o conteúdo de uma cadeia de caracteres (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: 114b6fdabd235d7e57947e77b672352e28aff11e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-modify-string-contents-c-programming-guide"></a><span data-ttu-id="4c7de-102">Como modificar o conteúdo de uma cadeia de caracteres (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4c7de-102">How to: Modify String Contents (C# Programming Guide)</span></span>
<span data-ttu-id="4c7de-103">Como as cadeias de caracteres são *imutáveis*, não é possível (sem usar código não seguro) modificar o valor de um objeto de cadeia de caracteres depois que ele foi criado.</span><span class="sxs-lookup"><span data-stu-id="4c7de-103">Because strings are *immutable*, it is not possible (without using unsafe code) to modify the value of a string object after it has been created.</span></span> <span data-ttu-id="4c7de-104">No entanto, há várias maneiras de modificar o valor de uma cadeia de caracteres e armazenar o resultado em um novo objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4c7de-104">However, there are many ways to modify the value of a string and store the result in a new string object.</span></span> <span data-ttu-id="4c7de-105">A classe <xref:System.String?displayProperty=fullName> fornece métodos que operam em uma cadeia de caracteres de entrada e retornam um novo objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4c7de-105">The <xref:System.String?displayProperty=fullName> class provides methods that operate on an input string and return a new string object.</span></span> <span data-ttu-id="4c7de-106">Em muitos casos, você pode atribuir o novo objeto à variável que mantinha a cadeia de caracteres original.</span><span class="sxs-lookup"><span data-stu-id="4c7de-106">In many cases, you can assign the new object to the variable that held the original string.</span></span> <span data-ttu-id="4c7de-107">A classe <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> fornece métodos adicionais que funcionam de maneira semelhante.</span><span class="sxs-lookup"><span data-stu-id="4c7de-107">The <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> class provides additional methods that work in a similar manner.</span></span> <span data-ttu-id="4c7de-108">A classe <xref:System.Text.StringBuilder?displayProperty=fullName> fornece um buffer de caracteres que você pode modificar "no local."</span><span class="sxs-lookup"><span data-stu-id="4c7de-108">The <xref:System.Text.StringBuilder?displayProperty=fullName> class provides a character buffer that you can modify "in-place."</span></span> <span data-ttu-id="4c7de-109">Você chama o método <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> para criar um novo objeto de cadeia de caracteres que contém o conteúdo atual do buffer.</span><span class="sxs-lookup"><span data-stu-id="4c7de-109">You call the <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> method to create a new string object that contains the current contents of the buffer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c7de-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c7de-110">Example</span></span>  
 <span data-ttu-id="4c7de-111">O exemplo a seguir mostra várias maneiras para substituir ou remover subcadeias de caracteres em uma cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="4c7de-111">The following example shows various ways to replace or remove substrings in a specified string.</span></span>  
  
 <span data-ttu-id="4c7de-112">[!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c7de-112">[!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c7de-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c7de-113">Example</span></span>  
 <span data-ttu-id="4c7de-114">Para acessar os caracteres individuais em uma cadeia de caracteres usando a notação de matriz, você pode usar o objeto <xref:System.Text.StringBuilder>, que sobrecarrega o operador `[]` para fornecer acesso ao seu buffer de caracteres interno.</span><span class="sxs-lookup"><span data-stu-id="4c7de-114">To access the individual characters in a string by using array notation, you can use the <xref:System.Text.StringBuilder> object, which overloads the `[]` operator to provide access to its internal character buffer.</span></span> <span data-ttu-id="4c7de-115">Você também pode converter a cadeia de caracteres em uma matriz de caracteres usando o método <xref:System.String.ToCharArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c7de-115">You can also convert the string to an array of chars by using the <xref:System.String.ToCharArray%2A> method.</span></span> <span data-ttu-id="4c7de-116">O exemplo a seguir usa o método `ToCharArray` para criar a matriz.</span><span class="sxs-lookup"><span data-stu-id="4c7de-116">The following example uses `ToCharArray` to create the array.</span></span> <span data-ttu-id="4c7de-117">Alguns elementos dessa matriz são modificados.</span><span class="sxs-lookup"><span data-stu-id="4c7de-117">Some elements of this array are then modified.</span></span> <span data-ttu-id="4c7de-118">Um construtor de cadeia de caracteres que recebe uma matriz de char como um parâmetro de entrada é chamado para criar uma nova cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4c7de-118">A string constructor that takes a char array as an input parameter is then called to create a new string.</span></span>  
  
 <span data-ttu-id="4c7de-119">[!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c7de-119">[!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c7de-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c7de-120">Example</span></span>  
 <span data-ttu-id="4c7de-121">O exemplo a seguir é fornecido para aquelas situações raras em que você talvez queira modificar uma cadeia de caracteres in-loco, usando código não seguro, de maneira semelhante a matrizes de caracteres de estilo C.</span><span class="sxs-lookup"><span data-stu-id="4c7de-121">The following example is provided for those very rare situations in which you may want to modify a string in-place by using unsafe code in a manner similar to C-style char arrays.</span></span> <span data-ttu-id="4c7de-122">O exemplo mostra como acessar os caracteres individuais "in-loco", usando a palavra-chave fixed.</span><span class="sxs-lookup"><span data-stu-id="4c7de-122">The example shows how to access the individual characters "in-place" by using the fixed keyword.</span></span> <span data-ttu-id="4c7de-123">Ele também demonstra um possível efeito colateral das operações não seguras em cadeias de caracteres, que resultam da forma com que o compilador C# armazena (interna) as cadeias de caracteres internamente.</span><span class="sxs-lookup"><span data-stu-id="4c7de-123">It also demonstrates one possible side effect of unsafe operations on strings that results from the way that the C# compiler stores (interns) strings internally.</span></span> <span data-ttu-id="4c7de-124">Em geral, você não deve usar essa técnica, a menos que seja absolutamente necessário.</span><span class="sxs-lookup"><span data-stu-id="4c7de-124">In general, you should not use this technique unless it is absolutely necessary.</span></span>  
  
 <span data-ttu-id="4c7de-125">[!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c7de-125">[!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7de-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c7de-126">See Also</span></span>  
 <span data-ttu-id="4c7de-127">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c7de-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="4c7de-128">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="4c7de-128">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

