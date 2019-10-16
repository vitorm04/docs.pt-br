---
title: Como especificar uma associação de serviço em configuração
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: b9790d3fb5fc20b3d2c6ce776070274ef0403732
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319866"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="d3fce-102">Como especificar uma associação de serviço em configuração</span><span class="sxs-lookup"><span data-stu-id="d3fce-102">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="d3fce-103">Neste exemplo, um contrato `ICalculator` é definido para um serviço de calculadora básica, o serviço é implementado na classe `CalculatorService` e, em seguida, seu ponto de extremidade é configurado no arquivo Web. config, onde é especificado que o serviço usa o <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d3fce-103">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="d3fce-104">Para obter uma descrição de como configurar esse serviço usando o código em vez de uma configuração, consulte [como especificar uma associação de serviço no código](how-to-specify-a-service-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="d3fce-104">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="d3fce-105">Geralmente, é a prática recomendada especificar a associação e as informações de endereço de forma declarativa na configuração, em vez de imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="d3fce-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="d3fce-106">A definição de pontos de extremidade no código geralmente não é prática porque as associações e os endereços para um serviço implantado são normalmente diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="d3fce-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="d3fce-107">Em geral, manter as informações de vinculação e endereçamento do código permite que elas sejam alteradas sem a necessidade de recompilar ou reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3fce-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="d3fce-108">Todas as etapas de configuração a seguir podem ser executadas usando a [ferramenta do editor de configuração (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d3fce-108">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="d3fce-109">Para a cópia de origem deste exemplo, consulte [BasicBinding](./samples/basicbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d3fce-109">For the source copy of this example, see [BasicBinding](./samples/basicbinding.md).</span></span>  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="d3fce-110">Para especificar o BasicHttpBinding a ser usado para configurar o serviço</span><span class="sxs-lookup"><span data-stu-id="d3fce-110">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1. <span data-ttu-id="d3fce-111">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="d3fce-111">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="d3fce-112">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="d3fce-112">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="d3fce-113">As informações de endereço ou de associação não são especificadas dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="d3fce-113">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="d3fce-114">Além disso, o código não precisa ser escrito para buscar essas informações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d3fce-114">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3. <span data-ttu-id="d3fce-115">Crie um arquivo Web. config para configurar um ponto de extremidade para o `CalculatorService` que usa o <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d3fce-115">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <!-- Leave the address blank to be populated by default -->  
            <!-- from the hosting environment,in this case IIS, so -->  
            <!-- the address will just be that of the IIS Virtual -->  
            <!-- Directory. -->  
                address=""   
            <!-- Specify the binding type -->  
                binding="wsHttpBinding"  
            <!-- Specify the binding configuration name for that -->  
            <!-- binding type. This is optional but useful if you -->  
            <!-- want to modify the properties of the binding. -->  
            <!-- The bindingConfiguration name Binding1 is defined -->  
            <!-- below in the bindings element. -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="d3fce-116">Crie um arquivo Service. svc que contenha a linha a seguir e coloque-o em seu diretório virtual Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="d3fce-116">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="d3fce-117">Para modificar os valores padrão das propriedades de associação</span><span class="sxs-lookup"><span data-stu-id="d3fce-117">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="d3fce-118">Para modificar um dos valores de propriedade padrão do <xref:System.ServiceModel.WSHttpBinding>, crie um novo nome de configuração de associação-`<binding name="Binding1">`-dentro do elemento de [> de \<wsHttpBinding](../configure-apps/file-schema/wcf/wshttpbinding.md) e defina os novos valores para os atributos da Associação nesse elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="d3fce-118">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="d3fce-119">Por exemplo, para alterar os valores de tempo limite de abertura e fechamento padrão de 1 minuto para 2 minutos, adicione o seguinte ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d3fce-119">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d3fce-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3fce-120">See also</span></span>

- [<span data-ttu-id="d3fce-121">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d3fce-121">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d3fce-122">Especificando um endereço do ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="d3fce-122">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
