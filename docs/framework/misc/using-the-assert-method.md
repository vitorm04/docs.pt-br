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
# <a name="using-the-assert-method"></a><span data-ttu-id="f067c-102">Usando o método Assert</span><span class="sxs-lookup"><span data-stu-id="f067c-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="f067c-103"><xref:System.Security.CodeAccessPermission.Assert%2A>é um método que pode ser chamado nas <xref:System.Security.PermissionSet> classes de permissão de acesso ao código e na classe.</span><span class="sxs-lookup"><span data-stu-id="f067c-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="f067c-104">Você pode usar **o Assert** para habilitar seu código (e os chamadores a jusante) para executar ações que seu código tem permissão para fazer, mas seus chamadores podem não ter permissão para fazer.</span><span class="sxs-lookup"><span data-stu-id="f067c-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="f067c-105">Uma afirmação de segurança altera o processo normal que o tempo de execução executa durante uma verificação de segurança.</span><span class="sxs-lookup"><span data-stu-id="f067c-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="f067c-106">Quando você afirma uma permissão, ele diz ao sistema de segurança para não verificar os chamadores do seu código para obter a permissão afirmada.</span><span class="sxs-lookup"><span data-stu-id="f067c-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f067c-107">Use as afirmações com cuidado porque elas podem abrir falhas de segurança e minar o mecanismo do tempo de execução para impor restrições de segurança.</span><span class="sxs-lookup"><span data-stu-id="f067c-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="f067c-108">As afirmações são úteis em situações em que uma biblioteca liga para código não gerenciado ou faz uma chamada que requer uma permissão que não está obviamente relacionada com o uso pretendido da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="f067c-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="f067c-109">Por exemplo, todo o código gerenciado que chamadas em código não gerenciado deve ter **a Permissão de Segurança** com o sinalizador Não **gerenciadoCódigo** especificado.</span><span class="sxs-lookup"><span data-stu-id="f067c-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="f067c-110">Código que não se origina do computador local, como código que é baixado da intranet local, não será concedido essa permissão por padrão.</span><span class="sxs-lookup"><span data-stu-id="f067c-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="f067c-111">Portanto, para que o código que é baixado da intranet local seja capaz de chamar uma biblioteca que usa código não gerenciado, ele deve ter a permissão afirmada pela biblioteca.</span><span class="sxs-lookup"><span data-stu-id="f067c-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="f067c-112">Além disso, algumas bibliotecas podem fazer chamadas que não são vistas para os chamadores e exigem permissões especiais.</span><span class="sxs-lookup"><span data-stu-id="f067c-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="f067c-113">Você também pode usar afirmações em situações em que seu código acessa um recurso de uma maneira completamente oculta dos chamadores.</span><span class="sxs-lookup"><span data-stu-id="f067c-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="f067c-114">Por exemplo, suponha que sua biblioteca adquire informações de um banco de dados, mas no processo também lê informações do registro do computador.</span><span class="sxs-lookup"><span data-stu-id="f067c-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="f067c-115">Como os desenvolvedores que usam sua biblioteca não têm acesso à sua fonte, eles não têm como saber que seu código requer **Permissão de Registro** para usar seu código.</span><span class="sxs-lookup"><span data-stu-id="f067c-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="f067c-116">Neste caso, se você decidir que não é razoável ou necessário exigir que os chamadores do seu código tenham permissão para acessar o registro, você pode afirmar permissão para ler o registro.</span><span class="sxs-lookup"><span data-stu-id="f067c-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="f067c-117">Nesta situação, é apropriado que a biblioteca faça valer a permissão para que os chamadores sem **Autorização de Registro** possam usar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="f067c-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="f067c-118">A afirmação afeta a caminhada de pilha somente se a permissão afirmada e uma permissão exigida por um chamador a jusante forem do mesmo tipo e se a permissão exigida for um subconjunto da permissão afirmada.</span><span class="sxs-lookup"><span data-stu-id="f067c-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="f067c-119">Por exemplo, se você afirmar **FileIOPermission** para ler todos os arquivos na unidade C e uma demanda a jusante for feita para **fileIOPermission** para ler arquivos em C:\Temp, a afirmação pode afetar a caminhada de pilha; no entanto, se a demanda fosse por **FileIOPermission** para escrever para a unidade C, a afirmação não teria efeito.</span><span class="sxs-lookup"><span data-stu-id="f067c-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="f067c-120">Para realizar afirmações, seu código deve ser concedido tanto <xref:System.Security.Permissions.SecurityPermission> a permissão que você está afirmando quanto o que representa o direito de fazer afirmações.</span><span class="sxs-lookup"><span data-stu-id="f067c-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="f067c-121">Embora você pudesse afirmar uma permissão que seu código não foi concedido, a afirmação seria inútil porque a verificação de segurança falharia antes que a afirmação pudesse fazer com que ele tivesse sucesso.</span><span class="sxs-lookup"><span data-stu-id="f067c-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="f067c-122">A ilustração a seguir mostra o que acontece quando você usa **O Assert**.</span><span class="sxs-lookup"><span data-stu-id="f067c-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="f067c-123">Assuma que as seguintes afirmações são verdadeiras sobre as assembléias A, B, C, E e F, e duas permissões, P1 e P1A:</span><span class="sxs-lookup"><span data-stu-id="f067c-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="f067c-124">P1A representa o direito de ler arquivos .txt na unidade C.</span><span class="sxs-lookup"><span data-stu-id="f067c-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="f067c-125">P1 representa o direito de ler todos os arquivos na unidade C.</span><span class="sxs-lookup"><span data-stu-id="f067c-125">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="f067c-126">P1A e P1 são tipos **de FileIOPermission,** e P1A é um subconjunto de P1.</span><span class="sxs-lookup"><span data-stu-id="f067c-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="f067c-127">As assembléias E e F receberam permissão P1A.</span><span class="sxs-lookup"><span data-stu-id="f067c-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="f067c-128">A Assembléia C recebeu permissão P1.</span><span class="sxs-lookup"><span data-stu-id="f067c-128">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="f067c-129">As assembléias A e B não receberam permissões P1 nem P1A.</span><span class="sxs-lookup"><span data-stu-id="f067c-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="f067c-130">O método A está contido na montagem A, o método B está contido na montagem B, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f067c-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagrama que mostra os conjuntos do método Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="f067c-132">Neste cenário, o método A chama B, B chama C, C chama E e E chama F. O método C afirma permissão para ler arquivos na unidade C (permissão P1), e o método E exige permissão para ler arquivos .txt na unidade C (permissão P1A).</span><span class="sxs-lookup"><span data-stu-id="f067c-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="f067c-133">Quando a demanda em F é encontrada no tempo de execução, uma caminhada de pilha é realizada para verificar as permissões de todos os chamadores de F, começando com E. E foi concedida permissão P1A, de modo que a caminhada de pilha prossegue para examinar as permissões de C, onde a afirmação de C é descoberta.</span><span class="sxs-lookup"><span data-stu-id="f067c-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="f067c-134">Como a permissão exigida (P1A) é um subconjunto da permissão afirmada (P1), a pilha de caminhada pára e a verificação de segurança é automaticamente bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="f067c-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="f067c-135">Não importa que as assembléias A e B não tenham sido concedidas permissão P1A.</span><span class="sxs-lookup"><span data-stu-id="f067c-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="f067c-136">Ao afirmar P1, o método C garante que seus chamadores possam acessar o recurso protegido por P1, mesmo que os chamadores não tenham recebido permissão para acessar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="f067c-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="f067c-137">Se você projetar uma biblioteca de classe e uma classe acessar um recurso protegido, você deve, na maioria dos casos, fazer uma demanda de segurança exigindo que os chamadores da classe tenham a permissão apropriada.</span><span class="sxs-lookup"><span data-stu-id="f067c-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="f067c-138">Se a classe realizar uma operação para a qual você sabe que a maioria de seus chamadores não terá permissão, e se você estiver disposto a assumir a responsabilidade de deixar esses chamadores chamarem seu código, você pode afirmar a permissão ligando para o método **Assert** em um objeto de permissão que representa a operação que o código está executando.</span><span class="sxs-lookup"><span data-stu-id="f067c-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="f067c-139">Usar **o Assert** desta forma permite que os chamadores que normalmente não poderiam fazê-lo chamem seu código.</span><span class="sxs-lookup"><span data-stu-id="f067c-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="f067c-140">Portanto, se você afirmar uma permissão, você deve ter certeza de realizar verificações de segurança apropriadas com antecedência para evitar que seu componente seja usado indevidamente.</span><span class="sxs-lookup"><span data-stu-id="f067c-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="f067c-141">Por exemplo, suponha que sua classe de biblioteca altamente confiável tenha um método que exclui arquivos.</span><span class="sxs-lookup"><span data-stu-id="f067c-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="f067c-142">Ele acessa o arquivo chamando uma função Win32 não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="f067c-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="f067c-143">Um chamador invoca o método **Excluir** do seu código, passando o nome do arquivo a ser excluído, C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="f067c-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="f067c-144">Dentro do método **Excluir,** <xref:System.Security.Permissions.FileIOPermission> seu código cria um objeto representando o acesso à gravação de C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="f067c-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="f067c-145">(O acesso à gravação é necessário para excluir um arquivo.) Em seguida, seu código invoca uma verificação de segurança imperativa, chamando o método **de Demanda** do objeto **FileIOPermission.**</span><span class="sxs-lookup"><span data-stu-id="f067c-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="f067c-146">Se um dos chamadores na pilha de chamadas <xref:System.Security.SecurityException> não tiver essa permissão, um será acionado.</span><span class="sxs-lookup"><span data-stu-id="f067c-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="f067c-147">Se nenhuma exceção for lançada, você sabe que todos os chamadores têm o direito de acessar C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="f067c-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="f067c-148">Como você acredita que a maioria dos seus chamadores não terá permissão para acessar código não gerenciado, seu código então cria um <xref:System.Security.Permissions.SecurityPermission> objeto que representa o direito de chamar código não gerenciado e chama o método **Assert** do objeto.</span><span class="sxs-lookup"><span data-stu-id="f067c-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="f067c-149">Finalmente, ele chama a função Win32 não gerenciada para excluir C:\Text.txt e retorna o controle ao chamador.</span><span class="sxs-lookup"><span data-stu-id="f067c-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f067c-150">Você deve ter certeza de que seu código não usa afirmações em situações onde seu código pode ser usado por outro código para acessar um recurso protegido pela permissão que você está afirmando.</span><span class="sxs-lookup"><span data-stu-id="f067c-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="f067c-151">Por exemplo, no código que grava em um arquivo cujo nome é especificado pelo chamador como parâmetro, você não afirmaria a **FileIOPermission** para escrever em arquivos porque seu código estaria aberto a uso indevido por terceiros.</span><span class="sxs-lookup"><span data-stu-id="f067c-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="f067c-152">Quando você usa a sintaxe de segurança imperativa, chamar o método **Assert** sobre várias permissões no mesmo método faz com que uma exceção de segurança seja lançada.</span><span class="sxs-lookup"><span data-stu-id="f067c-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="f067c-153">Em vez disso, você deve criar um objeto **PermissionSet,** passar-lhe as permissões individuais que deseja invocar e, em seguida, chamar o método **Assert** no objeto **PermissionSet.**</span><span class="sxs-lookup"><span data-stu-id="f067c-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="f067c-154">Você pode chamar o método **Assert** mais de uma vez quando você usar a sintaxe declarativa de segurança.</span><span class="sxs-lookup"><span data-stu-id="f067c-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="f067c-155">O exemplo a seguir mostra sintaxe declarativa para sobrepor verificações de segurança usando o método **Assert.**</span><span class="sxs-lookup"><span data-stu-id="f067c-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="f067c-156">Observe que a sintaxe **FileIOPermissionAttribute** leva dois valores: uma <xref:System.Security.Permissions.SecurityAction> enumeração e a localização do arquivo ou diretório ao qual a permissão deve ser concedida.</span><span class="sxs-lookup"><span data-stu-id="f067c-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="f067c-157">A chamada para **a** Assert `C:\Log.txt` faz com que as exigências de acesso sejam bem sucedidas, embora os chamadores não sejam verificados quanto à permissão para acessar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="f067c-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="f067c-158">Os fragmentos de código a seguir mostram sintaxe imperativa para sobrepor verificações de segurança usando o método **Assert.**</span><span class="sxs-lookup"><span data-stu-id="f067c-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="f067c-159">Neste exemplo, uma instância do objeto **FileIOPermission** é declarada.</span><span class="sxs-lookup"><span data-stu-id="f067c-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="f067c-160">Seu construtor é aprovado **FileIOPermissionAccess.AllAccess** para definir o tipo de acesso permitido, seguido por uma seqüência descrevendo a localização do arquivo.</span><span class="sxs-lookup"><span data-stu-id="f067c-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="f067c-161">Uma vez definido o objeto **FileIOPermission,** você só precisa chamar seu método **Assert** para substituir a verificação de segurança.</span><span class="sxs-lookup"><span data-stu-id="f067c-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f067c-162">Confira também</span><span class="sxs-lookup"><span data-stu-id="f067c-162">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="f067c-163">Atributos</span><span class="sxs-lookup"><span data-stu-id="f067c-163">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="f067c-164">Segurança de acesso a código</span><span class="sxs-lookup"><span data-stu-id="f067c-164">Code Access Security</span></span>](code-access-security.md)
