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
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181098"
---
# <a name="using-the-assert-method"></a>Usando o método Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>é um método que pode ser chamado nas <xref:System.Security.PermissionSet> classes de permissão de acesso ao código e na classe. Você pode usar **o Assert** para habilitar seu código (e os chamadores a jusante) para executar ações que seu código tem permissão para fazer, mas seus chamadores podem não ter permissão para fazer. Uma afirmação de segurança altera o processo normal que o tempo de execução executa durante uma verificação de segurança. Quando você afirma uma permissão, ele diz ao sistema de segurança para não verificar os chamadores do seu código para obter a permissão afirmada.  
  
> [!CAUTION]
> Use as afirmações com cuidado porque elas podem abrir falhas de segurança e minar o mecanismo do tempo de execução para impor restrições de segurança.  
  
 As afirmações são úteis em situações em que uma biblioteca liga para código não gerenciado ou faz uma chamada que requer uma permissão que não está obviamente relacionada com o uso pretendido da biblioteca. Por exemplo, todo o código gerenciado que chamadas em código não gerenciado deve ter **a Permissão de Segurança** com o sinalizador Não **gerenciadoCódigo** especificado. Código que não se origina do computador local, como código que é baixado da intranet local, não será concedido essa permissão por padrão. Portanto, para que o código que é baixado da intranet local seja capaz de chamar uma biblioteca que usa código não gerenciado, ele deve ter a permissão afirmada pela biblioteca. Além disso, algumas bibliotecas podem fazer chamadas que não são vistas para os chamadores e exigem permissões especiais.  
  
 Você também pode usar afirmações em situações em que seu código acessa um recurso de uma maneira completamente oculta dos chamadores. Por exemplo, suponha que sua biblioteca adquire informações de um banco de dados, mas no processo também lê informações do registro do computador. Como os desenvolvedores que usam sua biblioteca não têm acesso à sua fonte, eles não têm como saber que seu código requer **Permissão de Registro** para usar seu código. Neste caso, se você decidir que não é razoável ou necessário exigir que os chamadores do seu código tenham permissão para acessar o registro, você pode afirmar permissão para ler o registro. Nesta situação, é apropriado que a biblioteca faça valer a permissão para que os chamadores sem **Autorização de Registro** possam usar a biblioteca.  
  
 A afirmação afeta a caminhada de pilha somente se a permissão afirmada e uma permissão exigida por um chamador a jusante forem do mesmo tipo e se a permissão exigida for um subconjunto da permissão afirmada. Por exemplo, se você afirmar **FileIOPermission** para ler todos os arquivos na unidade C e uma demanda a jusante for feita para **fileIOPermission** para ler arquivos em C:\Temp, a afirmação pode afetar a caminhada de pilha; no entanto, se a demanda fosse por **FileIOPermission** para escrever para a unidade C, a afirmação não teria efeito.  
  
 Para realizar afirmações, seu código deve ser concedido tanto <xref:System.Security.Permissions.SecurityPermission> a permissão que você está afirmando quanto o que representa o direito de fazer afirmações. Embora você pudesse afirmar uma permissão que seu código não foi concedido, a afirmação seria inútil porque a verificação de segurança falharia antes que a afirmação pudesse fazer com que ele tivesse sucesso.  
  
 A ilustração a seguir mostra o que acontece quando você usa **O Assert**. Assuma que as seguintes afirmações são verdadeiras sobre as assembléias A, B, C, E e F, e duas permissões, P1 e P1A:  
  
- P1A representa o direito de ler arquivos .txt na unidade C.  
  
- P1 representa o direito de ler todos os arquivos na unidade C.  
  
- P1A e P1 são tipos **de FileIOPermission,** e P1A é um subconjunto de P1.  
  
- As assembléias E e F receberam permissão P1A.  
  
- A Assembléia C recebeu permissão P1.  
  
- As assembléias A e B não receberam permissões P1 nem P1A.  
  
- O método A está contido na montagem A, o método B está contido na montagem B, e assim por diante.  
  
 ![Diagrama que mostra os conjuntos do método Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 Neste cenário, o método A chama B, B chama C, C chama E e E chama F. O método C afirma permissão para ler arquivos na unidade C (permissão P1), e o método E exige permissão para ler arquivos .txt na unidade C (permissão P1A). Quando a demanda em F é encontrada no tempo de execução, uma caminhada de pilha é realizada para verificar as permissões de todos os chamadores de F, começando com E. E foi concedida permissão P1A, de modo que a caminhada de pilha prossegue para examinar as permissões de C, onde a afirmação de C é descoberta. Como a permissão exigida (P1A) é um subconjunto da permissão afirmada (P1), a pilha de caminhada pára e a verificação de segurança é automaticamente bem sucedida. Não importa que as assembléias A e B não tenham sido concedidas permissão P1A. Ao afirmar P1, o método C garante que seus chamadores possam acessar o recurso protegido por P1, mesmo que os chamadores não tenham recebido permissão para acessar esse recurso.  
  
 Se você projetar uma biblioteca de classe e uma classe acessar um recurso protegido, você deve, na maioria dos casos, fazer uma demanda de segurança exigindo que os chamadores da classe tenham a permissão apropriada. Se a classe realizar uma operação para a qual você sabe que a maioria de seus chamadores não terá permissão, e se você estiver disposto a assumir a responsabilidade de deixar esses chamadores chamarem seu código, você pode afirmar a permissão ligando para o método **Assert** em um objeto de permissão que representa a operação que o código está executando. Usar **o Assert** desta forma permite que os chamadores que normalmente não poderiam fazê-lo chamem seu código. Portanto, se você afirmar uma permissão, você deve ter certeza de realizar verificações de segurança apropriadas com antecedência para evitar que seu componente seja usado indevidamente.  
  
 Por exemplo, suponha que sua classe de biblioteca altamente confiável tenha um método que exclui arquivos. Ele acessa o arquivo chamando uma função Win32 não gerenciada. Um chamador invoca o método **Excluir** do seu código, passando o nome do arquivo a ser excluído, C:\Test.txt. Dentro do método **Excluir,** <xref:System.Security.Permissions.FileIOPermission> seu código cria um objeto representando o acesso à gravação de C:\Test.txt. (O acesso à gravação é necessário para excluir um arquivo.) Em seguida, seu código invoca uma verificação de segurança imperativa, chamando o método **de Demanda** do objeto **FileIOPermission.** Se um dos chamadores na pilha de chamadas <xref:System.Security.SecurityException> não tiver essa permissão, um será acionado. Se nenhuma exceção for lançada, você sabe que todos os chamadores têm o direito de acessar C:\Test.txt. Como você acredita que a maioria dos seus chamadores não terá permissão para acessar código não gerenciado, seu código então cria um <xref:System.Security.Permissions.SecurityPermission> objeto que representa o direito de chamar código não gerenciado e chama o método **Assert** do objeto. Finalmente, ele chama a função Win32 não gerenciada para excluir C:\Text.txt e retorna o controle ao chamador.  
  
> [!CAUTION]
> Você deve ter certeza de que seu código não usa afirmações em situações onde seu código pode ser usado por outro código para acessar um recurso protegido pela permissão que você está afirmando. Por exemplo, no código que grava em um arquivo cujo nome é especificado pelo chamador como parâmetro, você não afirmaria a **FileIOPermission** para escrever em arquivos porque seu código estaria aberto a uso indevido por terceiros.  
  
 Quando você usa a sintaxe de segurança imperativa, chamar o método **Assert** sobre várias permissões no mesmo método faz com que uma exceção de segurança seja lançada. Em vez disso, você deve criar um objeto **PermissionSet,** passar-lhe as permissões individuais que deseja invocar e, em seguida, chamar o método **Assert** no objeto **PermissionSet.** Você pode chamar o método **Assert** mais de uma vez quando você usar a sintaxe declarativa de segurança.  
  
 O exemplo a seguir mostra sintaxe declarativa para sobrepor verificações de segurança usando o método **Assert.** Observe que a sintaxe **FileIOPermissionAttribute** leva dois valores: uma <xref:System.Security.Permissions.SecurityAction> enumeração e a localização do arquivo ou diretório ao qual a permissão deve ser concedida. A chamada para **a** Assert `C:\Log.txt` faz com que as exigências de acesso sejam bem sucedidas, embora os chamadores não sejam verificados quanto à permissão para acessar o arquivo.  
  
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
  
 Os fragmentos de código a seguir mostram sintaxe imperativa para sobrepor verificações de segurança usando o método **Assert.** Neste exemplo, uma instância do objeto **FileIOPermission** é declarada. Seu construtor é aprovado **FileIOPermissionAccess.AllAccess** para definir o tipo de acesso permitido, seguido por uma seqüência descrevendo a localização do arquivo. Uma vez definido o objeto **FileIOPermission,** você só precisa chamar seu método **Assert** para substituir a verificação de segurança.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [Atributos](../../standard/attributes/index.md)
- [Segurança de acesso a código](code-access-security.md)
