---
title: "Como: fazer um objeto variável não se referir a nenhuma instância (Visual Basic) | Documentos do Microsoft"
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
- Nothing keyword, variable assignment
- object variables, null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: 9
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
ms.openlocfilehash: 46a2ebcfc91cb61e62d25953b7d41955c5aa7a3b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="d0bb2-102">Como fazer uma variável de objeto não se referir a nenhuma instância (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0bb2-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="d0bb2-103">Você pode desassociar uma variável de objeto de qualquer instância do objeto definindo-a como [nada](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="d0bb2-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="d0bb2-104">Para desassociar uma variável de objeto de qualquer instância do objeto</span><span class="sxs-lookup"><span data-stu-id="d0bb2-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="d0bb2-105">Definir a variável `Nothing` em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="d0bb2-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="d0bb2-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="d0bb2-106">Robust Programming</span></span>  
 <span data-ttu-id="d0bb2-107">Se seu código tentar acessar um membro de uma variável de objeto que foi definido como `Nothing`, um <xref:System.NullReferenceException>ocorre.</xref:System.NullReferenceException></span><span class="sxs-lookup"><span data-stu-id="d0bb2-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="d0bb2-108">Se você definir uma variável de objeto para `Nothing` com frequência, ou se for possível, a variável não é inicializada, ele é uma boa ideia colocar os acessos a membros em um `Try...Catch...Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="d0bb2-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d0bb2-109">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0bb2-109">.NET Framework Security</span></span>  
 <span data-ttu-id="d0bb2-110">Se você usar uma variável de objeto para objetos que contêm dados confidenciais, você pode definir a variável `Nothing` quando você não está ativamente lidando com um desses objetos.</span><span class="sxs-lookup"><span data-stu-id="d0bb2-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="d0bb2-111">Isso reduz a chance de códigos mal-intencionados acessem os dados.</span><span class="sxs-lookup"><span data-stu-id="d0bb2-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0bb2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0bb2-112">See Also</span></span>  
 <span data-ttu-id="d0bb2-113"><xref:System.NullReferenceException></xref:System.NullReferenceException></span><span class="sxs-lookup"><span data-stu-id="d0bb2-113"><xref:System.NullReferenceException></span></span>   
<span data-ttu-id="d0bb2-114"> [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="d0bb2-114"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="d0bb2-115"> [Atribuição de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span><span class="sxs-lookup"><span data-stu-id="d0bb2-115"> [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span></span>  
<span data-ttu-id="d0bb2-116"> [Nada](../../../../visual-basic/language-reference/nothing.md) </span><span class="sxs-lookup"><span data-stu-id="d0bb2-116"> [Nothing](../../../../visual-basic/language-reference/nothing.md) </span></span>  
<span data-ttu-id="d0bb2-117"> [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d0bb2-117"> [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="d0bb2-118"> [Solução de problemas de exceções: System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)</span><span class="sxs-lookup"><span data-stu-id="d0bb2-118"> [Troubleshooting Exceptions: System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)</span></span>
