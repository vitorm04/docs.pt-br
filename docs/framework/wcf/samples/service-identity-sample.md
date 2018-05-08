---
title: Exemplo de identidade de serviço
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: d7eee6070956fb3b9a87a79d79040f94740ad2d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="service-identity-sample"></a>Exemplo de identidade de serviço
Este exemplo de identidade de serviço demonstra como definir a identidade de um serviço. Em tempo de design, um cliente pode recuperar a identidade usando metadados do serviço e, em seguida, em tempo de execução, o cliente pode autenticar a identidade do serviço. O conceito de identidade de serviço é permitir que um cliente autenticar um serviço antes de chamar qualquer uma das suas operações, protegendo o cliente de chamadas não autenticadas. Em uma conexão segura o serviço também autentica credenciais do cliente antes de permitir acesso ele, mas isso não é o foco deste exemplo. Consulte os exemplos em [cliente](../../../../docs/framework/wcf/samples/client.md) que mostram a autenticação do servidor.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo ilustra os seguintes recursos:  
  
-   Como definir os diferentes tipos de identidade em diferentes pontos de extremidade para um serviço. Cada tipo de identidade tem recursos diferentes. O tipo de identidade deve ser usada depende do tipo de credenciais de segurança usadas na associação do ponto de extremidade.  
  
-   Identidade pode ser definida declarativamente na configuração ou imperativa no código. Normalmente para o cliente e o serviço, você deve usar configuração para definir a identidade.  
  
-   Como definir uma identidade personalizada no cliente. Uma identidade personalizada é normalmente uma personalização de um tipo existente de identidade, que permite que o cliente examinar outras informações de declaração fornecidas nas credenciais do serviço para tomar decisões de autorização antes de chamar o serviço.  
  
    > [!NOTE]
    >  Este exemplo verifica a identidade de um certificado específico chamado identity.com e a chave RSA contidos no certificado. Ao usar os tipos de identidade do certificado e RSA na configuração no cliente, uma maneira fácil de obter esses valores é inspecionar o WSDL para o serviço em que esses valores são serializados.  
  
 O código de exemplo a seguir mostra como configurar a identidade de um ponto de extremidade de serviço com o servidor DNS (Domain Name) de um certificado usando o WSHttpBinding.  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 A identidade também pode ser especificada na configuração no arquivo App. config. O exemplo a seguir mostra como definir a identidade UPN (Nome Principal do usuário) para um ponto de extremidade de serviço.  
  
```xml  
<endpoint address="upnidentity"  
        behaviorConfiguration=""  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_Windows"  
        name="WSHttpBinding_ICalculator_Windows"  
        contract="Microsoft.ServiceModel.Samples.ICalculator">  
  <!-- Set the UPN identity for this endpoint -->  
  <identity>  
      <userPrincipalName value="host\myservice.com" />  
  </identity >  
</endpoint>  
```  
  
 Uma identidade personalizada pode ser definida no cliente, derivando o <xref:System.ServiceModel.EndpointIdentity> e <xref:System.ServiceModel.Security.IdentityVerifier> classes. Conceitualmente o <xref:System.ServiceModel.Security.IdentityVerifier> classe pode ser considerada como o cliente equivalente do serviço de `AuthorizationManager` classe. O exemplo de código a seguir mostra uma implementação de `OrgEndpointIdentity`, que armazena um nome de organização para fazer a correspondência no nome da entidade do certificado do servidor. A verificação de autorização para o nome da organização ocorre no `CheckAccess` método o `CustomIdentityVerifier` classe.  
  
```  
// This custom EndpointIdentity stores an organization name   
public class OrgEndpointIdentity : EndpointIdentity  
{  
    private string orgClaim;  
    public OrgEndpointIdentity(string orgName)  
    {  
        orgClaim = orgName;  
    }  
    public string OrganizationClaim  
    {  
        get { return orgClaim; }  
        set { orgClaim = value; }  
    }  
}  
  
//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to  
//check that X.509 certificate's distinguished name claim contains  
//the organization name e.g. the string value "O=Contoso"   
class CustomIdentityVerifier : IdentityVerifier  
{  
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)  
    {  
        bool returnvalue = false;  
        foreach (ClaimSet claimset in authContext.ClaimSets)  
        {  
            foreach (Claim claim in claimset)  
            {  
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")  
                {  
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;  
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))  
                    {  
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);  
                        Console.WriteLine("Right: {0}", claim.Right);  
                        Console.WriteLine("Resource: {0}",claim.Resource);  
                        Console.WriteLine();  
                        returnvalue = true;  
                    }  
                }  
            }  
        }  
        return returnvalue;  
    }  
}  
```  
  
 Este exemplo usa um certificado chamado identity.com que está na pasta de solução de identidade específico do idioma.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Em [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou [!INCLUDE[wv](../../../../includes/wv-md.md)], importe o arquivo de certificado Identity.pfx na pasta de solução de identidade para o repositório de LocalMachine/meu certificado (pessoal) usando a ferramenta snap-in do MMC. Esse arquivo é protegido por senha. Durante a importação, você será solicitado para uma senha. Tipo `xyz` na caixa de senha. Para obter mais informações, consulte o [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tópico. Depois que isso for feito, execute bat em um prompt de comando Visual Studio com privilégios de administrador, que copia o certificado no armazenamento de pessoas confiáveis CurrentUser para uso no cliente.  
  
2.  Em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], execute bat da pasta de instalação de exemplo dentro de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando com privilégios de administrador. Isso instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando. Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat. Certifique-se de que você remova os certificados executando Cleanup.bat quando você tiver terminado com o exemplo. Outros exemplos de segurança usam os mesmos certificados.  
  
3.  Inicie Service.exe do diretório \service\bin. Certifique-se de que o serviço indica que ele está pronto e exibe um prompt para pressionar \<Enter > para encerrar o serviço.  
  
4.  Inicie o Client.exe do diretório \Client\Bin. ou pressionando F5 no Visual Studio para criar e executar. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
5.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Antes de criar a parte cliente de exemplo, certifique-se de alterar o valor para o endereço de ponto de extremidade do serviço no arquivo de Client.cs o `CallServiceCustomClientIdentity` método. Em seguida, crie o exemplo.  
  
2.  Crie um diretório no computador de serviço.  
  
3.  Copie os arquivos de programa do serviço de service\bin para o diretório no computador do serviço. Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.  
  
4.  Crie um diretório no computador cliente para os binários do cliente.  
  
5.  Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente. Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.  
  
6.  Sobre o serviço, execute `setup.bat service` em um prompt de comando do Visual Studio aberto com privilégios de administrador. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
7.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8.  No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço. Há várias instâncias que devem ser alteradas.  
  
9. No cliente, execute ImportServiceCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.  
  
10. No computador do serviço, inicie o Service.exe do prompt de comando.  
  
11. No computador cliente, inicie o Client.exe em um prompt de comando. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
-   Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.  
  
    > [!NOTE]
    >  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores. Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Consulte também
