---
title: Como especificar uma associação de serviço em configuração
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 245fe50ed5a80c51163652defb642cebefd55dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184028"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Como especificar uma associação de serviço em configuração
Neste exemplo, `ICalculator` um contrato é definido para um serviço de `CalculatorService` calculadora básica, o serviço é implementado na classe e, em seguida, seu ponto <xref:System.ServiceModel.BasicHttpBinding>final é configurado no arquivo Web.config, onde é especificado que o serviço usa o . Para obter uma descrição de como configurar esse serviço usando código em vez de uma configuração, consulte [Como: Especificar uma vinculação de serviço em código](how-to-specify-a-service-binding-in-code.md).  
  
 Geralmente é a melhor prática para especificar as informações de vinculação e endereço declarativamente na configuração, em vez de imperativamente em código. Definir pontos finais no código geralmente não é prático porque as vinculações e endereços de um serviço implantado são tipicamente diferentes daqueles usados enquanto o serviço está sendo desenvolvido. De forma mais geral, manter as informações de vinculação e endereçamento fora do código permite que eles mudem sem ter que recompilar ou reimplantar o aplicativo.  
  
 Todas as seguintes etapas de configuração podem ser realizadas usando a [Ferramenta do Editor de Configuração (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Para obter a cópia de origem deste exemplo, consulte [BasicBinding](./samples/basicbinding.md).  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Para especificar o BasicHttpBinding a ser usado para configurar o serviço  
  
1. Defina um contrato de serviço para o tipo de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Implemente o contrato de serviço em uma classe de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > As informações de endereço ou vinculação não são especificadas dentro da implementação do serviço. Além disso, o código não precisa ser escrito para obter essas informações do arquivo de configuração.  
  
3. Crie um arquivo Web.config para configurar `CalculatorService` um ponto <xref:System.ServiceModel.WSHttpBinding>final para o que usa o .  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
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
  
4. Crie um arquivo Service.svc que contenha a seguinte linha e coloque-a no diretório virtual do IIS (Internet Information Services, serviços de informação da Internet).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>Para modificar os valores padrão das propriedades vinculantes  
  
1. Para modificar um dos valores <xref:System.ServiceModel.WSHttpBinding>de propriedade padrão do `<binding name="Binding1">` , criar um novo nome de configuração vinculante - dentro do [ \<elemento wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) e definir os novos valores para os atributos da vinculação neste elemento de vinculação. Por exemplo, para alterar os valores de tempo aberto padrão e fechar de 1 minuto a 2 minutos, adicione o seguinte ao arquivo de configuração.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Confira também

- [Usando associações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md)
- [Especificando um endereço do ponto de extremidade](specifying-an-endpoint-address.md)
