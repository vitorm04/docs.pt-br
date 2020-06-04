---
title: Como fazer uma variável de objeto não se referir a nenhuma instância
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: cce2e59cb76652937868a731ad308872d1aba2f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410445"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="08177-102">Como fazer uma variável de objeto não se referir a nenhuma instância (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08177-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="08177-103">Você pode desassociar uma variável de objeto de qualquer instância de objeto, definindo-a como [Nothing](../../../language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="08177-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="08177-104">Para desassociar uma variável de objeto de qualquer instância de objeto</span><span class="sxs-lookup"><span data-stu-id="08177-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="08177-105">Defina a variável como `Nothing` em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="08177-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="08177-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="08177-106">Robust Programming</span></span>  
 <span data-ttu-id="08177-107">Se o seu código tentar acessar um membro de uma variável de objeto que foi definida como `Nothing` , <xref:System.NullReferenceException> ocorrerá um.</span><span class="sxs-lookup"><span data-stu-id="08177-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="08177-108">Se você definir uma variável de objeto com `Nothing` frequência ou se for possível que a variável não seja inicializada, é uma boa ideia colocar os acessos de membros em um `Try...Catch...Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="08177-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="08177-109">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="08177-109">.NET Framework Security</span></span>  
 <span data-ttu-id="08177-110">Se você usar uma variável de objeto para objetos que contêm dados confidenciais ou confidenciais, poderá definir a variável como `Nothing` quando não estiver lidando ativamente com um desses objetos.</span><span class="sxs-lookup"><span data-stu-id="08177-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="08177-111">Isso reduz a chance de código mal-intencionado obter acesso aos dados.</span><span class="sxs-lookup"><span data-stu-id="08177-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08177-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="08177-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="08177-113">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="08177-113">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="08177-114">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="08177-114">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="08177-115">Nada</span><span class="sxs-lookup"><span data-stu-id="08177-115">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="08177-116">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="08177-116">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
