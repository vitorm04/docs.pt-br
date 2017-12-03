---
title: "Como utilizar o Svcutil.exe para exportar metadados de código de serviço compilado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b6998333c3e49b24ad5bb96f36be65af94b6033
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Como utilizar o Svcutil.exe para exportar metadados de código de serviço compilado
Svcutil.exe pode exportar os metadados para os serviços, contratos e tipos de dados em assemblies compilados, da seguinte maneira:  
  
-   Para exportar metadados para todos os compilado contratos de serviço para um conjunto de assemblies usando Svcutil.exe, especifique os assemblies como parâmetros de entrada. Este é o comportamento padrão.  
  
-   Para exportar metadados para um serviço compilado usando Svcutil.exe, especifique o assembly de serviço ou assemblies como parâmetros de entrada. Você deve usar o `/serviceName` opção para indicar o nome da configuração do serviço que você deseja exportar. Svcutil.exe carrega automaticamente o arquivo de configuração para o assembly do executável especificado.  
  
-   Para exportar todos os tipos de contrato de dados em um conjunto de assemblies, use o `/dataContractOnly` opção.  
  
> [!NOTE]
>  Use o `/reference` opção para especificar os caminhos de arquivo para todos os assemblies dependentes.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Para exportar metadados para contratos de serviço compilado  
  
1.  Compile suas implementações de contrato de serviço em um ou mais libraries.1 de classe  
  
2.  Execute Svcutil.exe nos assemblies compilados.  
  
    > [!NOTE]
    >  Talvez seja necessário usar o `/reference` para especificar o caminho do arquivo para todos os assemblies dependentes.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Para exportar metadados para um serviço compilado  
  
1.  Compile sua implementação de serviço em um assembly.  
  
2.  Criar um arquivo de configuração para o executável do serviço e adicione uma configuração de serviço.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3.  Execute Svcutil.exe no serviço compilado executável usando o `/serviceName` para especificar o nome da configuração do serviço.  
  
    > [!NOTE]
    >  Talvez seja necessário usar o `/reference` para especificar o caminho do arquivo para todos os assemblies dependentes.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Para exportar metadados de contratos de dados compilados  
  
1.  Compile suas implementações de contrato de dados em uma ou mais bibliotecas de classe.  
  
2.  Executar Svcutil.exe nos assemblies compilados usando o `/dataContract` switch para especificar que apenas os metadados de contratos de dados devem ser gerados.  
  
    > [!NOTE]
    >  Talvez seja necessário usar o `/reference` para especificar o caminho do arquivo para todos os assemblies dependentes.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como gerar metadados para a implementação de serviço simples e a configuração.  
  
 Para exportar metadados para o contrato de serviço.  
  
```  
svcutil.exe Contracts.dll  
```  
  
 Para exportar metadados para os contratos de dados.  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Para exportar metadados para a implementação do serviço.  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 O `<path>` é o caminho para Contracts.dll.  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)]  
 [Exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
