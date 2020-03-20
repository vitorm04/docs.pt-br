---
title: Representando o cliente
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 10a8d243b3f053879f183864e955d9260c07865b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183605"
---
# <a name="impersonating-the-client"></a>Representando o cliente
A amostra de personificação demonstra como se passar pelo aplicativo de chamada no serviço para que o serviço possa acessar os recursos do sistema em nome do chamador.  
  
 Esta amostra é baseada na amostra [self-host.](../../../../docs/framework/wcf/samples/self-host.md) Os arquivos de configuração de serviço e cliente são os mesmos da amostra [Self-Host.](../../../../docs/framework/wcf/samples/self-host.md)  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 O código de serviço foi `Add` modificado de modo que o <xref:System.ServiceModel.OperationBehaviorAttribute> método no serviço se passa pelo chamador usando o conforme mostrado no código de amostra a seguir.  
  
```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 Como resultado, o contexto de segurança do segmento de execução `Add` é alterado para se passar pelo chamador antes de inserir o método e revertido ao sair do método.  
  
 O `DisplayIdentityInformation` método mostrado no código de amostra a seguir é uma função de utilidade que exibe a identidade do chamador.  
  
```csharp
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 O `Subtract` método no serviço personifica o chamador usando chamadas imperativas, conforme mostrado no código de amostra a seguir.  
  
```csharp
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    Console.WriteLine("Before impersonating");  
    DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs
            // on the system resource are enforced in the caller's context.
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
    Console.WriteLine("After reverting");  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 Observe que, neste caso, o chamador não é personificado para toda a chamada, mas é apenas personificado por uma parte da chamada. Em geral, representar-se para o menor escopo é preferível se passar por toda a operação.  
  
 Os outros métodos não se passam pelo interlocutor.  
  
 O código do cliente foi modificado para <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>definir o nível de representação para . O cliente especifica o nível de personificação a ser <xref:System.Security.Principal.TokenImpersonationLevel> usado pelo serviço, usando a enumeração. A enumeração suporta os <xref:System.Security.Principal.TokenImpersonationLevel.None>seguintes <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> valores: , <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, e <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Para realizar uma verificação de acesso ao acessar um recurso do sistema na máquina local que está <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>protegido usando ACLs do Windows, o nível de representação deve ser definido para , como mostrado no código de amostra a seguir.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas nas janelas do serviço e do console cliente. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
> [!NOTE]
> O serviço deve ser executado uma conta administrativa ou a `http://localhost:8000/ServiceModelSamples` conta a que ele é executado deve ser concedido o direito de registrar o URI com a camada HTTP. Esses direitos podem ser concedidos configurando uma [Reserva de Namespace](/windows/win32/http/namespace-reservations-registrations-and-routing) usando a [ferramenta Httpcfg.exe](/windows/win32/http/httpcfg-exe).  
  
> [!NOTE]
> Nos computadores que executam o Windows Server 2003, a representação só é suportada se o aplicativo Host.exe tiver o privilégio de personificação. (Por padrão, apenas os administradores têm essa permissão.) Para adicionar esse privilégio a uma conta que o serviço está executando, vá para **Ferramentas Administrativas,** abra **a Política de Segurança Local,** abra **políticas locais,** clique em **Atribuição de Direitos do Usuário**e **selecione Personificar um Cliente após autenticação** e clique duas vezes **em Propriedades** para adicionar um usuário ou grupo.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Para demonstrar que o serviço se passa pelo chamador, execute o cliente em uma conta diferente da que o serviço está executando. Para isso, no prompt de comando, digite:  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Em seguida, você é solicitado para uma senha. Digite a senha da conta que você especificou anteriormente.  
  
5. Quando executar o cliente, anote a identidade antes e depois de executá-la com diferentes credenciais.  
