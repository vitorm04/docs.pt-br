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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 94d6cc499caddc8b3cbbf8ba7845e4de5441165c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a><span data-ttu-id="fc77e-102">Como migrar código de serviço Web ASP.NET Web para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fc77e-102">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="fc77e-103">O procedimento a seguir descreve como migrar um serviço da Web ASP.NET [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc77e-103">The following procedure describes how to migrate an ASP.NET Web Service to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="fc77e-104">Procedimento</span><span class="sxs-lookup"><span data-stu-id="fc77e-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a><span data-ttu-id="fc77e-105">Para migrar o código de serviço da Web do ASP.NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="fc77e-105">To migrate ASP.NET Web service code to WCF</span></span>  
  
1.  <span data-ttu-id="fc77e-106">Certifique-se de que um abrangente conjunto de testes existem para o serviço.</span><span class="sxs-lookup"><span data-stu-id="fc77e-106">Ensure that a comprehensive set of tests exist for the service.</span></span>  
  
2.  <span data-ttu-id="fc77e-107">O WSDL para o serviço de gerar e salvar uma cópia na mesma pasta que o arquivo do serviço. asmx.</span><span class="sxs-lookup"><span data-stu-id="fc77e-107">Generate the WSDL for the service and save a copy in the same folder as the service’s .asmx file.</span></span>  
  
3.  <span data-ttu-id="fc77e-108">Atualize o serviço Web do ASP.NET para usar o .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="fc77e-108">Upgrade the ASP.NET Web service to use .NET 2.0.</span></span> <span data-ttu-id="fc77e-109">Primeiro implantar o .NET Framework 2.0 para o aplicativo no IIS e, em seguida, usar o Visual Studio 2005 para automatizar o processo de conversão de código, conforme documentado no [guia passo a passo para converter projetos da Web do Visual Studio .NET 2002/2003 para o Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span><span class="sxs-lookup"><span data-stu-id="fc77e-109">First deploy the .NET Framework 2.0 to the application in IIS, and then use Visual Studio 2005 to automate the code conversion process, as documented in [Step-By-Step Guide to Converting Web Projects from Visual Studio .NET 2002/2003 to Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span></span> <span data-ttu-id="fc77e-110">Execute o conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="fc77e-110">Run the set of tests.</span></span>  
  
4.  <span data-ttu-id="fc77e-111">Fornecer valores explícitos para o `Namespace` e `Name` parâmetros do <xref:System.Web.Services.WebService> atributos se eles não forem fornecidos.</span><span class="sxs-lookup"><span data-stu-id="fc77e-111">Provide explicit values for the `Namespace` and `Name` parameters of the <xref:System.Web.Services.WebService> attributes if they are not provided already.</span></span> <span data-ttu-id="fc77e-112">Faça o mesmo para o `MessageName` parâmetro o <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fc77e-112">Do the same for the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span> <span data-ttu-id="fc77e-113">Se os valores explícitos já não são fornecidos para os cabeçalhos HTTP SOAPAction pela qual solicitações são roteadas para os métodos, em seguida, explicitamente especificam o valor padrão de `Action` parâmetro com um <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fc77e-113">If explicit values are not already provided for the SOAPAction HTTP headers by which requests are routed to methods, then explicitly specify the default value of the `Action` parameter with a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
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
  
5.  <span data-ttu-id="fc77e-114">Teste a alteração.</span><span class="sxs-lookup"><span data-stu-id="fc77e-114">Test the change.</span></span>  
  
6.  <span data-ttu-id="fc77e-115">Mova qualquer código substancial nos corpos de métodos da classe para uma classe separada que a classe original é feita para usar.</span><span class="sxs-lookup"><span data-stu-id="fc77e-115">Move any substantive code in the bodies of the methods of the class to a separate class that the original class is made to use.</span></span>  
  
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
  
7.  <span data-ttu-id="fc77e-116">Teste a alteração.</span><span class="sxs-lookup"><span data-stu-id="fc77e-116">Test the change.</span></span>  
  
8.  <span data-ttu-id="fc77e-117">Adicione referências aos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assemblies System. ServiceModel e Serialization ao projeto de serviço da Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fc77e-117">Add references to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assemblies System.ServiceModel and System.Runtime.Serialization to the ASP.NET Web service project.</span></span>  
  
9. <span data-ttu-id="fc77e-118">Executar [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe cliente de WSDL.</span><span class="sxs-lookup"><span data-stu-id="fc77e-118">Run [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class from the WSDL.</span></span> <span data-ttu-id="fc77e-119">Adicione o módulo de classe gerada para a solução.</span><span class="sxs-lookup"><span data-stu-id="fc77e-119">Add the generated class module to the solution.</span></span>  
  
10. <span data-ttu-id="fc77e-120">O módulo de classe gerado na etapa anterior contém a definição de uma interface.</span><span class="sxs-lookup"><span data-stu-id="fc77e-120">The class module generated in the preceding step contains the definition of an interface.</span></span>  
  
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
  
     <span data-ttu-id="fc77e-121">Modificar a definição da classe de serviço da Web do ASP.NET para que a classe é definida como implementar essa interface, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fc77e-121">Modify the definition of the ASP.NET Web service class so that the class is defined as implementing that interface, as shown in the following sample code.</span></span>  
  
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
  
11. <span data-ttu-id="fc77e-122">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="fc77e-122">Compile the project.</span></span> <span data-ttu-id="fc77e-123">Pode haver alguns erros devido ao código gerado na etapa 9 que duplicado algumas definições de tipo.</span><span class="sxs-lookup"><span data-stu-id="fc77e-123">There may be some errors due to the code generated in step nine that duplicated some type definitions.</span></span> <span data-ttu-id="fc77e-124">Repare esses erros, geralmente, excluindo as definições já existentes dos tipos.</span><span class="sxs-lookup"><span data-stu-id="fc77e-124">Repair those errors, usually by deleting the pre-existing definitions of the types.</span></span> <span data-ttu-id="fc77e-125">Teste a alteração.</span><span class="sxs-lookup"><span data-stu-id="fc77e-125">Test the change.</span></span>  
  
12. <span data-ttu-id="fc77e-126">Remova os atributos específicos do ASP.NET, como o <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> e <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fc77e-126">Remove the ASP.NET-specific attributes, such as the <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> and <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
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
  
13. <span data-ttu-id="fc77e-127">Configurar a classe, que agora é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tipo exigir serviço [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modo de compatibilidade ASP.NET se baseava-se o serviço Web do ASP.NET em qualquer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="fc77e-127">Configure the class, which is now a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service type, to require [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode if the ASP.NET Web service relied on any of the following:</span></span>  
  
    -   <span data-ttu-id="fc77e-128">O <xref:System.Web.HttpContext> classe.</span><span class="sxs-lookup"><span data-stu-id="fc77e-128">The <xref:System.Web.HttpContext> class.</span></span>  
  
    -   <span data-ttu-id="fc77e-129">Os perfis do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fc77e-129">The ASP.NET Profiles.</span></span>  
  
    -   <span data-ttu-id="fc77e-130">ACLs em arquivos. asmx.</span><span class="sxs-lookup"><span data-stu-id="fc77e-130">ACLs on .asmx files.</span></span>  
  
    -   <span data-ttu-id="fc77e-131">Opções de autenticação do IIS.</span><span class="sxs-lookup"><span data-stu-id="fc77e-131">IIS authentication options.</span></span>  
  
    -   <span data-ttu-id="fc77e-132">Opções de representação do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fc77e-132">ASP.NET impersonation options.</span></span>  
  
    -   <span data-ttu-id="fc77e-133">Globalização do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fc77e-133">ASP.NET globalization.</span></span>  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. <span data-ttu-id="fc77e-134">Renomeie o arquivo original. asmx. asmx.old.</span><span class="sxs-lookup"><span data-stu-id="fc77e-134">Rename the original .asmx file to .asmx.old.</span></span>  
  
15. <span data-ttu-id="fc77e-135">Criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arquivo para o serviço de serviço, dê a ele a extensão,. asmx e salvá-lo para a raiz do aplicativo no IIS.</span><span class="sxs-lookup"><span data-stu-id="fc77e-135">Create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service file for the service, give it the extension, .asmx, and save it into the application root in IIS.</span></span>  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. <span data-ttu-id="fc77e-136">Adicionar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuração do serviço em seu arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="fc77e-136">Add a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration for the service to its Web.config file.</span></span> <span data-ttu-id="fc77e-137">Configurar o serviço para usar o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), para usar o arquivo de serviço com a extensão. asmx criada nas etapas anteriores e não gerar WSDL para si mesmo, mas usar o WSDL da etapa 2.</span><span class="sxs-lookup"><span data-stu-id="fc77e-137">Configure the service to use the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), to use the service file with the .asmx extension created in the preceding steps, and to not generate WSDL for itself, but to use the WSDL from step two.</span></span> <span data-ttu-id="fc77e-138">Também configurá-lo para usar o modo de compatibilidade ASP.NET se necessário.</span><span class="sxs-lookup"><span data-stu-id="fc77e-138">Also configure it to use ASP.NET compatibility mode if necessary.</span></span>  
  
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
  
17. <span data-ttu-id="fc77e-139">Salve a configuração.</span><span class="sxs-lookup"><span data-stu-id="fc77e-139">Save the configuration.</span></span>  
  
18. <span data-ttu-id="fc77e-140">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="fc77e-140">Compile the project.</span></span>  
  
19. <span data-ttu-id="fc77e-141">Execute o conjunto de testes para garantir que todas as alterações funcionem.</span><span class="sxs-lookup"><span data-stu-id="fc77e-141">Run the set of tests to make sure all the changes work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc77e-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc77e-142">See Also</span></span>  
 [<span data-ttu-id="fc77e-143">Como: migrar o código de cliente de serviço da Web do ASP.NET para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="fc77e-143">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
