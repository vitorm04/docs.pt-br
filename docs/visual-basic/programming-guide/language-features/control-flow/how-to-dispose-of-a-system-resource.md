---
title: Como descartar um recurso do sistema (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: cbb66934833da2bd6f0b797944dbb9c4df267cfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647225"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="7106e-102">Como descartar um recurso do sistema (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7106e-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="7106e-103">Você pode usar um `Using` bloco para garantir que o sistema descarte um recurso quando seu código sai do bloco.</span><span class="sxs-lookup"><span data-stu-id="7106e-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="7106e-104">Isso é útil se você estiver usando um recurso do sistema que consome uma grande quantidade de memória ou outros componentes também desejam usar.</span><span class="sxs-lookup"><span data-stu-id="7106e-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="7106e-105">Para descartar uma conexão de banco de dados quando o código for concluído com ele</span><span class="sxs-lookup"><span data-stu-id="7106e-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1.  <span data-ttu-id="7106e-106">Certifique-se de incluir as [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para a conexão de banco de dados no início do seu arquivo de origem (nesse caso, <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="7106e-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2.  <span data-ttu-id="7106e-107">Criar um `Using` bloco com a `Using` e `End Using` instruções.</span><span class="sxs-lookup"><span data-stu-id="7106e-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="7106e-108">Dentro do bloco, coloque o código que lida com a conexão de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="7106e-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3.  <span data-ttu-id="7106e-109">A conexão de declarar e criar uma instância dela como parte do `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="7106e-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="7106e-110">O sistema descarta o recurso não importa como você sair do bloco, incluindo o caso de uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="7106e-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="7106e-111">Observe que você não pode acessar `sqc` de fora de `Using` bloquear, porque seu escopo é limitado para o bloco.</span><span class="sxs-lookup"><span data-stu-id="7106e-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="7106e-112">Você pode usar essa mesma técnica em um recurso do sistema como um identificador de arquivo ou um wrapper COM.</span><span class="sxs-lookup"><span data-stu-id="7106e-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="7106e-113">Você usa um `Using` bloquear quando você deseja deixar o recurso disponível para outros componentes após você ter saído do `Using` bloco.</span><span class="sxs-lookup"><span data-stu-id="7106e-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7106e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7106e-114">See Also</span></span>  
 <xref:System.Data.SqlClient.SqlConnection>  
 [<span data-ttu-id="7106e-115">Fluxo de Controle</span><span class="sxs-lookup"><span data-stu-id="7106e-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="7106e-116">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="7106e-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="7106e-117">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="7106e-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="7106e-118">Outras Estruturas de Controle</span><span class="sxs-lookup"><span data-stu-id="7106e-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="7106e-119">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="7106e-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="7106e-120">Instrução Using</span><span class="sxs-lookup"><span data-stu-id="7106e-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
