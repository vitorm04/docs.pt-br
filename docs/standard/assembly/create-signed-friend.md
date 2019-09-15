---
title: 'Como: Criar assemblies Friend assinados'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 19c301c6b96e1070447401af9105fba2e0f0837f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973358"
---
# <a name="how-to-create-signed-friend-assemblies"></a>Como: Criar assemblies Friend assinados
Este exemplo mostra como usar assemblies amigáveis com assemblies que têm nomes fortes. Os dois assemblies devem ter nomes fortes. Embora os dois assemblies neste exemplo usem as mesmas chaves, você pode usar chaves diferentes para dois assemblies.  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a>Criar um assembly assinado e um assembly Friend  
  
1. Abra um prompt de comando.  
  
2. Use a seguinte sequência de comandos com a ferramenta Nome Forte para gerar um keyfile e exibir sua chave pública. Para obter mais informações, consulte [sn. exe (Strong Name Tool)](../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Gere uma chave de nome forte para este exemplo e armazene-a no arquivo *FriendAssemblies. SNK*:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Extraia a chave pública de *FriendAssemblies. SNK* e coloque-a em *FriendAssemblies. PublicKey*:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. Exiba a chave pública armazenada no arquivo *FriendAssemblies. PublicKey*:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Crie um C# arquivo ou Visual Basic chamado *friend_signed_A* que contém o código a seguir. O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo para declarar *friend_signed_B* como um assembly Friend.  
   
   A ferramenta Nome Forte gera uma nova chave pública sempre que for executada. Portanto, você deve substituir a chave pública no código a seguir com a chave pública que você acabou de gerar, conforme mostrado no exemplo a seguir.  
   
   ```csharp  
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
   
4. Compile e assine o *friend_signed_A* usando o comando a seguir.  
   
   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  
   
   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  
   
5. Crie um C# arquivo ou Visual Basic chamado *friend_signed_B* que contém o código a seguir. Como *friend_signed_A* especifica *friend_signed_B* como um assembly Friend, o código em *friend_signed_B* pode acessar `internal` osC#tipos e `Friend` Membros () ou (Visual Basic) de *friend_signed_A*. O arquivo contém o seguinte código.  
   
   ```csharp  
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
   
6. Compile e assine o *friend_signed_B* usando o comando a seguir.  
   
   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  
   
   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  
   
   O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Você deve especificar explicitamente o nome do assembly de saída ( *. exe* ou *. dll*) usando a opção `/out` do compilador. Para obter mais informações, consulte [/outC# (opções do compilador)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).  
   
7. Execute o arquivo *friend_signed_B. exe* .  
   
   O programa gera a cadeia de caracteres **Class1. Test**.  
  
## <a name="net-security"></a>Segurança do .NET  
 Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> o pode exigir permissões de segurança para executar uma determinada seção de código, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> enquanto o atributo controla a `internal` visibilidadeC#de tipos `Friend` e Membros () ou (Visual Basic).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Assemblies no .NET](index.md)
- [Assemblies Friend](friend.md)
- [Como: Criar assemblies Friend não assinados](create-unsigned-friend.md)
- [/keyfile (C#)](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [-keyfile (Visual Basic)](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn. exe (ferramenta Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Criar e usar assemblies de nome forte](create-use-strong-named.md)
- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de programação (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
