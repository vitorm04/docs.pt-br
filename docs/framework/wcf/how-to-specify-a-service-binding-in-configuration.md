---
title: 'Como: Especificar uma associação de serviço na configuração'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 2152398cecccdf1f949baf30217b7f5ac19ae22f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527127"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Como: Especificar uma associação de serviço na configuração
Neste exemplo, uma `ICalculator` contrato é definido para um serviço de calculadora básica, o serviço é implementado de `CalculatorService` classe e, em seguida, seu ponto de extremidade está configurado no arquivo Web. config, onde ele é especificado que o serviço usa o <xref:System.ServiceModel.BasicHttpBinding> . Para obter uma descrição de como configurar esse serviço usando o código em vez de uma configuração, consulte [como: Especificar uma associação de serviço no código](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Ele geralmente é a prática recomendada para especificar declarativamente as informações de endereço e associação na configuração em vez de imperativa no código. Definir pontos de extremidade no código geralmente não é prático porque as associações e endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. De modo geral, informações fora do código de endereçamento e manter a associação permite que eles alterem os sem ter que recompilar ou reimplantar o aplicativo.  
  
 Todas as etapas de configuração a seguir podem ser executadas usando o [ferramenta de Editor de configuração (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Para a cópia de origem deste exemplo, consulte [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Para especificar o BasicHttpBinding para usar para configurar o serviço  
  
1.  Defina um contrato de serviço para o tipo de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  Implemente o contrato de serviço em uma classe de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  Informações de associação ou o endereço não estão especificadas dentro da implementação do serviço. Além disso, o código não tem a ser gravado para buscar informações do arquivo de configuração.  
  
3.  Crie um arquivo Web. config para configurar um ponto de extremidade para o `CalculatorService` que usa o <xref:System.ServiceModel.WSHttpBinding>.  
  
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
  
4.  Crie um arquivo Service SVC que contém a linha a seguir e colocá-lo em seu diretório virtual de serviços de informações da Internet (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Para modificar os valores padrão das propriedades de associação  
  
1.  Para modificar um dos valores de propriedade padrão do <xref:System.ServiceModel.WSHttpBinding>, criar um novo nome de configuração de associação - `<binding name="Binding1">` - dentro a [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento e defina os novos valores para os atributos das associação nesse elemento de associação. Por exemplo, para alterar o padrão aberto e fechar os valores de tempo limite de 1 minuto para 2 minutos, adicione o seguinte ao arquivo de configuração.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Consulte também
- [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Especificando um endereço do ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
