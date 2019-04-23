---
title: Usando o método Assert
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08b46d96f9fb950602766639559a375a25747010
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073722"
---
# <a name="using-the-assert-method"></a>Usando o método Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> é um método que pode ser chamado em classes de permissão de acesso do código e, no <xref:System.Security.PermissionSet> classe. Você pode usar **Assert** habilitar o seu código (e chamadores downstream) executar ações que o código tem permissão para fazer, mas seus chamadores talvez não tenha permissão para fazer. Uma asserção de segurança altera o processo normal que o tempo de execução executa durante uma verificação de segurança. Quando você declarar uma permissão, ele informa ao sistema de segurança para não verificar os chamadores do seu código para a permissão declarada.  
  
> [!CAUTION]
>  Use asserções com cuidado, pois eles podem abrir brechas de segurança e prejudicar o mecanismo do tempo de execução para impor restrições de segurança.  
  
 Asserções são úteis em situações em que uma biblioteca chama código não gerenciado ou faz uma chamada que requer uma permissão que obviamente não está relacionada ao uso pretendido da biblioteca. Por exemplo, todos os gerenciados código que chama código não gerenciado deve ter **SecurityPermission** com o **UnmanagedCode** sinalizador especificado. Código que não se originam do computador local, como o código que é baixado da intranet local, não receberá essa permissão por padrão. Portanto, em ordem para o código que é baixado da intranet local para ser capaz de chamar uma biblioteca que usa o código não gerenciado, ele deve ter a permissão que declarada pela biblioteca. Além disso, algumas bibliotecas podem fazer chamadas que são invisíveis para os chamadores e exigem permissões especiais.  
  
 Você também pode usar asserções em situações em que o seu código que acessa um recurso de forma que será completamente oculto de chamadores. Por exemplo, suponha que sua biblioteca adquire informações de um banco de dados, mas no processo também lê informações de registro do computador. Como os desenvolvedores que usam sua biblioteca não tiver acesso à sua fonte, eles têm nenhuma maneira de saber que seu código exige **RegistryPermission** para usar seu código. Nesse caso, se você decidir que não é razoável ou necessárias para exigir que os chamadores do seu código tem permissão para acessar o registro, você pode declarar a permissão para ler o registro. Nessa situação, é apropriado para a biblioteca declarar a permissão de forma que os chamadores sem **RegistryPermission** pode usar a biblioteca.  
  
 A declaração afeta a movimentação da pilha somente se a permissão declarada e uma permissão exigida por um chamador downstream são do mesmo tipo e se a permissão exigida é um subconjunto da permissão declarada. Por exemplo, se você declarar **FileIOPermission** para ler todos os arquivos na unidade C e uma demanda downstream é feita **FileIOPermission** para ler arquivos em C:\Temp, a declaração pode afetar a movimentação da pilha; No entanto, se a demanda foi por **FileIOPermission** para gravar na unidade C, a asserção não terá efeito algum.  
  
 Para executar asserções, seu código deve ter a permissão ambos os você está declarando e o <xref:System.Security.Permissions.SecurityPermission> que representa o direito de fazer asserções. Embora você poderia declarar uma permissão que seu código não foi concedido, a asserção seria inútil porque a verificação de segurança falharia antes que a asserção pode fazer com que ele seja bem-sucedida.  
  
 A ilustração a seguir mostra o que acontece quando você usa **Assert**. Suponha que as instruções a seguir são verdadeiras sobre assemblies, A, B, C, E e F e duas permissões, P1 e P1A:  
  
-   P1A representa o direito de ler arquivos. txt na unidade C.  
  
-   P1 representa o direito de ler todos os arquivos na unidade C.  
  
-   P1A e P1 são ambos **FileIOPermission** tipos e P1A é um subconjunto de P1.  
  
-   Assemblies E e F concedeu permissão P1A.  
  
-   O assembly C recebeu permissão de P1.  
  
-   Assemblies A e B foram concedidos permissões nem P1 nem P1A.  
  
-   Método um está contido em um assembly, o método B está contido no assembly B e assim por diante.  
  
 ![Diagrama que mostra os assemblies de método Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 Nesse cenário, chamadas de um método B, B chamar C, E chamadas de C, e chamadas E F. método C declara permissão para ler os arquivos na unidade C (permissão P1) e o método E exige permissão para ler arquivos. txt na unidade C (permissão P1A). Quando a demanda em F é encontrada em tempo de execução, uma movimentação de pilha é executada para verificar as permissões de todos os chamadores de F, começando com E. E recebeu P1A permissão, portanto, a movimentação da pilha continuará para examinar as permissões de C, em que a declaração do C é descoberta. Como a permissão exigida (P1A) é um subconjunto da permissão declarada (P1), as paradas de movimentação da pilha e a verificação de segurança automaticamente terá êxito. Não importa que assemblies A e B não foi concedido permissão P1A. Declarando P1, o método C garante que os chamadores podem acessar o recurso protegido pela P1, mesmo que os chamadores não recebeu permissão para acessar o recurso.  
  
 Se você criar uma biblioteca de classes e uma classe acessa um recurso protegido, você deverá, na maioria dos casos, fazer uma exigência de segurança que exigem que os chamadores da classe tem a permissão apropriada. Se a classe, em seguida, executa uma operação para que você sabe que a maioria dos chamadores não terá permissão, e se você estiver disposto a aceitar a responsabilidade para permitir que esses chamadores chamar seu código, você pode declarar a permissão chamando o **Assert** método em um objeto de permissão que representa a operação o código está sendo executado. Usando o **Assert** dessa maneira permite que os chamadores que normalmente não pôde fazer isso chamará o seu código. Portanto, se você declarar uma permissão, você deve ser-se de executar verificações de segurança apropriadas com antecedência para impedir que o seu componente sejam mal utilizadas.  
  
 Por exemplo, suponha que sua classe de biblioteca altamente confiável tem um método que exclui os arquivos. Ele acessa o arquivo chamando uma função não gerenciada do Win32. Um chamador invoca seu código **excluir** método, passando no nome do arquivo a ser excluído, c:\test.txt. Dentro de **excluir** método, o código cria um <xref:System.Security.Permissions.FileIOPermission> objeto que representa o acesso de gravação para c:\test.txt. (É necessário acesso de gravação para excluir um arquivo.) Seu código, em seguida, invoca uma verificação de segurança imperativa, chamando o **FileIOPermission** do objeto **demanda** método. Se um dos chamadores na pilha de chamadas não tem essa permissão, um <xref:System.Security.SecurityException> é gerada. Se nenhuma exceção for lançada, você sabe que todos os chamadores têm o direito de acessar c:\test.txt. Como você acredita que a maioria dos chamadores não terão permissão para acessar código não gerenciado, seu código, em seguida, cria uma <xref:System.Security.Permissions.SecurityPermission> objeto que representa o direito de chamar código não gerenciado e chama o objeto **Assert** método. Por fim, ele chama a função não gerenciada do Win32 para excluir C:\Text.txt e retorna o controle ao chamador.  
  
> [!CAUTION]
>  Você deve ter certeza de que seu código use asserções em situações em que o seu código pode ser usado por outro código para acessar um recurso protegido pela permissão que você está declarando. Por exemplo, no código que grava em um arquivo cujo nome é especificado pelo chamador como um parâmetro, você teria não declarar o **FileIOPermission** para gravar em arquivos porque seu código deve ser aberto para uso indevido por terceiros.  
  
 Quando você usa a sintaxe de segurança imperativa, chamando o **Assert** método em várias permissões no mesmo método faz com que uma exceção de segurança seja lançada. Em vez disso, você deve criar uma **PermissionSet** do objeto, passe a ele as permissões individuais que você deseja invocar e, em seguida, chame o **Assert** método no **PermissionSet** objeto. Você pode chamar o **Assert** método mais do que uma vez quando você usa a sintaxe de segurança declarativa.  
  
 O exemplo a seguir mostra a sintaxe declarativa para verificações de segurança de substituição usando o **Assert** método. Observe que o **FileIOPermissionAttribute** sintaxe usa dois valores: um <xref:System.Security.Permissions.SecurityAction> enumeração e o local do arquivo ou diretório ao qual a permissão deve ser concedida. A chamada para **Assert** faz com que as demandas de acesso ao `C:\Log.txt` seja bem-sucedida, mesmo que os chamadores não são verificados para a permissão acessar o arquivo.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 Os fragmentos de código a seguir mostram a sintaxe imperativa para verificações de segurança de substituição usando o **Assert** método. Neste exemplo, uma instância das **FileIOPermission** objeto for declarado. Seu construtor é passado **FileIOPermissionAccess.AllAccess** definir o tipo de acesso permitido, seguido por uma cadeia de caracteres que descreve o local do arquivo. Uma vez a **FileIOPermission** objeto é definido, você só precisa chamar seu **Assert** método para substituir a verificação de segurança.  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [Atributos](../../../docs/standard/attributes/index.md)
- [Segurança de acesso do código](../../../docs/framework/misc/code-access-security.md)
