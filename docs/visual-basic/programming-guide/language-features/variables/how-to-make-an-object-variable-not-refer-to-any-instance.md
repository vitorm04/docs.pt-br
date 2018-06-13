---
title: Como fazer uma variável de objeto não se referir a nenhuma instância (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: bf918b762261e1dd1fc4161a10203f3d0067e454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649718"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="1ce37-102">Como fazer uma variável de objeto não se referir a nenhuma instância (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ce37-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="1ce37-103">Você pode desassociar uma variável de objeto de qualquer instância do objeto definindo-a como [nada](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="1ce37-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="1ce37-104">Para desassociar uma variável de objeto de qualquer instância do objeto</span><span class="sxs-lookup"><span data-stu-id="1ce37-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="1ce37-105">Defina a variável para `Nothing` em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="1ce37-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="1ce37-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="1ce37-106">Robust Programming</span></span>  
 <span data-ttu-id="1ce37-107">Se seu código tentar acessar um membro de uma variável de objeto que foi definida como `Nothing`, um <xref:System.NullReferenceException> ocorre.</span><span class="sxs-lookup"><span data-stu-id="1ce37-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="1ce37-108">Se você definir uma variável de objeto `Nothing` com frequência, ou se é possível que a variável não é inicializada, é aconselhável colocar o acesso de membro em uma `Try...Catch...Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="1ce37-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1ce37-109">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1ce37-109">.NET Framework Security</span></span>  
 <span data-ttu-id="1ce37-110">Se você usar uma variável de objeto para objetos que contêm dados confidenciais, você pode definir a variável `Nothing` quando você não estará ativamente lidando com um desses objetos.</span><span class="sxs-lookup"><span data-stu-id="1ce37-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="1ce37-111">Isso reduz a chance de programas mal-intencionados obtenham acesso aos dados.</span><span class="sxs-lookup"><span data-stu-id="1ce37-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce37-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ce37-112">See Also</span></span>  
 <xref:System.NullReferenceException>  
 [<span data-ttu-id="1ce37-113">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="1ce37-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="1ce37-114">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="1ce37-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="1ce37-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="1ce37-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="1ce37-116">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="1ce37-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="1ce37-117">Solução de problemas de exceções: System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="1ce37-117">Troubleshooting Exceptions: System.NullReferenceException</span></span>](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
