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
ms.openlocfilehash: 9634370b0031ac2e19ab5b357d7e9da5a5dcea1c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639852"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="15fd9-102">Usando o método Assert</span><span class="sxs-lookup"><span data-stu-id="15fd9-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="15fd9-103"><xref:System.Security.CodeAccessPermission.Assert%2A> é um método que pode ser chamado em classes de permissão de acesso do código e, no <xref:System.Security.PermissionSet> classe.</span><span class="sxs-lookup"><span data-stu-id="15fd9-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="15fd9-104">Você pode usar **Assert** habilitar o seu código (e chamadores downstream) executar ações que o código tem permissão para fazer, mas seus chamadores talvez não tenha permissão para fazer.</span><span class="sxs-lookup"><span data-stu-id="15fd9-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="15fd9-105">Uma asserção de segurança altera o processo normal que o tempo de execução executa durante uma verificação de segurança.</span><span class="sxs-lookup"><span data-stu-id="15fd9-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="15fd9-106">Quando você declarar uma permissão, ele informa ao sistema de segurança para não verificar os chamadores do seu código para a permissão declarada.</span><span class="sxs-lookup"><span data-stu-id="15fd9-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="15fd9-107">Use asserções com cuidado, pois eles podem abrir brechas de segurança e prejudicar o mecanismo do tempo de execução para impor restrições de segurança.</span><span class="sxs-lookup"><span data-stu-id="15fd9-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="15fd9-108">Asserções são úteis em situações em que uma biblioteca chama código não gerenciado ou faz uma chamada que requer uma permissão que obviamente não está relacionada ao uso pretendido da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="15fd9-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="15fd9-109">Por exemplo, todos os gerenciados código que chama código não gerenciado deve ter **SecurityPermission** com o **UnmanagedCode** sinalizador especificado.</span><span class="sxs-lookup"><span data-stu-id="15fd9-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="15fd9-110">Código que não se originam do computador local, como o código que é baixado da intranet local, não receberá essa permissão por padrão.</span><span class="sxs-lookup"><span data-stu-id="15fd9-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="15fd9-111">Portanto, em ordem para o código que é baixado da intranet local para ser capaz de chamar uma biblioteca que usa o código não gerenciado, ele deve ter a permissão que declarada pela biblioteca.</span><span class="sxs-lookup"><span data-stu-id="15fd9-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="15fd9-112">Além disso, algumas bibliotecas podem fazer chamadas que são invisíveis para os chamadores e exigem permissões especiais.</span><span class="sxs-lookup"><span data-stu-id="15fd9-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="15fd9-113">Você também pode usar asserções em situações em que o seu código que acessa um recurso de forma que será completamente oculto de chamadores.</span><span class="sxs-lookup"><span data-stu-id="15fd9-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="15fd9-114">Por exemplo, suponha que sua biblioteca adquire informações de um banco de dados, mas no processo também lê informações de registro do computador.</span><span class="sxs-lookup"><span data-stu-id="15fd9-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="15fd9-115">Como os desenvolvedores que usam sua biblioteca não tiver acesso à sua fonte, eles têm nenhuma maneira de saber que seu código exige **RegistryPermission** para usar seu código.</span><span class="sxs-lookup"><span data-stu-id="15fd9-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="15fd9-116">Nesse caso, se você decidir que não é razoável ou necessárias para exigir que os chamadores do seu código tem permissão para acessar o registro, você pode declarar a permissão para ler o registro.</span><span class="sxs-lookup"><span data-stu-id="15fd9-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="15fd9-117">Nessa situação, é apropriado para a biblioteca declarar a permissão de forma que os chamadores sem **RegistryPermission** pode usar a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="15fd9-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="15fd9-118">A declaração afeta a movimentação da pilha somente se a permissão declarada e uma permissão exigida por um chamador downstream são do mesmo tipo e se a permissão exigida é um subconjunto da permissão declarada.</span><span class="sxs-lookup"><span data-stu-id="15fd9-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="15fd9-119">Por exemplo, se você declarar **FileIOPermission** para ler todos os arquivos na unidade C e uma demanda downstream é feita **FileIOPermission** para ler arquivos em C:\Temp, a declaração pode afetar a movimentação da pilha; No entanto, se a demanda foi por **FileIOPermission** para gravar na unidade C, a asserção não terá efeito algum.</span><span class="sxs-lookup"><span data-stu-id="15fd9-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="15fd9-120">Para executar asserções, seu código deve ter a permissão ambos os você está declarando e o <xref:System.Security.Permissions.SecurityPermission> que representa o direito de fazer asserções.</span><span class="sxs-lookup"><span data-stu-id="15fd9-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="15fd9-121">Embora você poderia declarar uma permissão que seu código não foi concedido, a asserção seria inútil porque a verificação de segurança falharia antes que a asserção pode fazer com que ele seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="15fd9-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="15fd9-122">A ilustração a seguir mostra o que acontece quando você usa **Assert**.</span><span class="sxs-lookup"><span data-stu-id="15fd9-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="15fd9-123">Suponha que as instruções a seguir são verdadeiras sobre assemblies, A, B, C, E e F e duas permissões, P1 e P1A:</span><span class="sxs-lookup"><span data-stu-id="15fd9-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="15fd9-124">P1A representa o direito de ler arquivos. txt na unidade C.</span><span class="sxs-lookup"><span data-stu-id="15fd9-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="15fd9-125">P1 representa o direito de ler todos os arquivos na unidade C.</span><span class="sxs-lookup"><span data-stu-id="15fd9-125">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="15fd9-126">P1A e P1 são ambos **FileIOPermission** tipos e P1A é um subconjunto de P1.</span><span class="sxs-lookup"><span data-stu-id="15fd9-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="15fd9-127">Assemblies E e F concedeu permissão P1A.</span><span class="sxs-lookup"><span data-stu-id="15fd9-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="15fd9-128">O assembly C recebeu permissão de P1.</span><span class="sxs-lookup"><span data-stu-id="15fd9-128">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="15fd9-129">Assemblies A e B foram concedidos permissões nem P1 nem P1A.</span><span class="sxs-lookup"><span data-stu-id="15fd9-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="15fd9-130">Método um está contido em um assembly, o método B está contido no assembly B e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="15fd9-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagrama que mostra os assemblies de método Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 <span data-ttu-id="15fd9-132">Nesse cenário, chamadas de um método B, B chamar C, E chamadas de C, e chamadas E F. método C declara permissão para ler os arquivos na unidade C (permissão P1) e o método E exige permissão para ler arquivos. txt na unidade C (permissão P1A).</span><span class="sxs-lookup"><span data-stu-id="15fd9-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="15fd9-133">Quando a demanda em F é encontrada em tempo de execução, uma movimentação de pilha é executada para verificar as permissões de todos os chamadores de F, começando com E. E recebeu P1A permissão, portanto, a movimentação da pilha continuará para examinar as permissões de C, em que a declaração do C é descoberta.</span><span class="sxs-lookup"><span data-stu-id="15fd9-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="15fd9-134">Como a permissão exigida (P1A) é um subconjunto da permissão declarada (P1), as paradas de movimentação da pilha e a verificação de segurança automaticamente terá êxito.</span><span class="sxs-lookup"><span data-stu-id="15fd9-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="15fd9-135">Não importa que assemblies A e B não foi concedido permissão P1A.</span><span class="sxs-lookup"><span data-stu-id="15fd9-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="15fd9-136">Declarando P1, o método C garante que os chamadores podem acessar o recurso protegido pela P1, mesmo que os chamadores não recebeu permissão para acessar o recurso.</span><span class="sxs-lookup"><span data-stu-id="15fd9-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="15fd9-137">Se você criar uma biblioteca de classes e uma classe acessa um recurso protegido, você deverá, na maioria dos casos, fazer uma exigência de segurança que exigem que os chamadores da classe tem a permissão apropriada.</span><span class="sxs-lookup"><span data-stu-id="15fd9-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="15fd9-138">Se a classe, em seguida, executa uma operação para que você sabe que a maioria dos chamadores não terá permissão, e se você estiver disposto a aceitar a responsabilidade para permitir que esses chamadores chamar seu código, você pode declarar a permissão chamando o **Assert** método em um objeto de permissão que representa a operação o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="15fd9-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="15fd9-139">Usando o **Assert** dessa maneira permite que os chamadores que normalmente não pôde fazer isso chamará o seu código.</span><span class="sxs-lookup"><span data-stu-id="15fd9-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="15fd9-140">Portanto, se você declarar uma permissão, você deve ser-se de executar verificações de segurança apropriadas com antecedência para impedir que o seu componente sejam mal utilizadas.</span><span class="sxs-lookup"><span data-stu-id="15fd9-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="15fd9-141">Por exemplo, suponha que sua classe de biblioteca altamente confiável tem um método que exclui os arquivos.</span><span class="sxs-lookup"><span data-stu-id="15fd9-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="15fd9-142">Ele acessa o arquivo chamando uma função não gerenciada do Win32.</span><span class="sxs-lookup"><span data-stu-id="15fd9-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="15fd9-143">Um chamador invoca seu código **excluir** método, passando no nome do arquivo a ser excluído, c:\test.txt.</span><span class="sxs-lookup"><span data-stu-id="15fd9-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="15fd9-144">Dentro de **excluir** método, o código cria um <xref:System.Security.Permissions.FileIOPermission> objeto que representa o acesso de gravação para c:\test.txt.</span><span class="sxs-lookup"><span data-stu-id="15fd9-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="15fd9-145">(É necessário acesso de gravação para excluir um arquivo.) Seu código, em seguida, invoca uma verificação de segurança imperativa, chamando o **FileIOPermission** do objeto **demanda** método.</span><span class="sxs-lookup"><span data-stu-id="15fd9-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="15fd9-146">Se um dos chamadores na pilha de chamadas não tem essa permissão, um <xref:System.Security.SecurityException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="15fd9-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="15fd9-147">Se nenhuma exceção for lançada, você sabe que todos os chamadores têm o direito de acessar c:\test.txt.</span><span class="sxs-lookup"><span data-stu-id="15fd9-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="15fd9-148">Como você acredita que a maioria dos chamadores não terão permissão para acessar código não gerenciado, seu código, em seguida, cria uma <xref:System.Security.Permissions.SecurityPermission> objeto que representa o direito de chamar código não gerenciado e chama o objeto **Assert** método.</span><span class="sxs-lookup"><span data-stu-id="15fd9-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="15fd9-149">Por fim, ele chama a função não gerenciada do Win32 para excluir C:\Text.txt e retorna o controle ao chamador.</span><span class="sxs-lookup"><span data-stu-id="15fd9-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="15fd9-150">Você deve ter certeza de que seu código use asserções em situações em que o seu código pode ser usado por outro código para acessar um recurso protegido pela permissão que você está declarando.</span><span class="sxs-lookup"><span data-stu-id="15fd9-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="15fd9-151">Por exemplo, no código que grava em um arquivo cujo nome é especificado pelo chamador como um parâmetro, você teria não declarar o **FileIOPermission** para gravar em arquivos porque seu código deve ser aberto para uso indevido por terceiros.</span><span class="sxs-lookup"><span data-stu-id="15fd9-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="15fd9-152">Quando você usa a sintaxe de segurança imperativa, chamando o **Assert** método em várias permissões no mesmo método faz com que uma exceção de segurança seja lançada.</span><span class="sxs-lookup"><span data-stu-id="15fd9-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="15fd9-153">Em vez disso, você deve criar uma **PermissionSet** do objeto, passe a ele as permissões individuais que você deseja invocar e, em seguida, chame o **Assert** método no **PermissionSet** objeto.</span><span class="sxs-lookup"><span data-stu-id="15fd9-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="15fd9-154">Você pode chamar o **Assert** método mais do que uma vez quando você usa a sintaxe de segurança declarativa.</span><span class="sxs-lookup"><span data-stu-id="15fd9-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="15fd9-155">O exemplo a seguir mostra a sintaxe declarativa para verificações de segurança de substituição usando o **Assert** método.</span><span class="sxs-lookup"><span data-stu-id="15fd9-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="15fd9-156">Observe que o **FileIOPermissionAttribute** sintaxe usa dois valores: um <xref:System.Security.Permissions.SecurityAction> enumeração e o local do arquivo ou diretório ao qual a permissão deve ser concedida.</span><span class="sxs-lookup"><span data-stu-id="15fd9-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="15fd9-157">A chamada para **Assert** faz com que as demandas de acesso ao `C:\Log.txt` seja bem-sucedida, mesmo que os chamadores não são verificados para a permissão acessar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="15fd9-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="15fd9-158">Os fragmentos de código a seguir mostram a sintaxe imperativa para verificações de segurança de substituição usando o **Assert** método.</span><span class="sxs-lookup"><span data-stu-id="15fd9-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="15fd9-159">Neste exemplo, uma instância das **FileIOPermission** objeto for declarado.</span><span class="sxs-lookup"><span data-stu-id="15fd9-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="15fd9-160">Seu construtor é passado **FileIOPermissionAccess.AllAccess** definir o tipo de acesso permitido, seguido por uma cadeia de caracteres que descreve o local do arquivo.</span><span class="sxs-lookup"><span data-stu-id="15fd9-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="15fd9-161">Uma vez a **FileIOPermission** objeto é definido, você só precisa chamar seu **Assert** método para substituir a verificação de segurança.</span><span class="sxs-lookup"><span data-stu-id="15fd9-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15fd9-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15fd9-162">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="15fd9-163">Atributos</span><span class="sxs-lookup"><span data-stu-id="15fd9-163">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="15fd9-164">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="15fd9-164">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
