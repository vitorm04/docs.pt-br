---
title: 'Como: Fazer um objeto variável não se referir a qualquer instância (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 820d4cb9d17bf467d257bfbba5f43f07228c0b4f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663554"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="05015-102">Como: Fazer um objeto variável não se referir a qualquer instância (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05015-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="05015-103">Você pode desassociar uma variável de objeto de qualquer instância do objeto definindo-a para [nada](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="05015-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="05015-104">Para desassociar uma variável de objeto de qualquer instância do objeto</span><span class="sxs-lookup"><span data-stu-id="05015-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="05015-105">Defina a variável para `Nothing` em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="05015-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="05015-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="05015-106">Robust Programming</span></span>  
 <span data-ttu-id="05015-107">Se seu código tentar acessar um membro de uma variável de objeto que foi definido como `Nothing`, um <xref:System.NullReferenceException> ocorre.</span><span class="sxs-lookup"><span data-stu-id="05015-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="05015-108">Se você definir uma variável de objeto como `Nothing` com frequência, ou se for possível, a variável não é inicializada, é uma boa ideia colocar os acessos de membro em um `Try...Catch...Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="05015-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="05015-109">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="05015-109">.NET Framework Security</span></span>  
 <span data-ttu-id="05015-110">Se você usar uma variável de objeto para objetos que contêm dados confidenciais, você pode definir a variável `Nothing` quando você não está ativamente lidando com um desses objetos.</span><span class="sxs-lookup"><span data-stu-id="05015-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="05015-111">Isso reduz a chance de códigos mal-intencionados obtenham acesso aos dados.</span><span class="sxs-lookup"><span data-stu-id="05015-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05015-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05015-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="05015-113">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="05015-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="05015-114">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="05015-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="05015-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="05015-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="05015-116">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="05015-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
