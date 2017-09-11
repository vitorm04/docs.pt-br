---
title: "Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- object variables, declaring
- declaring object variables
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: 11
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 8e19153ff3aee931fdd16e1f8a2df5968e55c160
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="312df-102">Como declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="312df-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="312df-103">Declare uma variável do [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) especificando `As Object` em uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="312df-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="312df-104">Atribuir um objeto para tal variável colocando o objeto depois do sinal de igual (`=`) em uma cláusula de inicialização ou instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="312df-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="312df-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="312df-105">Example</span></span>  
 <span data-ttu-id="312df-106">O exemplo a seguir declara um `Object` variável e atribui a instância atual para ele.</span><span class="sxs-lookup"><span data-stu-id="312df-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="312df-107">Você pode combinar a declaração e atribuição Inicializando a variável como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="312df-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="312df-108">O exemplo a seguir é equivalente ao exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="312df-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="312df-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="312df-109">Compiling the Code</span></span>  
 <span data-ttu-id="312df-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="312df-110">This example requires:</span></span>  
  
-   <span data-ttu-id="312df-111">Uma referência para o <xref:System>namespace.</xref:System></span><span class="sxs-lookup"><span data-stu-id="312df-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="312df-112">Uma classe, estrutura ou módulo no qual colocar o `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="312df-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="312df-113">Um procedimento no qual colocar a instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="312df-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="312df-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="312df-114">See Also</span></span>  
 <span data-ttu-id="312df-115">[Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="312df-115">[Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="312df-116"> [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="312df-116"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="312df-117"> [Declaração de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="312df-117"> [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="312df-118"> [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="312df-118"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="312df-119"> [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="312df-119"> [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="312df-120"> [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="312df-120"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="312df-121"> [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="312df-121"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>

