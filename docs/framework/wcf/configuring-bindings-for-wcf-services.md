---
title: Configurando associações para serviços do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174817"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Configurando associações para serviços do Windows Communication Foundation
Ao criar um aplicativo, muitas vezes você deseja adiar as decisões para o administrador após a implantação do aplicativo. Por exemplo, muitas vezes não há como saber com antecedência qual será um endereço de serviço, ou Uri (Uniform Resource Identifier), ou Identificador de Recursos Uniformes (URI). Em vez de codificar um endereço, é preferível permitir que um administrador o faça depois de criar um serviço. Essa flexibilidade é realizada através da configuração.  
  
> [!NOTE]
> Use a [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) com o `/config` switch para criar rapidamente arquivos de configuração.  
  
## <a name="major-sections"></a>Principais Seções  
 O esquema de configuração da Windows Communication Foundation (WCF) inclui as três principais seções (,`serviceModel` `bindings`e `services`):  
  
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
  
### <a name="servicemodel-elements"></a>Elementos do ServiceModel  
 Você pode usar a seção limitada pelo `system.ServiceModel` elemento para configurar um tipo de serviço com um ou mais pontos finais, bem como configurações para um serviço. Cada ponto final pode então ser configurado com um endereço, um contrato e um vinculativo. Para obter mais informações sobre pontos finais, consulte [Visão geral da criação de endpoint](endpoint-creation-overview.md). Se nenhum ponto final for especificado, o tempo de execução adicionará pontos finais padrão. Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](simplified-configuration.md) e [Configuração simplificada para serviços WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
 Uma vinculação especifica transportes (HTTP, TCP, tubos, fila de mensagens) e protocolos (Segurança, Confiabilidade, Fluxos de Transação) e consiste em elementos de vinculação, cada um dos quais especifica um aspecto de como um ponto final se comunica com o mundo.  
  
 Por exemplo, especificar o [ \<elemento básicoHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) indica usar HTTP como transporte para um ponto final. Isso é usado para conectar o ponto final no tempo de execução quando o serviço usando este ponto final é aberto.  
  
 Existem dois tipos de ligações: predefinida e personalizada. As ligações predefinidas contêm combinações úteis de elementos que são usados em cenários comuns. Para obter uma lista de tipos de vinculação predefinidos que o WCF fornece, consulte [Vinculações fornecidas pelo sistema](system-provided-bindings.md). Se nenhuma coleta de vinculação predefinida tiver a combinação correta de recursos que um aplicativo de serviço precisa, você pode construir vinculações personalizadas para atender aos requisitos do aplicativo. Para obter mais informações sobre vinculações personalizadas, consulte [ \<>de vinculação personalizada ](../configure-apps/file-schema/wcf/custombinding.md).  
  
 Os quatro exemplos a seguir ilustram as configurações de vinculação mais comuns usadas para configurar um serviço WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Especificando um ponto final para usar um tipo de vinculação  
 O primeiro exemplo ilustra como especificar um ponto final configurado com um endereço, um contrato e uma vinculação.  
  
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
  
 Neste exemplo, `name` o atributo indica para qual tipo de serviço a configuração é. Quando você cria um serviço `HelloWorld` em seu código com o contrato, ele é inicializado com todos os pontos finais definidos na configuração do exemplo. Se o conjunto implementar apenas um `name` contrato de serviço, o atributo pode ser omitido porque o serviço usa o único tipo disponível. O atributo leva uma string, que deve estar no formato`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 O `address` atributo especifica o URI que outros pontos finais usam para se comunicar com o serviço. O URI pode ser um caminho absoluto ou relativo. Se um endereço relativo for fornecido, espera-se que o host forneça um endereço base apropriado para o esquema de transporte usado na vinculação. Se um endereço não estiver configurado, o endereço base é assumido como o endereço para esse ponto final.  
  
 O `contract` atributo especifica o contrato que este ponto final está expondo. O tipo de implementação do serviço deve implementar o tipo de contrato. Se uma implementação de serviço implementar um único tipo de contrato, essa propriedade poderá ser omitida.  
  
 O `binding` atributo seleciona uma vinculação predefinida ou personalizada para usar para este ponto final específico. Um ponto final que não seleciona explicitamente uma vinculação `BasicHttpBinding`usa a seleção de vinculação padrão, que é .  
  
#### <a name="modifying-a-predefined-binding"></a>Modificando uma vinculação predefinida  
 No exemplo a seguir, uma vinculação predefinida é modificada. Em seguida, ele pode ser usado para configurar qualquer ponto final no serviço. A vinculação é <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> modificada definindo o valor para 1 segundo. Observe que a <xref:System.TimeSpan> propriedade retorna um objeto.  
  
 Essa vinculação alterada é encontrada na seção de vinculações. Esta vinculação alterada agora pode ser usada `binding` ao criar `endpoint` qualquer ponto final, definindo o atributo no elemento.  
  
> [!NOTE]
> Se você der um nome `bindingConfiguration` específico à vinculação, o ponto final de serviço especificado deve coincidir com ele.  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Configurando um comportamento para aplicar a um serviço  
 No exemplo a seguir, um comportamento específico é configurado para o tipo de serviço. O `ServiceMetadataBehavior` elemento é usado para permitir que a [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) consulte o serviço e gere documentos WSDL (Web Services Description Language, linguagem de descrição de serviços da Web) a partir dos metadados.  
  
> [!NOTE]
> Se você der um nome `behaviorConfiguration` específico ao comportamento, o especificado na seção serviço ou ponto final deve corresponder a ele.  
  
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
  
 A configuração anterior permite que um cliente ligue e obtenha os metadados do serviço digitado "HelloWorld".  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Especificando um serviço com dois pontos finais usando diferentes valores de vinculação  
 Neste último exemplo, dois pontos finais `HelloWorld` são configurados para o tipo de serviço. Cada ponto final usa `bindingConfiguration` um atributo personalizado diferente do `basicHttpBinding`mesmo tipo de vinculação (cada um modifica o ).  
  
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
  
 Você pode obter o mesmo comportamento usando `protocolMapping` a configuração padrão adicionando uma seção e configurando as vinculações como demonstrado no exemplo a seguir.  
  
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
  
## <a name="see-also"></a>Confira também

- [Configuração simplificada](simplified-configuration.md)
- [Associações fornecidas pelo sistema](system-provided-bindings.md)
- [Visão geral de criação de ponto de extremidade](endpoint-creation-overview.md)
- [Usando associações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md)
