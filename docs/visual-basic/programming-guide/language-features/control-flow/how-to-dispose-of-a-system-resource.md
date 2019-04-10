---
title: 'Como: Descartar um recurso do sistema (Visual Basic)'
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
ms.openlocfilehash: e3594db036edc3a6288b0373737c1ee26a691a57
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341901"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Como: Descartar um recurso do sistema (Visual Basic)
Você pode usar um `Using` bloco para garantir que o sistema de descarte de um recurso quando seu código sai do bloco. Isso é útil se você estiver usando um recurso do sistema que consome uma grande quantidade de memória ou outros componentes também desejam usar.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Para descartar uma conexão de banco de dados quando seu código for concluído com ele  
  
1. Certifique-se de incluir apropriado [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para a conexão de banco de dados no início de seu arquivo de origem (nesse caso, <xref:System.Data.SqlClient>).  
  
2. Criar uma `Using` bloco com o `Using` e `End Using` instruções. Dentro do bloco, coloque o código que lida com a conexão de banco de dados.  
  
3. A conexão de declarar e criar uma instância dela como parte do `Using` instrução.  
  
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
  
     Observe que você não pode acessar `sqc` de fora a `Using` bloquear, porque seu escopo é limitado ao bloco.  
  
     Você pode usar essa mesma técnica em um recurso do sistema como um identificador de arquivo ou um wrapper COM. Você usa um `Using` bloquear quando você deseja deixar o recurso disponível para outros componentes após você ter saído do `Using` bloco.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.SqlClient.SqlConnection>
- [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de decisão](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Outras estruturas de controle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Estruturas de controle aninhadas](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md)
