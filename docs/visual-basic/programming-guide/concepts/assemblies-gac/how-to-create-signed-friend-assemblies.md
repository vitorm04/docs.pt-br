---
title: "Como: Criar Assemblies amig&#225;veis assinados (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: Criar Assemblies amig&#225;veis assinados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como usar assemblies amigáveis com assemblies com nomes fortes. Os dois assemblies devem ser nomeadas forte. Embora os dois assemblies neste exemplo usam as mesmas chaves, você pode usar chaves diferentes para dois assemblies.  
  
### Para criar um assembly assinado e um conjunto de módulos de amigo  
  
1.  Abra um prompt de comando.  
  
2.  Use a seguinte sequência de comandos com a ferramenta nome forte para gerar um arquivo de chaves e exibir sua chave pública. Para obter mais informações, consulte [Sn.exe \(Ferramenta de Nome Forte\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
    1.  Gerar uma chave de nome forte para este exemplo e armazená\-lo no arquivo FriendAssemblies.snk:  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Extrair a chave pública de FriendAssemblies.snk e colocá\-lo em FriendAssemblies.publickey:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Exiba a chave pública armazenada no arquivo FriendAssemblies.publickey:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Crie um arquivo do Visual Basic chamado `friend_signed_A` que contém o código a seguir. O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo declarar friend\_signed\_B como um assembly autorizado.  
  
     A ferramenta nome forte gera uma nova chave pública sempre que ele executa. Portanto, você deve substituir a chave pública no código a seguir com a chave pública que você acabou de gerar, conforme mostrado no exemplo a seguir.  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  Compile e assinar friend\_signed\_A usando o comando a seguir.  
  
    ```vb#  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  Criar um arquivo do Visual Basic chamado `friend_signed_B` e contém o código a seguir. Como friend\_signed\_A Especifica friend\_signed\_B como um assembly autorizado, pode acessar o código em friend\_signed\_B `Friend` tipos e membros do friend\_signed\_A. O arquivo contém o código a seguir.  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  Compile e assinar friend\_signed\_B usando o comando a seguir.  
  
    ```vb#  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     O nome do assembly gerado pelo compilador deve corresponder o nome do assembly autorizado passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo. Você pode definir explicitamente o assembly usando o `/out` opção de compilador. Para obter mais informações, consulte [\/out](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
7.  Execute o arquivo friend\_signed\_B.exe.  
  
     O programa imprime a cadeia de caracteres "Class1.Test".  
  
## Segurança do .NET Framework  
 Há semelhanças entre o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo e o <xref:System.Security.Permissions.StrongNameIdentityPermission> classe. A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo controla a visibilidade de `Friend` tipos e membros.  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Assemblies e o Cache de Assembly Global \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Assemblies amigáveis \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Como: Criar Assemblies amigáveis não assinados \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [\/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Sn.exe \(Ferramenta de Nome Forte\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)   
 [Criando e usando assemblies de nomes fortes](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)   
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)