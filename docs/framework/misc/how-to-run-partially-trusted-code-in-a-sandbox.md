---
title: Como executar código parcialmente confiável em uma área restrita
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: b2f5a72e747f6c71743a7b22fe9f1962ac2f6b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181177"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Como executar código parcialmente confiável em uma área restrita
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sandboxing é a prática de executar código em um ambiente de segurança restrito, que limita as permissões de acesso concedidas ao código. Por exemplo, se você tem uma biblioteca gerenciada de uma fonte em que você não confia completamente, você não deve executá-la como totalmente confiável. Em vez disso, você deve colocar o código em uma caixa de areia que <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> limita suas permissões àqueles que você espera que ele precise (por exemplo, permissão).  
  
 Você também pode usar o sandboxing para testar o código que você estará distribuindo que será executado em ambientes parcialmente confiáveis.  
  
 Um <xref:System.AppDomain> é uma maneira eficaz de fornecer uma caixa de areia para aplicativos gerenciados. Os domínios de aplicativos usados para executar código parcialmente confiável têm permissões <xref:System.AppDomain>que definem os recursos protegidos disponíveis ao executar dentro disso . O código que <xref:System.AppDomain> é executado dentro do <xref:System.AppDomain> está vinculado às permissões associadas ao e é permitido acessar apenas os recursos especificados. O <xref:System.AppDomain> também inclui <xref:System.Security.Policy.StrongName> uma matriz que é usada para identificar conjuntos que devem ser carregados como totalmente confiáveis. Isso permite que <xref:System.AppDomain> o criador de um inicie um novo domínio sandboxed que permite que conjuntos de ajudantes específicos sejam totalmente confiáveis. Outra opção para carregar conjuntos como totalmente confiáveis é colocá-los no cache global de montagem; no entanto, isso carregará conjuntos como totalmente confiáveis em todos os domínios de aplicativos criados nesse computador. A lista de nomes fortes<xref:System.AppDomain> apoia uma decisão por decisão que fornece determinação mais restritiva.  
  
 Você pode <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> usar a sobrecarga do método para especificar o conjunto de permissões para aplicativos executados em uma caixa de areia. Essa sobrecarga permite que você especifique o nível exato de segurança de acesso ao código deseja. Os conjuntos que são <xref:System.AppDomain> carregados em um usando essa sobrecarga podem ter apenas o conjunto de subvenções especificado ou podem ser totalmente confiáveis. A montagem é concedida total confiança se estiver no `fullTrustAssemblies` cache <xref:System.Security.Policy.StrongName>de montagem global ou listada no parâmetro (a ) matriz. Apenas conjuntos conhecidos como totalmente confiáveis devem ser adicionados à `fullTrustAssemblies` lista.  
  
 A sobrecarga tem a seguinte assinatura:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Os parâmetros <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> para a sobrecarga <xref:System.AppDomain>do método especificam o nome do , a evidência para o <xref:System.AppDomain>, o <xref:System.AppDomainSetup> objeto que identifica a base de aplicativo para a caixa de areia, o conjunto de permissões para usar e os nomes fortes para assembléias totalmente confiáveis.  
  
 Por razões de segurança, a `info` base de aplicação especificada no parâmetro não deve ser a base de aplicação para o aplicativo de hospedagem.  
  
 Para `grantSet` o parâmetro, você pode especificar um conjunto de permissões que você criou <xref:System.Security.SecurityManager.GetStandardSandbox%2A> explicitamente ou um conjunto de permissões padrão criado pelo método.  
  
 Ao <xref:System.AppDomain> contrário da maioria das <xref:System.AppDomain> cargas, a evidência `securityInfo` para o (que é fornecido pelo parâmetro) não é usada para determinar o conjunto de subvenções para as assembléias parcialmente confiáveis. Em vez disso, é especificado independentemente pelo `grantSet` parâmetro. No entanto, as evidências podem ser usadas para outros fins, como determinar o escopo de armazenamento isolado.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Para executar um aplicativo em uma caixa de areia  
  
1. Crie o conjunto de permissões a ser concedido ao aplicativo não confiável. A permissão mínima <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> que você pode conceder é a permissão. Você também pode conceder permissões adicionais que você acha que podem ser seguras para código não confiável; por exemplo, <xref:System.Security.Permissions.IsolatedStorageFilePermission>. O código a seguir cria <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> um novo conjunto de permissões apenas com permissão.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternativamente, você pode usar um conjunto de permissões nomeado existente, como a Internet.  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     O <xref:System.Security.SecurityManager.GetStandardSandbox%2A> método retorna `Internet` um conjunto `LocalIntranet` de permissões ou um conjunto de permissões dependendo da região na evidência. <xref:System.Security.SecurityManager.GetStandardSandbox%2A>também constrói permissões de identidade para alguns dos objetos de evidência passados como referências.  
  
2. Assine o conjunto que contém `Sandboxer` a classe de hospedagem (nomeada neste exemplo) que chama o código não confiável. Adicione <xref:System.Security.Policy.StrongName> o usado para assinar <xref:System.Security.Policy.StrongName> a `fullTrustAssemblies` montagem à <xref:System.AppDomain.CreateDomain%2A> matriz do parâmetro da chamada. A classe de hospedagem deve ser executada como totalmente confiável para permitir a execução do código de confiança parcial ou para oferecer serviços ao aplicativo de confiança parcial. É assim que <xref:System.Security.Policy.StrongName> você lê a de uma assembléia:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     As assembléias do .NET Framework, como mscorlib e System.dll, não devem ser adicionadas à lista de confiança total porque são carregadas como totalmente confiáveis do cache de montagem global.  
  
3. Inicializar <xref:System.AppDomainSetup> o parâmetro <xref:System.AppDomain.CreateDomain%2A> do método. Com este parâmetro, você pode controlar muitas das <xref:System.AppDomain>configurações do novo . O <xref:System.AppDomainSetup.ApplicationBase%2A> imóvel é um ambiente importante, <xref:System.AppDomainSetup.ApplicationBase%2A> e deve <xref:System.AppDomain> ser diferente da propriedade para o aplicativo de hospedagem. Se <xref:System.AppDomainSetup.ApplicationBase%2A> as configurações forem as mesmas, o aplicativo de confiança parcial pode fazer com que o aplicativo de hospedagem carregue (como totalmente confiável) uma exceção que ele define, explorando-o assim. Esta é outra razão pela qual uma captura (exceção) não é recomendada. Definir a base de aplicação do host de forma diferente da base de aplicação do aplicativo sandboxa reduz o risco de explorações.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Chame <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> a sobrecarga do método para criar o domínio do aplicativo usando os parâmetros especificados.  
  
     A assinatura deste método é:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Informações adicionais:  
  
    - Esta é a única <xref:System.AppDomain.CreateDomain%2A> sobrecarga do <xref:System.Security.PermissionSet> método que toma um parâmetro e, portanto, a única sobrecarga que permite carregar um aplicativo em uma configuração de confiança parcial.  
  
    - O `evidence` parâmetro não é usado para calcular um conjunto de permissões; é usado para identificação por outras características do .NET Framework.  
  
    - Definir <xref:System.AppDomainSetup.ApplicationBase%2A> a propriedade `info` do parâmetro é obrigatório para esta sobrecarga.  
  
    - O `fullTrustAssemblies` parâmetro tem `params` a palavra-chave, o que significa <xref:System.Security.Policy.StrongName> que não é necessário criar uma matriz. Passar 0, 1 ou mais nomes fortes como parâmetros é permitido.  
  
    - O código para criar o domínio do aplicativo é:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Carregue o código no <xref:System.AppDomain> sandboxing que você criou. Isso pode ser feito de duas maneiras:  
  
    - Chame <xref:System.AppDomain.ExecuteAssembly%2A> o método para a montagem.  
  
    - Use <xref:System.Activator.CreateInstanceFrom%2A> o método para criar uma instância <xref:System.MarshalByRefObject> de <xref:System.AppDomain>uma classe derivada do novo .  
  
     O segundo método é preferível, pois facilita a <xref:System.AppDomain> passagem de parâmetros para a nova instância. O <xref:System.Activator.CreateInstanceFrom%2A> método fornece duas características importantes:  
  
    - Você pode usar uma base de código que aponta para um local que não contenha sua montagem.  
  
    - Você pode fazer a <xref:System.Security.CodeAccessPermission.Assert%2A> criação<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>um para full-trust (), que permite criar uma instância de uma classe crítica. (Isso acontece sempre que sua montagem não tem marcas de transparência e é carregada como totalmente confiável.) Portanto, você tem que ter cuidado para criar apenas o código em que você confia com essa função, e recomendamos que você crie apenas instâncias de classes totalmente confiáveis no novo domínio do aplicativo.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Observe que, para criar uma instância de uma classe em um <xref:System.MarshalByRefObject> novo domínio, a classe tem que estender a classe  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Desembrulhe a nova instância de domínio em uma referência neste domínio. Esta referência é usada para executar o código não confiável.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Chame `ExecuteUntrustedCode` o método no `Sandboxer` caso da classe que você acabou de criar.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Esta chamada é executada no domínio do aplicativo sandboxed, que tem permissões restritas.  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <xref:System.Reflection>é usado para obter uma alça de um método na montagem parcialmente confiável. O cabo pode ser usado para executar código de forma segura com permissões mínimas.  
  
     No código anterior, <xref:System.Security.PermissionSet.Assert%2A> observe a permissão para <xref:System.Security.SecurityException>a confiança total antes de imprimir o .  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     A afirmação de confiança total é <xref:System.Security.SecurityException>usada para obter informações estendidas do . Sem <xref:System.Security.PermissionSet.Assert%2A>o <xref:System.Security.SecurityException.ToString%2A> , <xref:System.Security.SecurityException> o método de descobrir que há um código parcialmente confiável na pilha e restringirá as informações devolvidas. Isso poderia causar problemas de segurança se o código de confiança parcial pudesse <xref:System.Security.Permissions.UIPermission>ler essas informações, mas o risco é mitigado pela não concessão . A afirmação de confiança total deve ser usada com moderação e somente quando você tiver certeza de que não está permitindo que o código de confiança parcial se eleve para a confiança total. Como regra geral, não chame código em que você não confia na mesma função e depois que você chamou uma afirmação para total confiança. É uma boa prática sempre reverter a afirmação quando você terminar de usá-la.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir implementa o procedimento na seção anterior. No exemplo, um `Sandboxer` projeto nomeado em uma solução `UntrustedCode`visual studio também `UntrustedClass`contém um projeto chamado , que implementa a classe . Este cenário pressupõe que você tenha baixado um conjunto `true` de `false` biblioteca contendo um método que é esperado para retornar ou para indicar se o número que você forneceu é um número de Fibonacci. Em vez disso, o método tenta ler um arquivo do seu computador. O exemplo a seguir mostra o código não confiável.  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 O exemplo a `Sandboxer` seguir mostra o código do aplicativo que executa o código não confiável.  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
