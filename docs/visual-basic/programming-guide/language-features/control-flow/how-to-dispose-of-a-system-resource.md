---
title: 'Como: descartar um recurso do sistema (Visual Basic) | Documentos do Microsoft'
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
- Using statement, disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement, Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
caps.latest.revision: 15
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
ms.openlocfilehash: 110e8a3d0732d311d48cad74c2118b4ac470f408
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="908bb-102">Como descartar um recurso do sistema (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="908bb-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="908bb-103">Você pode usar um `Using` bloco para garantir que o sistema descarte um recurso quando seu código sai do bloco.</span><span class="sxs-lookup"><span data-stu-id="908bb-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="908bb-104">Isso é útil se você estiver usando um recurso do sistema que consome uma grande quantidade de memória ou outros componentes também desejam usar.</span><span class="sxs-lookup"><span data-stu-id="908bb-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="908bb-105">Para descartar uma conexão de banco de dados quando seu código for concluído com ele</span><span class="sxs-lookup"><span data-stu-id="908bb-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1.  <span data-ttu-id="908bb-106">Certifique-se de incluir as devidas [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para a conexão de banco de dados no início do seu arquivo de origem (neste caso, <xref:System.Data.SqlClient>).</xref:System.Data.SqlClient></span><span class="sxs-lookup"><span data-stu-id="908bb-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2.  <span data-ttu-id="908bb-107">Criar um `Using` bloco com a `Using` e `End Using` instruções.</span><span class="sxs-lookup"><span data-stu-id="908bb-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="908bb-108">Dentro do bloco, coloque o código que lida com a conexão de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="908bb-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3.  <span data-ttu-id="908bb-109">Declare a conexão e crie uma instância dela como parte do `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="908bb-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="908bb-110">O sistema descarta o recurso não importa como você sai do bloco, incluindo o caso de uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="908bb-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="908bb-111">Observe que você não pode acessar `sqc` de fora a `Using` bloquear, porque seu escopo é limitado para o bloco.</span><span class="sxs-lookup"><span data-stu-id="908bb-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="908bb-112">Você pode usar essa mesma técnica em um recurso do sistema como um identificador de arquivo ou um wrapper COM.</span><span class="sxs-lookup"><span data-stu-id="908bb-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="908bb-113">Você usa um `Using` bloquear quando você deseja deixar o recurso disponível para outros componentes após você ter saído do `Using` bloco.</span><span class="sxs-lookup"><span data-stu-id="908bb-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="908bb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="908bb-114">See Also</span></span>  
 <span data-ttu-id="908bb-115"><xref:System.Data.SqlClient.SqlConnection></xref:System.Data.SqlClient.SqlConnection></span><span class="sxs-lookup"><span data-stu-id="908bb-115"><xref:System.Data.SqlClient.SqlConnection></span></span>   
<span data-ttu-id="908bb-116"> [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="908bb-116"> [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="908bb-117"> [Estruturas de decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="908bb-117"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="908bb-118"> [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="908bb-118"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="908bb-119"> [Outras estruturas de controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="908bb-119"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span></span>  
<span data-ttu-id="908bb-120"> [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="908bb-120"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="908bb-121"> [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="908bb-121"> [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)</span></span>
