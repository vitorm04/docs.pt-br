---
title: Como descartar um recurso do sistema (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5b5c65c9d123c6f481852eb249cb4d479a180c5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Como descartar um recurso do sistema (Visual Basic)
Você pode usar um `Using` bloco para garantir que o sistema descarte um recurso quando seu código sai do bloco. Isso é útil se você estiver usando um recurso do sistema que consome uma grande quantidade de memória ou outros componentes também desejam usar.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Para descartar uma conexão de banco de dados quando o código for concluído com ele  
  
1.  Certifique-se de incluir as [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para a conexão de banco de dados no início do seu arquivo de origem (nesse caso, <xref:System.Data.SqlClient>).  
  
2.  Criar um `Using` bloco com a `Using` e `End Using` instruções. Dentro do bloco, coloque o código que lida com a conexão de banco de dados.  
  
3.  A conexão de declarar e criar uma instância dela como parte do `Using` instrução.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     O sistema descarta o recurso não importa como você sair do bloco, incluindo o caso de uma exceção sem tratamento.  
  
     Observe que você não pode acessar `sqc` de fora de `Using` bloquear, porque seu escopo é limitado para o bloco.  
  
     Você pode usar essa mesma técnica em um recurso do sistema como um identificador de arquivo ou um wrapper COM. Você usa um `Using` bloquear quando você deseja deixar o recurso disponível para outros componentes após você ter saído do `Using` bloco.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.SqlClient.SqlConnection>  
 [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Estruturas de Decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Outras Estruturas de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [Estruturas de Controle Aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md)
