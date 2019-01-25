---
title: 'Como: Executar código parcialmente confiável em uma área restrita'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b33750e5792dcc83e261bc9bb8d1c5dbe35808aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627220"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Como: Executar código parcialmente confiável em uma área restrita
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Área restrita é a prática da execução do código em um ambiente de segurança restrito, o que limita as permissões de acesso concedidas ao código. Por exemplo, se você tiver uma biblioteca gerenciada de uma fonte que não confiar completamente, você não deve executá-lo como totalmente confiável. Em vez disso, você deve colocar o código em uma área restrita que limita suas permissões para aqueles que você espera que ele precisa (por exemplo, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão).  
  
 Você também pode usar a área restrita para testar o código que você distribuirá que serão executadas em ambientes parcialmente confiáveis.  
  
 Um <xref:System.AppDomain> é uma maneira eficiente de fornecer uma área restrita para aplicativos gerenciados. Domínios de aplicativo que são usados para executar código parcialmente confiável têm permissões que definem os recursos protegidos que estão disponíveis quando em execução dentro do que <xref:System.AppDomain>. Código executado dentro de <xref:System.AppDomain> vinculado, as permissões associadas a <xref:System.AppDomain> e tem permissão para acessar somente os recursos especificados. O <xref:System.AppDomain> também inclui um <xref:System.Security.Policy.StrongName> matriz que é usado para identificar os assemblies que devem ser carregados como totalmente confiável. Isso permite que o criador de um <xref:System.AppDomain> para iniciar um novo domínio em área restrita que permite que os assemblies específicos de auxiliar ser totalmente confiável. Outra opção para carregar assemblies como totalmente confiável é colocá-las no cache de assembly global; No entanto, que irá carregar assemblies como totalmente confiáveis em todos os domínios de aplicativo criados no computador em questão. A lista de alta segurança nomes dá suporte a uma por-<xref:System.AppDomain> decisão que fornece mais restritiva determinação.  
  
 Você pode usar o <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> sobrecarga de método para especificar a permissão definida para aplicativos que são executados em uma área restrita. Essa sobrecarga permite que você especifique o nível exato de segurança de acesso do código desejado. Assemblies que são carregados em um <xref:System.AppDomain> usando essa sobrecarga pode ter especificado conceder apenas o conjunto, ou pode ser totalmente confiável. O assembly é concedido confiança total, se ele estiver no cache de assembly global ou listados na `fullTrustAssemblies` (o <xref:System.Security.Policy.StrongName>) o parâmetro de matriz. Apenas os assemblies conhecidos por ser totalmente confiáveis devem ser adicionados para o `fullTrustAssemblies` lista.  
  
 A sobrecarga tem a seguinte assinatura:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Os parâmetros para o <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> sobrecarga do método especificar o nome da <xref:System.AppDomain>, a evidência para o <xref:System.AppDomain>, o <xref:System.AppDomainSetup> objeto que identifica a base do aplicativo para a área restrita, o conjunto de permissões para usar e os nomes fortes para assemblies totalmente confiáveis.  
  
 Por motivos de segurança, a base do aplicativo especificado no `info` parâmetro não deve ser a base para o aplicativo de hospedagem de aplicativo.  
  
 Para o `grantSet` parâmetro, você pode especificar um conjunto de permissões que você criou explicitamente, ou uma permissão padrão conjunto criado pelo <xref:System.Security.SecurityManager.GetStandardSandbox%2A> método.  
  
 Ao contrário da maioria <xref:System.AppDomain> carrega a evidência para o <xref:System.AppDomain> (que é fornecido pelo `securityInfo` parâmetro) não é usado para determinar o conjunto de concessões para os assemblies parcialmente confiáveis. Em vez disso, ele é especificado pelo independentemente o `grantSet` parâmetro. No entanto, a evidência pode ser usada para outras finalidades como determinar o escopo do armazenamento isolado.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Para executar um aplicativo em uma área restrita  
  
1.  Crie conjunto de permissões para ser concedido ao aplicativo não confiável. A permissão mínima, você pode conceder é <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão. Você também pode conceder permissões adicionais que você acha que podem ser seguras para código não confiável; Por exemplo, <xref:System.Security.Permissions.IsolatedStorageFilePermission>. O código a seguir cria um novo conjunto de permissões com apenas <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Como alternativa, você pode usar um conjunto de permissões nomeado existente, como a Internet.  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     O <xref:System.Security.SecurityManager.GetStandardSandbox%2A> método retorna um `Internet` conjunto de permissões ou uma `LocalIntranet` conjunto de permissões, dependendo da zona na evidência. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> também constrói as permissões de identidade para alguns dos objetos de evidência passados como referências.  
  
2.  Assinar o assembly que contém a classe de hospedagem (chamada `Sandboxer` neste exemplo) que chama o código não confiável. Adicionar o <xref:System.Security.Policy.StrongName> usado para assinar o assembly para o <xref:System.Security.Policy.StrongName> matriz da `fullTrustAssemblies` parâmetro do <xref:System.AppDomain.CreateDomain%2A> chamar. A classe de hospedagem deve ser executado como totalmente confiável para habilitar a execução do código parcialmente confiável ou para oferecer serviços para o aplicativo de confiança parcial. Isso é como você ler o <xref:System.Security.Policy.StrongName> de um assembly:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Assemblies do .NET framework, como mscorlib e System. dll não é preciso ser adicionado à lista de confiança total, porque eles são carregados como totalmente confiáveis do cache de assembly global.  
  
3.  Inicializar o <xref:System.AppDomainSetup> parâmetro do <xref:System.AppDomain.CreateDomain%2A> método. Com esse parâmetro, você pode controlar muitas das configurações do novo <xref:System.AppDomain>. O <xref:System.AppDomainSetup.ApplicationBase%2A> propriedade é uma configuração importante e deve ser diferente de <xref:System.AppDomainSetup.ApplicationBase%2A> propriedade para o <xref:System.AppDomain> do aplicativo host. Se o <xref:System.AppDomainSetup.ApplicationBase%2A> configurações são as mesmas, o aplicativo de confiança parcial pode obter a carregar (como totalmente confiável), uma exceção, ele define, explorando-a, portanto, o aplicativo de hospedagem. Essa é outra razão por que não é recomendado um catch (exception). Configurando o aplicativo base do host de maneira diferente da base de aplicativo do aplicativo em área restrita minimiza o risco de explorações.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  Chamar o <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> sobrecarga de método para criar o domínio de aplicativo usando os parâmetros que especificamos.  
  
     A assinatura para esse método é:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Informações adicionais:  
  
    -   Isso é a única sobrecarga da <xref:System.AppDomain.CreateDomain%2A> método que usa um <xref:System.Security.PermissionSet> como um parâmetro e, portanto, a única sobrecarga que permite que você carregam um aplicativo em uma configuração de confiança parcial.  
  
    -   O `evidence` parâmetro não é usado para calcular um conjunto de permissões; ele é usado para identificação por outros recursos do .NET Framework.  
  
    -   Definindo o <xref:System.AppDomainSetup.ApplicationBase%2A> propriedade do `info` o parâmetro é obrigatório para essa sobrecarga.  
  
    -   O `fullTrustAssemblies` parâmetro tem o `params` palavra-chave, o que significa que não é necessário criar um <xref:System.Security.Policy.StrongName> matriz. É permitido passar 0, 1 ou mais nomes fortes, como parâmetros.  
  
    -   O código para criar o domínio de aplicativo é:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  Carregar o código para a área restrita <xref:System.AppDomain> que você criou. Isso pode ser feito de duas maneiras:  
  
    -   Chamar o <xref:System.AppDomain.ExecuteAssembly%2A> método para o assembly.  
  
    -   Use o <xref:System.Activator.CreateInstanceFrom%2A> método para criar uma instância de uma classe derivada de <xref:System.MarshalByRefObject> no novo <xref:System.AppDomain>.  
  
     O segundo método é preferível, pois ele torna mais fácil passar parâmetros para o novo <xref:System.AppDomain> instância. O <xref:System.Activator.CreateInstanceFrom%2A> método fornece dois recursos importantes:  
  
    -   Você pode usar uma base de código que aponta para um local que não contém o assembly.  
  
    -   Você pode fazer a criação em um <xref:System.Security.CodeAccessPermission.Assert%2A> para confiança total (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), que permite que você crie uma instância de uma classe crítica. (Isso ocorre sempre que o assembly tem sem marcações de transparência e é carregado como totalmente confiável). Portanto, você precisa ter cuidado para criar somente o código que você confia com essa função, e é recomendável que você crie apenas instâncias de classes totalmente confiáveis no novo domínio de aplicativo.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Observe que, para criar uma instância de uma classe em um novo domínio, a classe tem que estender o <xref:System.MarshalByRefObject> classe  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  Desencapsular a nova instância de domínio em uma referência nesse domínio. Essa referência é usada para executar o código não confiável.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  Chame o `ExecuteUntrustedCode` método na instância da `Sandboxer` classe que você acabou de criar.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Essa chamada é executada no domínio do aplicativo em área restrita, que possui permissões restritas.  
  
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
  
     <xref:System.Reflection> é usado para obter um identificador de um método no assembly parcialmente confiável. O identificador pode ser usado para executar código em um modo seguro com permissões mínimas.  
  
     No código anterior, observe os <xref:System.Security.PermissionSet.Assert%2A> para a permissão de confiança total antes de imprimir o <xref:System.Security.SecurityException>.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     A declaração de confiança total é usada para obter informações estendidas do <xref:System.Security.SecurityException>. Sem o <xref:System.Security.PermissionSet.Assert%2A>, o <xref:System.Security.SecurityException.ToString%2A> método <xref:System.Security.SecurityException> descobrirá que há um código parcialmente confiável na pilha e restringirá as informações retornadas. Isso pode causar problemas de segurança se o código de confiança parcial foi possível ler essas informações, mas o risco é atenuado ao não conceder <xref:System.Security.Permissions.UIPermission>. A declaração de confiança total deve ser usada com moderação e somente quando você tiver certeza de que você não permitem o código de confiança parcial elevar à confiança total. Como regra, não chame código que não confiável na mesma função e depois de você chamado uma declaração de confiança total. É recomendável sempre reverter assert quando tiver terminado de usá-lo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir implementa o procedimento na seção anterior. No exemplo, um projeto chamado `Sandboxer` em um Visual Studio a solução também contém um projeto chamado `UntrustedCode`, que implementa a classe `UntrustedClass`. Este cenário pressupõe que você tenha baixado um assembly de biblioteca que contém um método que deve retornar `true` ou `false` para indicar se o número fornecido é um número de Fibonacci. Em vez disso, o método tenta ler um arquivo do seu computador. O exemplo a seguir mostra o código não confiável.  
  
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
  
 A exemplo a seguir mostra o `Sandboxer` código do aplicativo que executa o código não confiável.  
  
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
  
## <a name="see-also"></a>Consulte também
- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
