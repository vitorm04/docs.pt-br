---
title: Configurando associações para serviços do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 52f93acacec434ce6f7ba93678615c104aa94b24
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704037"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Configurando associações para serviços do Windows Communication Foundation
Ao criar um aplicativo, você geralmente deseja adiar as decisões para o administrador após a implantação do aplicativo. Por exemplo, geralmente não há nenhuma maneira de saber com antecedência qual um endereço de serviço ou o identificador de recurso uniforme (URI), será. Em vez de embutir um endereço, é preferível para permitir que um administrador para fazer isso depois de criar um serviço. Essa flexibilidade é realizada por meio da configuração.  
  
> [!NOTE]
>  Use o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com o `/config` switch para criar rapidamente arquivos de configuração.  
  
## <a name="major-sections"></a>Seções principais  
 O esquema de configuração do Windows Communication Foundation (WCF) inclui as três seções principais (`serviceModel`, `bindings`, e `services`):  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a>Elementos de ServiceModel  
 Você pode usar a seção delimitada pelo `system.ServiceModel` elemento para configurar um tipo de serviço com um ou mais pontos de extremidade, bem como configurações de um serviço. Cada ponto de extremidade, em seguida, pode ser configurado com um endereço, um contrato e uma associação. Para obter mais informações sobre pontos de extremidade, consulte [visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md). Se nenhum ponto de extremidade forem especificados, o tempo de execução adiciona pontos de extremidade padrão. Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 Uma associação Especifica (pipes HTTP, TCP, enfileiramento de mensagens) de transportes e protocolos (segurança, confiabilidade, os fluxos de transação) e consiste em elementos, cada um deles especifica um aspecto de como um ponto de extremidade se comunica com o mundo de associação.  
  
 Por exemplo, especificando o [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento indica para usar o HTTP como o transporte para um ponto de extremidade. Isso é usado para conectar o ponto de extremidade no tempo de execução quando o serviço usando esse ponto de extremidade é aberto.  
  
 Há dois tipos de associações: predefinidos e personalizados. Associações predefinidas contêm útil combinações de elementos que são usados em cenários comuns. Para obter uma lista de tipos de associação predefinida que o WCF fornece, consulte [System-Provided associações](../../../docs/framework/wcf/system-provided-bindings.md). Se nenhuma coleção de associação predefinida tiver a combinação correta de recursos que precisa de um aplicativo de serviço, você pode construir ligações personalizadas para atender aos requisitos do aplicativo. Para obter mais informações sobre ligações personalizadas, consulte [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Os quatro exemplos a seguir ilustram as configurações de associação mais comuns usadas para configurar um serviço WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Especificando um ponto de extremidade para usar um tipo de associação  
 O primeiro exemplo ilustra como especificar um ponto de extremidade configurado com um endereço, um contrato e uma associação.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 Neste exemplo, o `name` atributo indica que a configuração é do tipo de serviço. Quando você cria um serviço em seu código com o `HelloWorld` contrato, ele é inicializado com todos os pontos de extremidade definidos na configuração de exemplo. Se o assembly implementa apenas um contrato de serviço, o `name` atributo pode ser omitido porque o serviço usa o tipo só está disponível. O atributo utiliza uma cadeia de caracteres, deve estar no formato `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 O `address` atributo especifica o URI usado por outros pontos de extremidade para se comunicar com o serviço. O URI pode ser um caminho absoluto ou relativo. Se um endereço relativo for fornecido, o host deve fornecer um endereço base que é apropriado para o esquema de transporte usado na associação. Se um endereço não estiver configurado, o endereço base é considerado o endereço do ponto de extremidade.  
  
 O `contract` atributo especifica o contrato que esse ponto de extremidade está expondo. O tipo de implementação de serviço deve implementar o tipo de contrato. Se uma implementação de serviço implementa um tipo de contrato único, em seguida, essa propriedade pode ser omitida.  
  
 O `binding` atributo seleciona uma associação predefinida ou personalizada a ser usado para esse ponto de extremidade específico. Um ponto de extremidade não seleciona explicitamente uma associação usa a seleção de associação padrão, que é `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Modificando uma associação predefinida  
 No exemplo a seguir, uma associação predefinida é modificada. Ele pode ser usado para configurar qualquer ponto de extremidade no serviço. A associação é modificada, definindo o <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> valor como 1 segundo. Observe que a propriedade retorna um <xref:System.TimeSpan> objeto.  
  
 Alterado de associação for encontrado na seção de associações. Isso alterado associação agora pode ser usado durante a criação de qualquer ponto de extremidade, definindo o `binding` de atributo no `endpoint` elemento.  
  
> [!NOTE]
>  Se você fornecer um nome específico à associação, o `bindingConfiguration` especificado no serviço de ponto de extremidade deve corresponder com ele.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Configurando um comportamento a ser aplicado a um serviço  
 No exemplo a seguir, um comportamento específico é configurado para o tipo de serviço. O `ServiceMetadataBehavior` elemento é usado para habilitar o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para consultar o serviço e gerar documentos de descrição linguagem WSDL (Web Services) dos metadados.  
  
> [!NOTE]
>  Se você fornecer um nome específico para o comportamento, o `behaviorConfiguration` especificado no serviço ou ponto de extremidade de seção deve corresponder a ele.  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 O habilita a configuração anterior um cliente chamar e obter os metadados de "HelloWorld" digitado o serviço.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Especificando um serviço com dois pontos de extremidade usando valores diferentes de associação  
 Neste último exemplo, dois pontos de extremidade são configurados para o `HelloWorld` tipo de serviço. Cada ponto de extremidade usa diferentes personalizado `bindingConfiguration` atributo do mesmo tipo de associação (cada modifica o `basicHttpBinding`).  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 Você pode obter o mesmo comportamento usando a configuração padrão, adicionando um `protocolMapping` seção e configurar as associações, conforme demonstrado no exemplo a seguir.  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a>Consulte também
- [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md)
- [Associações fornecidas pelo sistema](../../../docs/framework/wcf/system-provided-bindings.md)
- [Visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
