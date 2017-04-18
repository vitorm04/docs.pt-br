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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9e0223faa18d8bc471d5e4a0d70b160b56c976fd
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Como descartar um recurso do sistema (Visual Basic)
Você pode usar um `Using` bloco para garantir que o sistema descarte um recurso quando seu código sai do bloco. Isso é útil se você estiver usando um recurso do sistema que consome uma grande quantidade de memória ou outros componentes também desejam usar.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Para descartar uma conexão de banco de dados quando seu código for concluído com ele  
  
1.  Certifique-se de incluir as devidas [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para a conexão de banco de dados no início do seu arquivo de origem (neste caso, <xref:System.Data.SqlClient>).</xref:System.Data.SqlClient>  
  
2.  Criar um `Using` bloco com a `Using` e `End Using` instruções. Dentro do bloco, coloque o código que lida com a conexão de banco de dados.  
  
3.  Declare a conexão e crie uma instância dela como parte do `Using` instrução.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     O sistema descarta o recurso não importa como você sai do bloco, incluindo o caso de uma exceção sem tratamento.  
  
     Observe que você não pode acessar `sqc` de fora a `Using` bloquear, porque seu escopo é limitado para o bloco.  
  
     Você pode usar essa mesma técnica em um recurso do sistema como um identificador de arquivo ou um wrapper COM. Você usa um `Using` bloquear quando você deseja deixar o recurso disponível para outros componentes após você ter saído do `Using` bloco.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.SqlClient.SqlConnection></xref:System.Data.SqlClient.SqlConnection>   
 [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Estruturas de decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Outras estruturas de controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md)
