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
ms.openlocfilehash: ea8be23eb6fd2500e59527890b874b8f19ec06d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-assert-method"></a>Usando o método Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> é um método que pode ser chamado em classes de permissão de acesso do código e na <xref:System.Security.PermissionSet> classe. Você pode usar **Assert** permitir que seu código (e chamadores downstream) executar ações que seu código tem permissão para fazer, mas seus chamadores talvez não tenha permissão para fazer. Uma asserção de segurança altera o processo normal que o tempo de execução executa durante uma verificação de segurança. Quando você declara uma permissão, ele informa ao sistema de segurança para não verificar os chamadores do seu código para a permissão declarada.  
  
> [!CAUTION]
>  Use asserções com cuidado porque eles podem abrir vulnerabilidades de segurança e prejudicar o mecanismo de tempo de execução para impor restrições de segurança.  
  
 Declarações são úteis em situações em que uma biblioteca de chama código não gerenciado ou faz uma chamada que requer uma permissão que obviamente não está relacionada ao uso pretendido da biblioteca. Por exemplo, o código que chama o código não gerenciado deve ter todos os gerenciado **SecurityPermission** com o **UnmanagedCode** sinalizador especificado. Código que não se originam do computador local, como o código que é baixado da intranet local, não receberão essa permissão por padrão. Portanto, para o código que é baixado da intranet local para chamar uma biblioteca que usa o código não gerenciado, ele deve ter a permissão declarada pela biblioteca. Além disso, algumas bibliotecas podem fazer chamadas que são invisíveis para chamadores e exigem permissões especiais.  
  
 Você também pode usar declarações em situações em que seu código acessa um recurso de uma maneira que é completamente oculta de chamadores. Por exemplo, suponha que sua biblioteca obtém informações de um banco de dados, mas o processo também lê informações do registro do computador. Os desenvolvedores que usam a biblioteca não tem acesso à sua origem, eles têm nenhuma maneira de saber que seu código requer **RegistryPermission** para usar seu código. Nesse caso, se você decidir que não é necessário para exigir que os chamadores do seu código tem permissão para acessar o registro ou razoável, você pode declarar a permissão para ler o registro. Nessa situação, é apropriado para a biblioteca a declarar a permissão de forma que os chamadores sem **RegistryPermission** pode usar a biblioteca.  
  
 A declaração afeta a movimentação da pilha somente se a permissão declarada e uma permissão exigidos por um chamador downstream são do mesmo tipo e se a permissão de demanda é um subconjunto da permissão declarada. Por exemplo, se você declarar **FileIOPermission** para ler todos os arquivos na unidade C e uma demanda downstream é feita **FileIOPermission** para ler arquivos em C:\Temp, a declaração pode afetar a movimentação da pilha; No entanto, se a demanda foi por **FileIOPermission** para gravar na unidade C, a asserção não terá nenhum efeito.  
  
 Para executar declarações, seu código deve ter a permissão ambos está afirmando e <xref:System.Security.Permissions.SecurityPermission> que representa o direito de fazer declarações. Embora pode declarar uma permissão que não tenha sido concedido o seu código, a asserção seria sem sentido, porque a verificação de segurança falha antes da asserção pode fazer com que ele seja bem-sucedida.  
  
 A ilustração a seguir mostra o que acontece quando você usa **Assert**. Suponha que as instruções a seguir sejam verdadeiras sobre assemblies A, B, C, E e F e duas permissões, P1 e P1A:  
  
-   P1A representa o direito de ler arquivos. txt na unidade C.  
  
-   P1 representa o direito de ler todos os arquivos na unidade C.  
  
-   P1A e P1 estiverem **FileIOPermission** tipos e P1A é um subconjunto de P1.  
  
-   Assemblies E e F receberam permissão P1A.  
  
-   Assembly C foi concedida permissão de P1.  
  
-   Assemblies A e B foram concedidos permissões P1, nem P1A.  
  
-   Método um está contido no assembly A, B do método é contido em assembly B e assim por diante.  
  
 ![](../../../docs/framework/misc/media/assert.gif "Assert")  
Usar Assert  
  
 Nesse cenário, chamadas de um método B, B chamadas C, E chamadas de C, e chamadas E F. método C declara a permissão para ler os arquivos na unidade C (permissão P1) e o método E exige permissão para ler arquivos. txt na unidade C (permissão P1A). Quando a demanda em F é encontrada em tempo de execução, um exame da pilha é executado para verificar as permissões de todos os chamadores de F, começando com E. E tem permissão P1A, portanto, a movimentação da pilha continuará para examinar as permissões de C, onde a declaração do C é descoberta. Como a permissão de demanda (P1A) é um subconjunto da permissão declarada (P1), as paradas de movimentação de pilha e a verificação de segurança automaticamente terá êxito. Não importa que assemblies A e B não recebeu permissão P1A. Declarando P1, o método C garante que os chamadores podem acessar o recurso protegido pelo P1, mesmo que os chamadores não recebeu permissão para acessar o recurso.  
  
 Se você criar uma biblioteca de classes e uma classe acessa um recurso protegido, você deve, na maioria dos casos, fazer uma exigência de segurança que exigem que os chamadores da classe tem a permissão apropriada. Se a classe, em seguida, executa uma operação para que você sabe que a maioria dos chamadores não terá permissão e se você estiver disposto a aceitar a responsabilidade de permitir que esses chamadores chamar seu código, você pode declarar a permissão chamando o **Assert** método em um objeto de permissão que representa a operação de código está sendo executado. Usando **Assert** dessa maneira permite que os chamadores que normalmente não podem fazer isso chamam seu código. Portanto, se você declarar uma permissão, você deve ser execute verificações de segurança apropriadas antecipadamente para impedir que o componente que está sendo usado de forma incorreta.  
  
 Por exemplo, suponha que sua classe de biblioteca altamente confiável tem um método que exclui os arquivos. Ele acessa o arquivo chamando uma função não gerenciada do Win32. Um chamador chama seu código **excluir** método, transmitindo o nome do arquivo a ser excluído, c:\test.txt. Dentro de **excluir** método, o código cria um <xref:System.Security.Permissions.FileIOPermission> objeto representando o acesso de gravação para c:\test.txt. (O acesso de gravação é necessário para excluir um arquivo.) Seu código, em seguida, invoca uma verificação de segurança obrigatória chamando o **FileIOPermission** do objeto **demanda** método. Se um dos chamadores na pilha de chamadas não tiver essa permissão, um <xref:System.Security.SecurityException> é gerada. Se nenhuma exceção for lançada, você saberá que todos os chamadores tem o direito de acessar c:\test.txt. Porque você acredita que a maioria dos chamadores não terá permissão para acessar código não gerenciado, seu código, em seguida, cria um <xref:System.Security.Permissions.SecurityPermission> objeto que representa o direito para chamar código não gerenciado e chama o objeto **Assert** método. Finalmente, ele chama a função não gerenciada do Win32 para excluir C:\Text.txt e retorna o controle ao chamador.  
  
> [!CAUTION]
>  Você deve certificar-se de que seu código não use asserções em situações em que o seu código pode ser usado por outro código para acessar um recurso protegido, a permissão que está afirmando. Por exemplo, no código que grava em um arquivo cujo nome é especificado pelo chamador como um parâmetro, você poderia não declarar o **FileIOPermission** para gravar em arquivos porque seu código deve ser aberto para o uso indevido de terceiros.  
  
 Quando você usar a sintaxe de segurança imperativa, chamando o **Assert** método várias permissões no mesmo método faz com que uma exceção de segurança seja gerada. Em vez disso, você deve criar um **PermissionSet** de objeto, passe a ele as permissões individuais que você deseja invocar e, em seguida, chame o **Assert** método o **PermissionSet** objeto. Você pode chamar o **Assert** método mais de uma vez quando você usa a sintaxe de segurança declarativa.  
  
 O exemplo a seguir mostra a sintaxe declarativa para verificações de segurança substituindo usando o **Assert** método. Observe que o **FileIOPermissionAttribute** sintaxe assume dois valores: um <xref:System.Security.Permissions.SecurityAction> enumeração e o local do arquivo ou diretório ao qual a permissão é para ser concedida. A chamada para **Assert** faz com que solicitações de acesso para `C:\Log.txt` seja bem-sucedida, mesmo que os chamadores não são verificados para permissão para acessar o arquivo.  
  
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
  
 Os fragmentos de código a seguir mostram a sintaxe fundamental para verificações de segurança substituindo usando o **Assert** método. Neste exemplo, uma instância do **FileIOPermission** objeto for declarado. O construtor é passado **FileIOPermissionAccess.AllAccess** definir o tipo de acesso permitido, seguido por uma cadeia de caracteres que descreve o local do arquivo. Uma vez o **FileIOPermission** objeto é definido, você só precisa chamar seu **Assert** método para substituir a verificação de segurança.  
  
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
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [Atributos](../../../docs/standard/attributes/index.md)  
 [Segurança de acesso do código](../../../docs/framework/misc/code-access-security.md)
