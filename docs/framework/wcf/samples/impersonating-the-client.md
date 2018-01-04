---
title: Representando o cliente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a17a3631b781e6a96eb8aec17b20e8ddca52890d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="impersonating-the-client"></a>Representando o cliente
O exemplo representação demonstra como representar o aplicativo chamador no serviço de forma que o serviço pode acessar recursos do sistema em nome do chamador.  
  
 Este exemplo se baseia o [auto-host](../../../../docs/framework/wcf/samples/self-host.md) exemplo. Os arquivos de configuração do cliente e de serviço são os mesmos que o [auto-host](../../../../docs/framework/wcf/samples/self-host.md) exemplo.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O código de serviço tiver sido modificado, de modo que o `Add` método no serviço representará o chamador usando a <xref:System.ServiceModel.OperationBehaviorAttribute> conforme mostrado no código de exemplo a seguir.  
  
```  
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
  
 Como resultado, o contexto de segurança do thread em execução é alternado para representar o chamador antes de inserir o `Add` método e revertida em sair do método.  
  
 O `DisplayIdentityInformation` método mostrado no código de exemplo a seguir é uma função de utilitário que exibe a identidade do chamador.  
  
```  
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
  
 O `Subtract` método no serviço representará o chamador usando chamadas obrigatória, conforme mostrado no código de exemplo a seguir.  
  
```  
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
  
 Observe que nesse caso o chamador não é representado pela chamada de inteiro, mas apenas é representado por uma parte da chamada. Em geral, a representação para o menor escopo é preferível representando para toda a operação.  
  
 Os outros métodos não representam o chamador.  
  
 O código do cliente foi modificado para definir a representação de nível para <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>. O cliente especifica o nível de representação a ser usado pelo serviço, usando o <xref:System.Security.Principal.TokenImpersonationLevel> enumeração. A enumeração suporta os seguintes valores: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> e <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Para executar uma verificação de acesso ao acessar um recurso do sistema no computador local que é protegida usando ACLs do Windows, o nível de representação deve ser definido como <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, conforme mostrado no código de exemplo a seguir.  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas em janelas do console de serviço e o cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
> [!NOTE]
>  O serviço deve executar sob uma conta de administrador ou a conta que ele é executado deve ter direitos para registrar o URI de http://localhost:8000/ServiceModelSamples com a camada HTTP. Tais direitos podem ser concedidos, configurando uma [reserva de Namespace](http://go.microsoft.com/fwlink/?LinkId=95012) usando o [ferramenta Httpcfg.exe](http://go.microsoft.com/fwlink/?LinkId=95010).  
  
> [!NOTE]
>  Em computadores que executam [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a representação tem suporte apenas se o aplicativo Host.exe tem o privilégio de representação. (Por padrão, somente os administradores têm essa permissão.) Para adicionar esse privilégio a uma conta de serviço estiver em execução, vá para **ferramentas administrativas**, abra **política de segurança Local**, abra **políticas locais**, clique em **Atribuição de direitos de usuário**e selecione **representar um cliente após autenticação** e clique duas vezes em **propriedades** para adicionar um usuário ou grupo.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Para demonstrar o serviço representará o chamador, execute o cliente em uma conta diferente daquela que o serviço está em execução. Para fazer isso, no prompt de comando, digite:  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Em seguida, você será solicitado para uma senha. Insira a senha para a conta especificada anteriormente.  
  
5.  Quando você executa o cliente, observe a identidade antes e depois de executá-lo com credenciais diferentes.  
  
## <a name="see-also"></a>Consulte também
