---
title: "Como especificar uma associação de serviço em configuração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea54b2f84c9de233ff2560795dc97f79c15aa0af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Como especificar uma associação de serviço em configuração
Neste exemplo, um `ICalculator` contrato é definido para um serviço básico de cálculo, o serviço é implementado no `CalculatorService` classe e seu ponto de extremidade está configurado no arquivo Web. config, onde ele é especificado que o serviço usa o <xref:System.ServiceModel.BasicHttpBinding> . Para obter uma descrição de como configurar este serviço usando código em vez de uma configuração, consulte [como: especificar uma associação de serviço em código](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Geralmente é a prática recomendada para especificar declarativamente a associação e as informações de endereço na configuração em vez de imperativa no código. Definir pontos de extremidade no código geralmente não é prático porque as associações e os endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Geralmente, informações sem o código de endereçamento e manter a associação permite que a alteração sem precisar recompilar ou reimplantar o aplicativo.  
  
 Todas as etapas de configuração a seguir podem ser feitas usando o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Para a cópia de origem deste exemplo, consulte [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Para especificar o BasicHttpBinding para usar para configurar o serviço  
  
1.  Defina um contrato de serviço para o tipo de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  Implemente o contrato de serviço em uma classe de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  Informações de endereço e associação não estão especificadas dentro da implementação do serviço. Além disso, não tem código a ser gravado para buscar informações do arquivo de configuração.  
  
3.  Criar um arquivo Web. config para configurar um ponto de extremidade para o `CalculatorService` que usa o <xref:System.ServiceModel.WSHttpBinding>.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <-- Leave the address blank to be populated by default-->  
            <--from the hosting environment,in this case IIS, so -->  
            <-- the address will just be that of the IIS Virtual -->  
            <--Directory.-->  
                address=""   
            <--Specify the binding type -->  
                binding="wsHttpBinding"  
            <--Specify the binding configuration name for that -->  
            <--binding type. This is optional but useful if you  -->  
            <--want to modify the properties of the binding. -->  
            <--The bindingConfiguration name Binding1 is defined  -->  
            <--below in the bindings element.  -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <-- Binding property values can be modified here. -->  
              <--See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  Crie um arquivo SVC que contém a linha a seguir e colocá-lo em seu diretório virtual dos serviços de informações da Internet (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Para modificar os valores padrão das propriedades de associação  
  
1.  Para modificar um dos valores de propriedade padrão da <xref:System.ServiceModel.WSHttpBinding>, crie um novo nome de configuração de associação - `<binding name="Binding1">` - dentro de [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento e definir os novos valores para os atributos do Esse elemento de associação de associação. Por exemplo, para alterar o padrão aberto e fechar os valores de tempo limite de 1 minuto para 2 minutos, adicione o seguinte ao arquivo de configuração.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Especificando um endereço do ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
