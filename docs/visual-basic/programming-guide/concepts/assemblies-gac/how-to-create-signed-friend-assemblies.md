---
title: 'Como: Criar Assemblies amigáveis assinados (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b31a359167307a58d8393e9c29e7dab1575cfdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>Como: Criar Assemblies amigáveis assinados (Visual Basic)
Este exemplo mostra como usar assemblies amigáveis com assemblies que têm nomes fortes. Os dois assemblies devem ter nomes fortes. Embora os dois assemblies neste exemplo usem as mesmas chaves, você pode usar chaves diferentes para dois assemblies.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Para criar um assembly assinado e um assembly amigável  
  
1.  Abra um prompt de comando.  
  
2.  Use a seguinte sequência de comandos com a ferramenta Nome Forte para gerar um keyfile e exibir sua chave pública. Para obter mais informações, consulte [Sn.exe (ferramenta de nome forte)][Sn.exe (ferramenta de nome forte)](../../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
    1.  Gere uma chave de nome forte para este exemplo e armazene-a no arquivo FriendAssemblies.snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Extraia a chave pública de FriendAssemblies.snk e coloque-a no FriendAssemblies.publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Exiba a chave pública armazenada no arquivo FriendAssemblies.publickey:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Crie um arquivo do Visual Basic chamado `friend_signed_A` que contém o código a seguir. O código usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para declarar friend_signed_B como um assembly autorizado.  
  
     A ferramenta Nome Forte gera uma nova chave pública sempre que for executada. Portanto, você deve substituir a chave pública no código a seguir com a chave pública que você acabou de gerar, conforme mostrado no exemplo a seguir.  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  Compile e assine o friend_signed_A usando o seguinte comando.  
  
    ```console  
    Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  Criar um arquivo do Visual Basic chamado `friend_signed_B` e contém o código a seguir. Como o friend_signed_A especifica o friend_signed_B como um assembly amigável, o código em friend_signed_B pode acessar tipos `Friend` e membros do friend_signed_A. O arquivo contém o seguinte código.  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  Compile e assine o friend_signed_B, usando o comando a seguir.  
  
    ```console  
    vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Você pode definir explicitamente o assembly usando o `-out` opção de compilador. Para obter mais informações, consulte [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
7.  Execute o arquivo friend_signed_B.exe.  
  
     O programa exibe a cadeia de caracteres "Class1.Test".  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> controla a visibilidade de membros e tipos de `Friend`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Assemblies e o cache de assembly global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Assemblies amigáveis (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Como: Criar Assemblies amigáveis não assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [-keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Sn.exe (ferramenta de nome forte)] [Sn.exe (ferramenta de nome forte)](../../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Criar e usar assemblies de nomes fortes](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)
