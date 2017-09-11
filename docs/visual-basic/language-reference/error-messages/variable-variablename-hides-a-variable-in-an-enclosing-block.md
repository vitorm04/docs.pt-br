---
title: "Variável &quot;&lt;variablename&gt;&quot; oculta uma variável em um bloco delimitador | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
dev_langs:
- VB
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 8
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
ms.openlocfilehash: 4ca5cbc88e1b4a60fa29e4f8468a177083f6a2f3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="de569-102">Variável '&lt;variablename&gt;' oculta uma variável em um bloco delimitador</span><span class="sxs-lookup"><span data-stu-id="de569-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="de569-103">Uma variável incluída em um bloco tem o mesmo nome que outra variável local.</span><span class="sxs-lookup"><span data-stu-id="de569-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="de569-104">**ID do erro:** BC30616</span><span class="sxs-lookup"><span data-stu-id="de569-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="de569-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="de569-105">To correct this error</span></span>  
  
-   <span data-ttu-id="de569-106">Renomear a variável no bloco incluso para que não seja o mesmo que todas as outras variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="de569-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="de569-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="de569-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="de569-108">Uma causa comum para esse erro é o uso de `Catch e As Exception` dentro de um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="de569-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="de569-109">Se esse for o caso, o nome o `Catch` variável de bloco `ex` em vez de `e`.</span><span class="sxs-lookup"><span data-stu-id="de569-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="de569-110">Outra origem comum desse erro é uma tentativa de acessar uma variável local declarada dentro de um `Try` bloquear em um separado `Catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="de569-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="de569-111">Para corrigir isso, declare a variável de fora a `Try...Catch...Finally` estrutura.</span><span class="sxs-lookup"><span data-stu-id="de569-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de569-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de569-112">See Also</span></span>  
 <span data-ttu-id="de569-113">[Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="de569-113">[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="de569-114"> [Declaração de Variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)</span><span class="sxs-lookup"><span data-stu-id="de569-114"> [Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)</span></span>
