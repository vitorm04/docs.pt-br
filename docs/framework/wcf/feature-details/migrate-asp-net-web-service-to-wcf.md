---
title: "Como migrar código de serviço Web ASP.NET Web para o Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d6ed443d2b645687d59a3d795c706f303616cfb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a>Como migrar código de serviço Web ASP.NET Web para o Windows Communication Foundation
O procedimento a seguir descreve como migrar um serviço da Web ASP.NET [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a>Para migrar o código de serviço da Web do ASP.NET para o WCF  
  
1.  Certifique-se de que um abrangente conjunto de testes existem para o serviço.  
  
2.  O WSDL para o serviço de gerar e salvar uma cópia na mesma pasta que o arquivo do serviço. asmx.  
  
3.  Atualize o serviço Web do ASP.NET para usar o .NET 2.0. Primeiro implantar o .NET Framework 2.0 para o aplicativo no IIS e, em seguida, usar o Visual Studio 2005 para automatizar o processo de conversão de código, conforme documentado no [guia passo a passo para converter projetos da Web do Visual Studio .NET 2002/2003 para o Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492). Execute o conjunto de testes.  
  
4.  Fornecer valores explícitos para o `Namespace` e `Name` parâmetros do <xref:System.Web.Services.WebService> atributos se eles não forem fornecidos. Faça o mesmo para o `MessageName` parâmetro o <xref:System.Web.Services.WebMethodAttribute>. Se os valores explícitos já não são fornecidos para os cabeçalhos HTTP SOAPAction pela qual solicitações são roteadas para os métodos, em seguida, explicitamente especificam o valor padrão de `Action` parâmetro com um <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
5.  Teste a alteração.  
  
6.  Mova qualquer código substancial nos corpos de métodos da classe para uma classe separada que a classe original é feita para usar.  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
    }  
  
    internal class ActualAdder  
    {  
         internal double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
7.  Teste a alteração.  
  
8.  Adicione referências aos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assemblies System. ServiceModel e Serialization ao projeto de serviço da Web do ASP.NET.  
  
9. Executar [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe cliente de WSDL. Adicione o módulo de classe gerada para a solução.  
  
10. O módulo de classe gerado na etapa anterior contém a definição de uma interface.  
  
    ```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface AdderSoap  
    {  
         [System.ServiceModel.OperationContractAttribute(  
          Action="http://tempuri.org/Add",   
          ReplyAction="http://tempuri.org/Add")]  
         AddResponse Add(AddRequest request);  
    }  
    ```  
  
     Modificar a definição da classe de serviço da Web do ASP.NET para que a classe é definida como implementar essa interface, conforme mostrado no código de exemplo a seguir.  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder: AdderSoap  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
            return new AddResponse(  
            new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
11. Compile o projeto. Pode haver alguns erros devido ao código gerado na etapa 9 que duplicado algumas definições de tipo. Repare esses erros, geralmente, excluindo as definições já existentes dos tipos. Teste a alteração.  
  
12. Remova os atributos específicos do ASP.NET, como o <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> e <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
    ```  
    public class Adder: AdderSoap  
    {  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
              return new AddResponse(  
             new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
13. Configurar a classe, que agora é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tipo exigir serviço [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modo de compatibilidade ASP.NET se baseava-se o serviço Web do ASP.NET em qualquer um dos seguintes:  
  
    -   O <xref:System.Web.HttpContext> classe.  
  
    -   Os perfis do ASP.NET.  
  
    -   ACLs em arquivos. asmx.  
  
    -   Opções de autenticação do IIS.  
  
    -   Opções de representação do ASP.NET.  
  
    -   Globalização do ASP.NET.  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. Renomeie o arquivo original. asmx. asmx.old.  
  
15. Criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arquivo para o serviço de serviço, dê a ele a extensão,. asmx e salvá-lo para a raiz do aplicativo no IIS.  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. Adicionar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuração do serviço em seu arquivo Web. config. Configurar o serviço para usar o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), para usar o arquivo de serviço com a extensão. asmx criada nas etapas anteriores e não gerar WSDL para si mesmo, mas usar o WSDL da etapa 2. Também configurá-lo para usar o modo de compatibilidade ASP.NET se necessário.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.web>  
      <compilation>  
      <buildProviders>  
       <remove extension=".asmx" />  
       <add extension=".asmx"   
        type=  
        "System.ServiceModel.Activation.ServiceBuildProvider,  
        T:System.ServiceModel, Version=2.0.0.0,   
       Culture=neutral,   
       PublicKeyToken=b77a5c561934e089" />  
      </buildProviders>  
      </compilation>  
     </system.web>  
     <system.serviceModel>  
      <services>  
      <service name="MyOrganization.Adder "  
        behaviorConfiguration="AdderBehavior">  
       <endpoint   
        address=""  
        binding="basicHttpBinding"  
        contract="AdderSoap "/>  
       </service>  
      </services>  
      <behaviors>  
      <behavior name="AdderBehavior">  
       <metadataPublishing   
        enableMetadataExchange="true"   
        enableGetWsdl="true"   
        enableHelpPage="true"   
        metadataLocation=  
        "http://MyHost.com/AdderService/Service.WSDL"/>  
      </behavior>  
      </behaviors>  
      <serviceHostingEnvironment   
       aspNetCompatibilityEnabled ="true"/>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
17. Salve a configuração.  
  
18. Compile o projeto.  
  
19. Execute o conjunto de testes para garantir que todas as alterações funcionem.  
  
## <a name="see-also"></a>Consulte também  
 [Como: migrar o código de cliente de serviço da Web do ASP.NET para o Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
