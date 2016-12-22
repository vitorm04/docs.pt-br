---
title: "Como: Criar Assemblies amig&#225;veis assinados (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: Criar Assemblies amig&#225;veis assinados (c#)
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
  
3.  Crie um arquivo c\# chamado `friend_signed_A` que contém o código a seguir. O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo declarar friend\_signed\_B como um assembly autorizado.  
  
     A ferramenta nome forte gera uma nova chave pública sempre que ele executa. Portanto, você deve substituir a chave pública no código a seguir com a chave pública que você acabou de gerar, conforme mostrado no exemplo a seguir.  
  
    ```c#  
    // friend_signed_A.cs  
    // Compile with:   
    // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    using System.Runtime.CompilerServices;  
  
    [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
    class Class1  
    {  
        public void Test()  
        {  
            System.Console.WriteLine("Class1.Test");  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
4.  Compile e assinar friend\_signed\_A usando o comando a seguir.  
  
    ```c#  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  Crie um arquivo c\# chamado `friend_signed_B` e contém o código a seguir. Como friend\_signed\_A Especifica friend\_signed\_B como um assembly autorizado, pode acessar o código em friend\_signed\_B `internal` tipos e membros do friend\_signed\_A. O arquivo contém o código a seguir.  
  
    ```c#  
    // friend_signed_B.cs  
    // Compile with:   
    // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            Class1 inst = new Class1();  
            inst.Test();  
        }  
    }  
    ```  
  
6.  Compile e assinar friend\_signed\_B usando o comando a seguir.  
  
    ```c#  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     O nome do assembly gerado pelo compilador deve corresponder o nome do assembly autorizado passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo. Você deve especificar explicitamente o nome do assembly de saída \(.exe ou. dll\) usando o `/out` opção de compilador.  Para obter mais informações, consulte [\/out \(Set Output File Name\)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
7.  Execute o arquivo friend\_signed\_B.exe.  
  
     O programa imprime a cadeia de caracteres "Class1.Test".  
  
## Segurança do .NET Framework  
 Há semelhanças entre o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo e o <xref:System.Security.Permissions.StrongNameIdentityPermission> classe. A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo controla a visibilidade de `internal` tipos e membros.  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Assemblies e o Cache de Assembly Global \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/assemblies-and-the-global-assembly-cache.md)   
 [Assemblies amigáveis \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Como: Criar Assemblies amigáveis não assinados \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [\/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Sn.exe \(Ferramenta de Nome Forte\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)   
 [Criando e usando assemblies de nomes fortes](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)   
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)